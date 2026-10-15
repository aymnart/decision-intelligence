# Architecture Decision Records

One record per decision, numbered in the order it was made. Records are never deleted. A replaced decision is marked `Superseded by ADR-00X`.

New major technology choices follow the [technology decision process](../../10-architecture/tech-stack/10-governance.md#technology-decision-process): proposal, AI Council review, ADR here, tech-stack update, implementation.

Each record has Status, Date, Source, then **Context**, **Options**, **Decision**, and **Consequences**. Add new records to the end of the last part. Start a new part when it passes ~250 lines.

---

## Contents

| File | Records | Lines |
| --- | --- | --- |
| [01-foundations.md](01-foundations.md) | ADR-001 to ADR-008: decisions already made in the specs (product, council, stack, governance) | 129 |
| [02-mvp-design.md](02-mvp-design.md) | ADR-009 onward: MVP design decisions (council size, lifecycle, targets, schema, run orchestration, layout, security, branching, CLI-first MVP) | 197 |

---

## Index

| ADR | Title | Status |
| --- | --- | --- |
| [ADR-001](01-foundations.md#adr-001-the-decision-intelligence-engine-is-the-product) | The Decision Intelligence Engine is the product | Accepted |
| [ADR-002](01-foundations.md#adr-002-councils-are-assembled-dynamically-per-request) | Councils are assembled dynamically per request | Accepted |
| [ADR-003](01-foundations.md#adr-003-permanent-quality-control-experts-sit-on-every-council) | Permanent quality-control experts sit on every council | Superseded by ADR-009 |
| [ADR-004](01-foundations.md#adr-004-mvp-councils-are-built-autonomously-with-no-user-customization) | MVP councils are built autonomously, with no user customization | Accepted |
| [ADR-005](01-foundations.md#adr-005-typescript-monorepo-with-pnpm-and-turborepo) | TypeScript monorepo with pnpm and Turborepo | Accepted |
| [ADR-006](01-foundations.md#adr-006-the-engine-is-independent-of-frameworks-providers-and-eve) | The engine is independent of frameworks, providers, and Eve | Accepted |
| [ADR-007](01-foundations.md#adr-007-stack-governance-for-versions-and-dependencies) | Stack governance for versions and dependencies | Accepted |
| [ADR-008](01-foundations.md#adr-008-defer-infrastructure-until-it-is-needed) | Defer infrastructure until it is needed | Accepted |
| [ADR-009](02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) | Council composition scales with impact level | Accepted |
| [ADR-010](02-mvp-design.md#adr-010-mvp-decision-lifecycle-ends-at-stored-with-human-approval-for-high-impact) | MVP decision lifecycle ends at STORED, with human approval for high impact | Accepted |
| [ADR-011](02-mvp-design.md#adr-011-mvp-response-time-targets-per-impact-level) | MVP response-time targets per impact level | Accepted |
| [ADR-012](02-mvp-design.md#adr-012-measurable-mvp-success-targets) | Measurable MVP success targets | Accepted, amended by ADR-018 (Trust and Repeat usage removed) |
| [ADR-013](02-mvp-design.md#adr-013-mvp-database-schema) | MVP database schema | Accepted, amended by ADR-018 (user, ownership, and rating columns deferred) |
| [ADR-014](02-mvp-design.md#adr-014-mvp-decision-run-orchestration) | MVP decision run orchestration | Accepted, amended by ADR-018 (Inngest, polling, per-user limits, and approval expiry deferred to the web app) |
| [ADR-015](02-mvp-design.md#adr-015-repository-layout-and-dependency-direction) | Repository layout and dependency direction | Accepted, amended by ADR-018 (`apps/cli` is the MVP composition root) |
| [ADR-016](02-mvp-design.md#adr-016-mvp-security-baseline) | MVP security baseline | Accepted, amended by ADR-018 (session and ownership rules apply from the web app) |
| [ADR-017](02-mvp-design.md#adr-017-short-lived-branches-off-main) | Short-lived branches off main | Accepted |
| [ADR-018](02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) | The MVP is a headless engine with a CLI | Accepted |
