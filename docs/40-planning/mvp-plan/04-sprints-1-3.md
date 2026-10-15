> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# MVP Implementation Order

---

# Sprint 1

## Foundation

Tasks:

Create repository

Setup CLI app (`apps/cli`), per [ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)

Setup TypeScript

Setup database

Setup ORM

Create base architecture

Output:

Working application.

---

# Sprint 2

## AI Provider System

Tasks:

Create AI interface.

Implement provider.

Add:

- generation
- structured outputs

Output:

Application can communicate with AI.

---

# Sprint 3

## Expert System

Tasks:

Create expert registry as a domain knowledge base.

Structure:

```
experts/

engineering/

business/

legal/

general/
```

Create seed built-in experts, including permanent quality-control agents:

Devil's Advocate

Risk Analyst

Critical Thinker

Ethics Reviewer

Plus domain seeds (CTO, Backend Architect, etc.).

Implement shared `CouncilExpert` contract:

- id
- name
- domain
- type: built-in | custom | eve-agent (custom/eve post-MVP)
- instructions
- capabilities
- weight
- alwaysIncluded?
- analyze(context)

Implement:

Expert prompts

Expert execution

Output:

Multiple experts can answer one question through one interface.
