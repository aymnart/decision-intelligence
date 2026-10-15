> Part of [Tech Stack](README.md).

# Version Policy

Always use

Latest stable versions.

Avoid beta releases in production.

Major upgrades require:

- testing
- ADR
- changelog

---

# Stack Governance

Adding a dependency requires answering:

1. What problem does it solve?

2. Can an existing dependency solve it?

3. Is it maintained?

4. Does it improve developer experience?

5. Does it introduce vendor lock-in?

If the answer is unclear,

Do not add it.

---

# Technology Decision Process

Every major technology choice follows:

```
Proposal

↓

AI Council Review

↓

Architecture Decision Record

↓

STACK.md Update

↓

Implementation
```

---

# Future Technologies

Potential future additions

- Temporal
- OpenSearch
- pgvector
- Kubernetes
- Bun runtime
- Rust services
- MCP integrations
- Multi-region deployment

These are intentionally excluded from the MVP.

---

# Golden Rules

1. Prefer simplicity over novelty.

2. Prefer type safety over convenience.

3. Prefer portability over vendor lock-in.

4. Keep the Decision Engine framework-independent.

5. Eve is an implementation detail, not the architecture.

6. AI providers must be interchangeable.

7. Do not introduce infrastructure before it is needed.

8. Every major stack change must be documented.

9. The stack serves the architecture—not the other way around.

10. Consistency beats perfection.
