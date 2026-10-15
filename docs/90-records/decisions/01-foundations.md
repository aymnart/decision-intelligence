> Part of [Architecture Decision Records](README.md).

# Foundations

## ADR-001: The Decision Intelligence Engine is the product

- Status: Accepted
- Date: 2026-10-15
- Source: [Principles](../../00-product/vision/02-principles.md#fundamental-principle), [Tech Stack](../../10-architecture/tech-stack/README.md#architecture-direction)

**Context** — Planning, execution, GitHub automation, and agents all need architectural judgment. Embedding that judgment in each workflow would duplicate it and let it drift.

**Options** — Put decision logic inside each workflow; or centralize it in one engine that every feature calls.

**Decision** — The Decision Intelligence Engine is the product, and dynamic council assembly is its core mechanism. Every feature, agent, or user request that needs a decision calls the engine. Workflows never embed architectural intelligence directly.

**Consequences** — Decision quality improves in one place and every consumer benefits. The engine becomes a hard dependency for all later phases, so its interface must stay stable.

---

## ADR-002: Councils are assembled dynamically per request

- Status: Accepted
- Date: 2026-10-15
- Source: [AI Council purpose](../../30-specs/ai-council/01-purpose-and-vision.md#purpose), [Tech Stack](../../10-architecture/tech-stack/README.md#architecture-direction)

**Context** — A single AI agent has blind spots. A fixed roster of personas only covers the blind spots someone predicted in advance.

**Options** — Ship a static set of experts; or analyze each objective and assemble a temporary expert organization for it.

**Decision** — For each request the engine analyzes intent, detects domain and impact, then assembles Required Experts plus Permanent Experts. That council debates, reaches consensus, and stores the decision in memory.

**Consequences** — Councils fit the problem, and each expert brings a distinct optimization target. This requires a reliable intent and domain classifier and an expert registry before anything else works.

---

## ADR-003: Permanent quality-control experts sit on every council

- Status: Superseded by ADR-009
- Date: 2026-10-15
- Source: [Permanent Council Members](../../30-specs/ai-council/04-expert-categories-and-permanent-members.md#permanent-council-members), [Core Principle](../../30-specs/ai-council/01-purpose-and-vision.md#core-principle)

**Context** — Domain experts optimize for their own field. Nobody is assigned to attack the decision itself or to check the quality of its reasoning.

**Options** — Rely on domain experts to critique each other; or always add dedicated quality-control agents.

**Decision** — Devil's Advocate, Risk Analyst, and Critical Thinker are present on every council. Ethics/Safety Reviewer joins for sensitive domains.

**Consequences** — Every decision is challenged on assumptions, risks, and logic. Each request costs at least three extra expert calls.

---

## ADR-004: MVP councils are built autonomously, with no user customization

- Status: Accepted
- Date: 2026-10-15
- Source: [AI Council MVP](../../30-specs/ai-council/03-mvp.md), [Principles](../../00-product/vision/02-principles.md#fundamental-principle)

**Context** — The MVP has to answer one question: can an automatically generated council outperform a single AI?

**Options** — Let users pick or edit council members; or let the engine decide alone.

**Decision** — In the MVP the engine decides council composition. Custom experts, Eve agents as council members, company knowledge, private councils, and user-customized councils are deferred.

**Consequences** — The MVP measures the engine's assembly quality without user choices skewing the result. Users with strong opinions on the experts they want have to wait for [Phase 2.5](../../00-product/roadmap/04-phase-2.5-custom-experts.md).

---

## ADR-005: TypeScript monorepo with pnpm and Turborepo

- Status: Accepted
- Date: 2026-10-15
- Source: [Project Structure](../../10-architecture/project-structure/01-purpose-and-repository.md#architecture-style), [Foundation](../../10-architecture/tech-stack/02-foundation.md)

**Context** — The system has many layers (engine core, council, consensus, memory, execution, integrations, UI) that must stay separated yet ship together. It relies heavily on structured AI outputs.

**Options** — Monorepo: Turborepo or Nx. Package manager: pnpm, npm, or Yarn. Runtime: Node.js or Bun.

**Decision** — Single monorepo with `apps/` and `packages/`, TypeScript everywhere in strict mode, pnpm workspaces, Turborepo, TypeScript project references, and Node.js 24 LTS. Packages follow clean architecture and domain-driven organization, and no package takes on another layer's responsibilities.

**Consequences** — Strong type safety for AI output contracts, incremental builds, and clear package boundaries. Nx is rejected as too complex for the MVP. Bun is rejected for now because it is still evolving.

---

## ADR-006: The engine is independent of frameworks, providers, and Eve

- Status: Accepted
- Date: 2026-10-15
- Source: [Golden Rules](../../10-architecture/tech-stack/10-governance.md#golden-rules)

**Context** — AI providers, agent runtimes, and frameworks change quickly. If the engine is coupled to any of them, it inherits their churn and lock-in.

**Options** — Build directly on a chosen framework, provider, or runtime; or keep the engine core isolated behind adapters.

**Decision** — The Decision Engine stays framework-independent. AI providers must be interchangeable. Eve is an implementation detail, not the architecture.

**Consequences** — Providers and runtimes can be swapped without rewriting the core. Adapter layers add some upfront work.

---

## ADR-007: Stack governance for versions and dependencies

- Status: Accepted
- Date: 2026-10-15
- Source: [Version Policy and Stack Governance](../../10-architecture/tech-stack/10-governance.md#version-policy)

**Context** — An unmanaged dependency tree and ad-hoc upgrades erode stability and portability.

**Options** — Add dependencies and upgrade freely; or gate both behind explicit criteria.

**Decision** — Use the latest stable versions and no beta releases in production. A major upgrade requires testing, an ADR, and a changelog entry. A new dependency must justify the problem it solves, show that no existing dependency covers it, be maintained, improve developer experience, and avoid vendor lock-in. If the answer is unclear, the dependency is not added.

**Consequences** — The stack stays small and portable. Adding a library takes deliberate justification.

---

## ADR-008: Defer infrastructure until it is needed

- Status: Accepted
- Date: 2026-10-15
- Source: [Future Technologies](../../10-architecture/tech-stack/10-governance.md#future-technologies)

**Context** — Durable workflow engines, search clusters, vector stores, and orchestration platforms add operational cost before the MVP has proven its value.

**Options** — Build for scale from day one; or add infrastructure only when a concrete need appears.

**Decision** — Temporal, OpenSearch, pgvector, Kubernetes, Bun runtime, Rust services, MCP integrations, and multi-region deployment are excluded from the MVP.

**Consequences** — The MVP stays simple to build and operate. Adopting any of these later requires a new ADR, and the code should avoid choices that make them hard to add.
