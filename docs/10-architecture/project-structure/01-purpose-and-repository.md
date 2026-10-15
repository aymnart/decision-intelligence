> Part of [Project Structure Specification](README.md).

# Purpose

This document defines the codebase architecture for the Decision Intelligence Engine.

The project must be modular, scalable, and maintainable.

The architecture separates:

- Decision Intelligence Engine core
- Council assembly (AI Council)
- AI orchestration
- Consensus / debate
- Memory
- Execution
- External integrations
- User interface

No package should contain responsibilities belonging to another layer.

---

# Architecture Style

Use:

- Monorepo architecture
- TypeScript everywhere
- Package-based separation
- Clean architecture principles
- Domain-driven organization

Recommended tooling:

- pnpm workspaces
- Turborepo
- TypeScript project references

---

# Repository Structure

Canonical tree ([ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction)). The MVP builds `apps/cli` and the engine packages first ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)).

```
decision-intelligence/

│
├── apps/
│
│   ├── cli/          (MVP)
│   │
│   ├── web/          (roadmap Phase 2)
│   │
│   └── api/          (roadmap Phase 2)
│
│
├── packages/
│
│   ├── core/
│   │
│   ├── decision-engine/
│   │
│   ├── council/
│   │
│   ├── consensus/
│   │
│   ├── memory/
│   │
│   ├── planner/
│   │
│   ├── executor/
│   │
│   ├── workflows/
│   │
│   ├── github/
│   │
│   ├── eve/
│   │
│   ├── prompts/
│   │
│   ├── database/
│   │
│   ├── ai/
│   │
│   ├── observability/
│   │
│   ├── security/
│   │
│   └── shared/
│
│
├── agents/
│
│   └── (runtime wrappers / Eve adapters — optional)
│
│
├── experts/
│
│   ├── engineering/
│   │
│   │   ├── backend-architect/
│   │   ├── frontend-architect/
│   │   └── database-engineer/
│   │
│   ├── business/
│   │
│   │   ├── cfo/
│   │   ├── startup-advisor/
│   │   └── marketer/
│   │
│   ├── legal/
│   │
│   │   ├── lawyer/
│   │   └── compliance-specialist/
│   │
│   └── general/
│
│       ├── devil-advocate/
│       ├── critical-thinker/
│       ├── risk-analyst/
│       └── ethics-reviewer/
│
│
├── docs/
│
├── scripts/
│
├── tests/
│
├── .env.example
│
├── package.json
│
├── pnpm-workspace.yaml
│
└── turbo.json
```
