> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Documentation Standards

Every project must maintain:

```

README.md

PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

DECISIONS.md

ROADMAP.md

```

---

# Documentation Rules

Documentation must explain:

Why

Not only:

What

---

Bad:

```

Using PostgreSQL.

```

Good:

```

PostgreSQL was selected because relational consistency
and complex querying were more important than schema flexibility.

```

---

# Code Review Standards

Every change should be reviewed against:

---

## Correctness

Does it work?

---

## Architecture

Does it fit the design?

---

## Security

Can it be abused?

---

## Performance

Will it scale?

---

## Maintainability

Will future engineers understand it?

---

# AI Generated Code Review

Before accepting AI-generated code:

The system should run:

```

Architecture Review

Security Review

Quality Review

Testing Review

```
