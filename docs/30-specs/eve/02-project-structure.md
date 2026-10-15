> Part of [Eve Implementation Specification](README.md).

# Project Structure

The canonical monorepo layout and dependency direction are defined in [Project Structure](../../10-architecture/project-structure/01-purpose-and-repository.md#repository-structure) and [ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction). The sketch below shows where Eve components integrate when Phase 6 arrives:

```
decision-intelligence/

├── apps/

│   └── web/

│

├── packages/

│

│   ├── council/

│   │
│   ├── decision-engine/

│   │
│   ├── consensus/

│   │
│   ├── memory/

│   │
│   ├── planner/

│   │
│   ├── executor/

│   │
│   ├── github/

│   │
│   ├── eve/

│   │
│   ├── prompts/

│   │
│   └── shared/

│

├── experts/

│   ├── engineering/

│   ├── business/

│   ├── legal/

│   └── general/

│       ├── devil-advocate/

│       ├── critical-thinker/

│       ├── risk-analyst/

│       └── ethics-reviewer/

│

├── agents/   # optional Eve runtime wrappers

│

├── workflows/

│
├── docs/

│
├── tests/

│
└── package.json
```
