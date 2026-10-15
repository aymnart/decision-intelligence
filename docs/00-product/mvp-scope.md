# MVP Scope

What the first usable version of the Decision Intelligence Engine includes and excludes. Detail lives in the linked specs; this page is the summary to check scope against.

---

## Goal

Build an Autonomous Council Builder that makes better decisions than a single AI agent ([MVP definition](../40-planning/mvp-plan/01-definition-and-user-flow.md#purpose)), delivered as a headless engine with a command-line interface ([ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)).

The question the MVP must answer: can an automatically generated council outperform a single AI? ([AI Council MVP](../30-specs/ai-council/03-mvp.md#mvp-must-prove))

---

## In scope

| Capability | What it covers | Spec |
| --- | --- | --- |
| Command-line interface | `apps/cli` submits decisions, shows progress and reports, handles approval, resumes runs, and runs evaluations | [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli), [System Design](../10-architecture/system-design.md#commands) |
| Decision submission | The operator submits a decision or problem from the CLI | [MVP definition](../40-planning/mvp-plan/01-definition-and-user-flow.md#mvp-definition) |
| Intent, domain, and impact analysis | Intent analysis, domain detection with multi-domain support, impact level | [Domain classifier](../30-specs/decision-engine/10-mvp-and-future.md#domain-classifier) |
| Expert registry | Domain-organized, built-in experts only, shared `CouncilExpert` contract | [Expert registry](../30-specs/decision-engine/10-mvp-and-future.md#expert-registry) |
| Council builder | Candidate retrieval, ranking, mandatory expert injection; the engine decides who participates | [Council builder](../30-specs/decision-engine/10-mvp-and-future.md#council-builder), [ADR-004](../90-records/decisions/01-foundations.md#adr-004-mvp-councils-are-built-autonomously-with-no-user-customization) |
| Permanent experts | Devil's Advocate, Risk Analyst, Critical Thinker on medium- and high-impact councils; Ethics Reviewer for sensitive domains | [Permanent experts](../30-specs/decision-engine/10-mvp-and-future.md#permanent-experts), [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| Debate engine | Independent opinions, critique, revision | [Debate engine](../30-specs/decision-engine/10-mvp-and-future.md#debate-engine) |
| Consensus engine | Weighted voting, minority reports, final consensus report | [Consensus engine](../30-specs/decision-engine/10-mvp-and-future.md#consensus-engine) |
| Human approval | High-impact decisions wait for the operator to confirm or reject them in the CLI before they are stored | [ADR-010](../90-records/decisions/02-mvp-design.md#adr-010-mvp-decision-lifecycle-ends-at-stored-with-human-approval-for-high-impact) |
| Decision storage | Save each decision and its reasoning for future reference | [Decision storage](../30-specs/decision-engine/10-mvp-and-future.md#decision-storage--memory) |
| Result display | Print the consensus report in the terminal | [MVP user flow](../40-planning/mvp-plan/01-definition-and-user-flow.md#mvp-user-flow) |
| Evaluation | The `eval` command compares council reports with a single-AI baseline for blind rating, then scores the ratings | [ADR-012](../90-records/decisions/02-mvp-design.md#adr-012-measurable-mvp-success-targets) |

Build order follows the [AI Council MVP build order](../30-specs/ai-council/03-mvp.md#mvp-build-order). Sprint breakdown is in the [MVP plan](../40-planning/mvp-plan/README.md).

---

## Out of scope

| Item | Reason |
| --- | --- |
| User-customized councils, custom or personal experts, Eve agents as council members, company private councils | The MVP must measure the engine's own assembly quality without user choices skewing the result ([ADR-004](../90-records/decisions/01-foundations.md#adr-004-mvp-councils-are-built-autonomously-with-no-user-customization)) |
| GitHub automation, code generation, repository creation, project planning, design generation, autonomous coding agents | All are expansions that depend on the council. The biggest risk is whether the council beats a single AI, so that is validated first ([Reason](../40-planning/mvp-plan/07-success-and-scope.md#reason)) |
| Complex memory systems | The MVP only needs to save decisions and reasoning ([What NOT to build](../40-planning/mvp-plan/07-success-and-scope.md#what-not-to-build)) |
| Multi-agent workflows beyond council debate | Same as above: council debate is the only workflow being validated |
| Learned expert weights, outcome-based scoring, organizational knowledge graph | Planned for V2 once there is decision history to learn from ([Future improvements](../30-specs/decision-engine/10-mvp-and-future.md#future-improvements)) |
| Web app, HTTP API, accounts and sign-in, Inngest background runs, report rating | The core question needs none of them. They follow in [Phase 2](roadmap/03-phase-2-advanced-decision-engine.md#web-app-and-api) and reuse the same engine ([ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)) |
| Temporal, OpenSearch, pgvector, Kubernetes, and other deferred infrastructure | Not needed until a concrete need appears ([ADR-008](../90-records/decisions/01-foundations.md#adr-008-defer-infrastructure-until-it-is-needed)) |

Post-MVP sequencing is in the [roadmap](roadmap/README.md).

---

## Success metrics

From [MVP success metrics](../40-planning/mvp-plan/07-success-and-scope.md#mvp-success-metrics):

| Metric | Signal | Target |
| --- | --- | --- |
| Quality | Blind raters prefer council answers over single-AI answers | Council preferred in at least 60% of blind comparisons |
| Technical | The system runs multiple experts, debates, reaches consensus, and stores decisions | At least 95% reach consensus unaided, within NFR-007 times |

Measurement method, sample size, and baseline definition are in [ADR-012](../90-records/decisions/02-mvp-design.md#adr-012-measurable-mvp-success-targets). Trust and Repeat usage were removed from the MVP by [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) and are measured once the web app ships.

---

## Exit criteria

The MVP is complete, and post-MVP phases can start, when all of the following hold:

1. The [first development goal](../40-planning/mvp-plan/07-success-and-scope.md#first-development-goal) runs end to end: question, intent and domain and impact, autonomous council assembly, debate, consensus, decision report, and stored memory.
2. Every in-scope capability above works for built-in experts without user customization.
3. Both success metrics meet their targets: the council beats a single AI, and runs complete reliably ([After MVP validation](../40-planning/mvp-plan/07-success-and-scope.md#after-mvp-validation)).
