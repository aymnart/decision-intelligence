> Part of [Eve Implementation Specification](README.md).

# MVP Eve Implementation

Per [ADR-008](../../90-records/decisions/01-foundations.md#adr-008-defer-infrastructure-until-it-is-needed), [ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction), and [ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli), the MVP runs directly as a headless engine via `apps/cli` without the Eve runtime, external tools ([ADR-016](../../90-records/decisions/02-mvp-design.md#adr-016-mvp-security-baseline)), or workflow and artifact tables ([Database Design](../../10-architecture/database-design.md#not-in-the-mvp-schema)).

The sections below specify the baseline design for when Eve integration arrives in [Phase 6](../../00-product/roadmap/07-phase-5-6-github-and-eve.md).

First Eve implementation requires durable execution of **built-in** experts assembled by the engine.

Do not implement user-customized Eve council members yet.

## Agents (seed workers)

```
CTO

Backend Architect

Database Engineer

Security Engineer

Devil's Advocate

Risk Analyst

Critical Thinker
```

These are workers for roles selected by Council Assembly — not a fixed always-on roster.

---

## Tools

```
Filesystem

GitHub

Terminal
```

---

## Workflows

```
Architecture Decision

Project Planning

Issue Generation
```

---

## Storage

```
PostgreSQL

Decision table

Workflow table

Artifact table
```

---

# Future Eve Expansion

Stages within Eve. Product-wide phase numbers live in the [roadmap](../../00-product/roadmap/README.md).

Stage 1:

More experts

More tools

More workflows

Stage 2:

Autonomous coding

Testing agents

Review agents

Stage 3:

Complete software company simulation

---

# Golden Rule

Eve executes.

The Council decides.

The Decision Engine remembers.

The Human approves.
