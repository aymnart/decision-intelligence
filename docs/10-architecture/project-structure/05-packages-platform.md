> Part of [Project Structure Specification](README.md).

# packages/prompts

Central prompt management.

Never place prompts inside random files.

Each expert's own prompt lives in `experts/<domain>/<expert>/SYSTEM.md` ([Expert Structure](06-expert-structure.md)). This package holds pipeline prompts and the loader that reads expert files ([ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction)).

Structure:

```
prompts/

pipeline/

    classification.md

    debate.md

    consensus.md


tasks/

    architecture.md

    planning.md
```

---

# packages/database

Database layer.

Contains:

- schema
- migrations
- queries
- repositories

Recommended:

PostgreSQL.

ORM:

Drizzle ORM (decided in [Data and Infrastructure](../tech-stack/05-data-and-infrastructure.md#orm) and [ADR-013](../../90-records/decisions/02-mvp-design.md#adr-013-mvp-database-schema); Prisma rejected).

---

# packages/ai

AI provider abstraction.

Supports:

- OpenAI
- Anthropic
- Google
- local models

Example:

```
ai/

providers/

models/

completion/

embeddings/
```

Never call providers directly.

---

# packages/observability

Contains:

- logging
- tracing
- metrics

Track:

- agent executions
- tokens
- latency
- failures
- decisions

---

# packages/security

Contains:

- permissions
- approvals
- validation
- secret handling

---

# packages/shared

Small utilities.

Examples:

- date helpers
- validation
- formatting

Must remain lightweight.
