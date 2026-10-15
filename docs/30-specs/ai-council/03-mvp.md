> Part of [AI Council System Specification](README.md).

# MVP: Autonomous Council Builder

The MVP should **not allow users to customize councils yet**.

The engine decides.

Example:

User:

> "Should my startup switch from PostgreSQL to MongoDB?"

The engine detects:

```
Domain:
Software Architecture

Impact:
High

Required experts:

✓ CTO
✓ Backend Architect
✓ Database Engineer
✓ Performance Engineer
✓ Security Engineer

Mandatory:

✓ Devil's Advocate
✓ Risk Analyst
✓ Critical Thinker
```

Then it runs.

## MVP Must Prove

> Can an automatically generated council outperform a single AI?

## MVP Build Order

1. Expert registry
2. Domain classifier
3. Council builder
4. Permanent experts
5. Debate engine
6. Consensus engine
7. Memory

## Explicitly Later (Not MVP)

- custom experts
- Eve agents as council members
- company knowledge
- private councils
- user-customized councils
