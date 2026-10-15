> Part of [Architecture Decision Records](README.md).

# MVP Design

## ADR-009: Council composition scales with impact level

- Status: Accepted
- Date: 2026-10-15
- Source: User decision; [Impact Classification](../../30-specs/decision-engine/03-impact-classification.md), [Decision Impact Levels](../../30-specs/ai-council/07-council-assembly.md#decision-impact-levels), [Permanent Council Members](../../30-specs/ai-council/04-expert-categories-and-permanent-members.md#permanent-council-members)

**Context** — The permanent-members spec says Devil's Advocate, Risk Analyst, and Critical Thinker are always present (ADR-003). The impact specs say a low-impact decision uses one expert with no debate. They also disagree on whether the 3–5 experts of a medium-impact council include the permanent experts.

**Options** — Low impact: always add all three permanent experts; never add any; or one domain expert with an optional single permanent check. Medium impact: 3–5 experts in total; or 3–5 domain experts plus the permanent experts.

**Decision** — Low impact: one domain expert, no debate, and the engine may add one permanent check. Medium impact: 3–5 domain experts plus Devil's Advocate, Risk Analyst, and Critical Thinker, with one debate round. High impact: the full relevant council plus all three permanent experts, with multiple debate rounds. Ethics/Safety Reviewer joins at any level for sensitive or regulated domains.

**Consequences** — Trivial decisions stay cheap and fast, while every medium- or high-impact decision is challenged by all quality-control agents. A low-impact decision that the classifier gets wrong gets less scrutiny, so classification accuracy matters.

---

## ADR-010: MVP decision lifecycle ends at STORED, with human approval for high impact

- Status: Accepted
- Date: 2026-10-15
- Source: User decision; [Decision Lifecycle](../../30-specs/decision-engine/02-lifecycle-object-categories.md#decision-lifecycle), [High Impact](../../30-specs/decision-engine/03-impact-classification.md#high-impact), [MVP Scope](../../00-product/mvp-scope.md)

**Context** — The full lifecycle runs from CREATED to EVALUATED, including EXECUTED. Execution is out of MVP scope, and the impact spec recommends human approval for high-impact decisions.

**Options** — Run the full lifecycle; stop at STORED and skip approval; or stop at STORED with an approval step for high-impact decisions.

**Decision** — MVP decisions go from CREATED to STORED. High-impact decisions wait in APPROVED until a human confirms them. Low- and medium-impact decisions pass through without human approval. EXECUTED and EVALUATED are not used in the MVP.

**Consequences** — Humans stay in control of the decisions with the largest blast radius. The MVP needs an approval action in the interface, and high-impact decisions can sit unconfirmed.

---

## ADR-011: MVP response-time targets per impact level

- Status: Accepted
- Date: 2026-10-15
- Source: User decision; [Performance](../../50-quality/07-performance-and-observability.md), [LLM Cost Optimization](../../00-product/vision/07-operations.md#llm-cost-optimization)

**Context** — The specs require latency to be tracked and reasoning depth to scale with impact, but give no numeric targets. Without targets, response time can't be tested.

**Options** — Low / medium / high under 10 s / 1 min / 3 min; 15 s / 2 min / 5 min; 30 s / 5 min / 15 min; or no targets until the MVP has been measured.

**Decision** — At the 95th percentile, submission to consensus report takes under 15 seconds for low impact, 2 minutes for medium impact, and 5 minutes for high impact. Time waiting for human approval is excluded.

**Consequences** — Debate rounds and expert calls must fit these budgets, which favors running independent expert analysis in parallel. Medium- and high-impact decisions take long enough that the interface needs to show progress rather than block silently.

---

## ADR-012: Measurable MVP success targets

- Status: Accepted, amended by ADR-018 (Trust and Repeat usage removed)
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [MVP Success Metrics](../../40-planning/mvp-plan/07-success-and-scope.md#mvp-success-metrics), replaces [A-001](../assumptions.md)

**Context** — The MVP success metrics (Quality, Trust, Repeat usage, Technical) were qualitative. The MVP must prove that a generated council outperforms a single AI, which needs a fair comparison and a pass mark set before results come in.

**Options** — Judge qualitatively; rely on live user feedback only; or combine a fixed, blind benchmark against a single-AI baseline with in-product signals.

**Decision** — Targets are fixed before the evaluation runs:

- **Quality:** on an evaluation set of at least 30 questions covering all three impact levels and at least five domains, blind raters prefer the council report over a single-AI answer in at least 60% of non-tie comparisons. The baseline uses the same model as the council, one prompt, and the same question. Pair order is randomized and the source is hidden.
- **Trust:** at least 80% of rated reports get "yes" to "Do you understand why this decision was made?"
- **Repeat usage:** at least 40% of users who complete a first decision submit another within 30 days.
- **Technical:** at least 95% of submitted decisions reach `CONSENSUS` without manual intervention, and [NFR-007](../../00-product/requirements.md#non-functional-requirements) response times are met.

Trust and repeat usage are measured over at least 20 users.

**Consequences** — The MVP needs an evaluation script, a fixed question set, and a one-question rating on the report. Targets are a starting point; changing them after results are known requires a new ADR, so the bar cannot quietly move.

---

## ADR-013: MVP database schema

- Status: Accepted, amended by ADR-018 (user, ownership, and rating columns deferred)
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [Database Models](../../10-architecture/project-structure/07-database-models.md), [MVP schema](../../40-planning/mvp-plan/03-database-schema.md), [Expert Structure](../../10-architecture/project-structure/06-expert-structure.md)

**Context** — Two schema sketches disagree. One ties decisions to projects and stores a debate as one row with a list of messages. The other ties decisions to users, stores one row per debate message, and keeps expert prompts in an `Expert` table, while the project structure keeps prompts in files under `experts/`. Neither covers council membership, approval, the report rating, or failed runs, which the requirements need.

**Options** — Adopt either sketch as is; or merge them, keeping only what the MVP requirements need.

**Decision** — The schema in [Database Design](../../10-architecture/database-design.md) is the single source of truth:

- Decisions belong to a user. `project` and `decision.project_id` arrive with Phase 3.
- Expert definitions stay in `experts/`. The database keeps a synced `expert` catalog with a content-hash `version`, and each council member records the version used.
- Debate is stored as one row per message, with explicit `council_member` and `vote` tables.
- The final result and confidence live in `consensus`, not on `decision`.
- `decision_status` adds a terminal `FAILED` value, so failed runs can be counted.
- Rows other than `decision` are insert-only, and foreign keys never cascade deletes.

**Consequences** — Every stored decision can be replayed: who sat on the council, which expert version, what each said, and how they voted. It adds tables that a single JSON column would avoid, in exchange for queryable history. Expert prompts change only through code review, never in the database.

---

## ADR-014: MVP decision run orchestration

- Status: Accepted, amended by ADR-018 (Inngest, polling, per-user limits, and approval expiry deferred to the web app)
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [System Architecture](../../10-architecture/system/README.md), [Durable Workflows](../../30-specs/eve/05-approval-and-workflows.md#durable-workflows), [Data and Infrastructure](../../10-architecture/tech-stack/05-data-and-infrastructure.md)

**Context** — A high-impact run can take up to 5 minutes ([ADR-011](#adr-011-mvp-response-time-targets-per-impact-level)), longer than one serverless invocation should stay open. The specs require retries, fallback models, and resumable workflows, but do not say how partial expert failure, progress display, or rejected approvals behave.

**Options** — Run the council inside the API request; run it on a separate long-lived worker; or run it as a durable Inngest function, which the stack already includes for long-running jobs.

**Decision** — Full design in [System Design](../../10-architecture/system-design.md):

- The API stores the decision and sends `decision/created`. One Inngest function runs the lifecycle as durable steps, with the decision id as the idempotency key.
- The web app polls decision status every 2 seconds while a run is in progress.
- MVP context is the submitted text plus optional user-typed context. Retrieval of past decisions starts in Phase 3.
- Failed model calls are retried up to 3 times, then once on a fallback model. A medium- or high-impact run continues only if all three permanent experts and at least 3 domain experts produced opinions; otherwise it ends `FAILED`.
- A human can reject a high-impact decision, and an approval left unanswered for 30 days expires. Both end in a new terminal status, `REJECTED`.
- MVP limits: at most 8 domain experts per council, 2 concurrent runs per user, and 20 submissions per user per day.

**Consequences** — Runs survive crashes and redeploys without duplicate work, and the API stays fast. Polling is simpler than streaming but adds read load; streaming can replace it later without changing the run. Weighted agreement is computed in code, so consensus numbers are reproducible.

---

## ADR-015: Repository layout and dependency direction

- Status: Accepted, amended by ADR-018 (`apps/cli` is the MVP composition root)
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [Repository Structure](../../10-architecture/project-structure/01-purpose-and-repository.md#repository-structure), [Dependency Rules](../../10-architecture/project-structure/08-dependencies-testing-order.md#dependency-rules), [Repository and Dependencies](../../10-architecture/tech-stack/09-repository-and-dependencies.md), [System Overview](../../10-architecture/system/01-overview.md#high-level-architecture)

**Context** — Three docs give three repository trees: one has `apps/api`, one has `packages/api` plus `orchestration` and `queue`, one has a `types` package. The tech-stack dependency diagram has domain depending on infrastructure, which contradicts its own dependency-injection example and Clean Architecture. `packages/prompts` and `experts/*/SYSTEM.md` both claim expert prompts.

**Options** — Keep each doc's version; or pick one tree, one dependency direction, and one home for each kind of prompt.

**Decision** —

- The tree in [Project Structure](../../10-architecture/project-structure/01-purpose-and-repository.md#repository-structure) is canonical: `apps/web`, `apps/api`, `packages/*`, `experts/*`.
- Dependencies point inward. `core` holds domain types and ports (interfaces such as `AIProvider` and `DecisionRepository`) and depends on nothing but `shared`. `decision-engine`, `council`, `consensus`, and `memory` depend on `core` and on each other only in the direction `decision-engine` → `council`, `consensus`, `memory`. `ai`, `database`, and `observability` implement `core` ports and depend only on `core` and `shared`.
- `apps/api` is the composition root: it wires adapters into the engine and hosts the Inngest function. `apps/web` talks only to `apps/api`.
- Engine packages never import `ai`, `database`, or `observability` implementations, nor Hono, Next.js, Inngest, or Eve.
- Each expert's own prompt lives in `experts/<domain>/<expert>/SYSTEM.md`. `packages/prompts` holds pipeline prompts (classification, debate, consensus) and the loader for expert files.
- The MVP creates only `core`, `decision-engine`, `council`, `consensus`, `memory`, `ai`, `database`, `prompts`, `observability`, and `shared`. `planner`, `executor`, `workflows`, `github`, `eve`, `security`, and `agents/` wait for their roadmap phase.

**Consequences** — The engine can be unit-tested with fake adapters, and providers or the database can be swapped without touching it ([NFR-003](../../00-product/requirements.md#non-functional-requirements), [NFR-004](../../00-product/requirements.md#non-functional-requirements)). Wiring code in `apps/api` grows as adapters are added. Dependency direction should be enforced by a lint rule, not by review alone.

---

## ADR-016: MVP security baseline

- Status: Accepted, amended by ADR-018 (session and ownership rules apply from the web app)
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [Security Guidelines](../../50-quality/06-security.md), [Operations](../../00-product/vision/07-operations.md#security)

**Context** — The security docs set principles (least privilege, minimal data, approval for dangerous actions) but not who may approve a decision, what tools experts get, or what user data is kept.

**Options** — Allow any authenticated user to approve; or only the owner. Give experts the tools listed in their `TOOLS.md`; or none until execution exists.

**Decision** — Every decision read, write, and approval is scoped to its owner, and other users' decisions return not-found. Experts get no tools in the MVP, so injected text in a question cannot trigger an action. The only personal data stored is the account email. User text and model output are untrusted: passed as delimited content, validated with Zod, and rendered escaped. Logs carry ids and metrics, not question text or prompt bodies.

**Consequences** — Prompt injection can at worst skew one decision's reasoning, not take actions or reach other users' data. Teams cannot share or co-approve decisions until a later ADR adds roles. Debugging a run relies on stored rows rather than log contents. Rules are in [`.cursor/rules/security.mdc`](../../../.cursor/rules/security.mdc).

---

## ADR-017: Short-lived branches off main

- Status: Accepted
- Date: 2026-10-15
- Source: Delegated by the user to the agent; [Branch Strategy](../../30-specs/github-automation/03-branches-commits-prs.md#branch-strategy)

**Context** — The GitHub automation spec defines `main`, `develop`, `feature/<issue>-<name>`, and `fix/<issue>-<name>` for repositories the product generates. This repository has only `main`, no release process, and also gets docs, refactor, and chore changes.

**Options** — Adopt `develop` now; or branch from `main` and merge back through pull requests until a release process needs more.

**Decision** — This repository branches from `main` as `<type>/<issue-number>-<short-name>`, where `<type>` matches the commit type (`feature` for `feat`) and the issue number is optional. Pull requests merge into `main`. The spec's branch model still applies to repositories the product generates.

**Consequences** — One long-lived branch keeps merges simple while the team is small. `main` must stay releasable, so CI has to gate merges. Adding `develop` later needs a new ADR.

---

## ADR-018: The MVP is a headless engine with a CLI

- Status: Accepted
- Date: 2026-10-15
- Source: User decision; [MVP Must Prove](../../30-specs/ai-council/03-mvp.md#mvp-must-prove), [Golden Rule](../../00-product/roadmap/09-vision-mvp-and-success.md#golden-rule), [ADR-008](01-foundations.md#adr-008-defer-infrastructure-until-it-is-needed)

**Context** — The riskiest assumption is whether a generated council beats a single AI. Answering that needs a question set, the council, a single-AI baseline, and blind rating. It does not need a UI, accounts, or background infrastructure. The MVP plan started with a Next.js app, which would build all of those before the core is proven.

**Options** — Web app first; a published SDK or HTTP API first; or the engine packages with a command-line interface, adding the web app after validation.

**Decision** —

- The MVP is the engine packages plus `apps/cli`, the composition root. `apps/web`, `apps/api`, accounts and sign-in, and Inngest move after the MVP, to [Phase 2](../../00-product/roadmap/03-phase-2-advanced-decision-engine.md#web-app-and-api).
- MVP success is Quality and Technical only. Trust and Repeat usage, the report rating, and the 20-user cohort are removed ([ADR-012](#adr-012-measurable-mvp-success-targets) amended).
- Storage stays PostgreSQL with Drizzle, run locally or on a Neon branch. The `user` table, ownership, and rating columns wait for the web app ([ADR-013](#adr-013-mvp-database-schema) amended).
- The CLI runs the engine in-process and stores each stage before the next, so `resume` can continue an interrupted run. Retries, fallback model, partial-failure rules, and council limits from [ADR-014](#adr-014-mvp-decision-run-orchestration) still apply; Inngest, polling, per-user limits, and approval expiry wait for the web app.
- High-impact approval is a terminal prompt, plus `approve` and `reject` commands for decisions left pending.
- The CLI uses Node's built-in `util.parseArgs` and `readline`, adding no dependencies ([ADR-007](01-foundations.md#adr-007-stack-governance-for-versions-and-dependencies)).
- Session and ownership rules from [ADR-016](#adr-016-mvp-security-baseline) apply once the web app exists. The CLI runs as one local operator.

**Consequences** — The core question gets answered with the least infrastructure, and the `eval` command is the FR-023 harness. Because the engine depends only on `core` ports ([ADR-015](#adr-015-repository-layout-and-dependency-direction)), the web app reuses it unchanged. The MVP no longer measures whether non-developers trust or return to the product; that is measured when the web app ships.
