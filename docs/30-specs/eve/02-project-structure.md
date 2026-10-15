> Part of [Eve Implementation Specification](README.md).

# Project Structure

Recommended structure:

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
