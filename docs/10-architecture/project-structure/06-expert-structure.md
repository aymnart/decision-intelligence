> Part of [Project Structure Specification](README.md).

# Expert Structure

Every expert follows the same knowledge-base layout:

```
experts/

engineering/

database-engineer/

├── SYSTEM.md

├── KNOWLEDGE.md

├── TOOLS.md

├── CONFIG.ts

└── TESTS/
```

Permanent / general experts live under `experts/general/`.

Domain experts live under their domain folders.

All experts implement the shared `CouncilExpert` contract (`built-in` | `custom` | `eve-agent`).

MVP only ships `built-in`.

---

# SYSTEM.md

Contains:

Identity

Role

Responsibilities

Reasoning style

Optimization goals

---

Example:

```
You are a CTO.

You optimize for:

- scalability
- maintainability
- business alignment

Challenge unnecessary complexity.
```

---

# KNOWLEDGE.md

Contains:

Domain knowledge.

Example:

CTO:

- architecture patterns
- scalability principles
- tradeoffs

---

# TOOLS.md

Defines allowed tools.

Example:

CTO:

Can:

- inspect architecture
- read files

Cannot:

- deploy

---

# CONFIG.ts

Contains:

Model

Temperature

Permissions

Weight
