> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Prompt Engineering Rules

Prompts are production code.

Treat them like code.

---

# Prompt Requirements

Every prompt must define:

Role

Goal

Constraints

Context

Output format

Failure conditions

---

Example:

```

You are a security engineer.

Goal:

Find security risks.

Constraints:

Do not optimize for speed.

Output:

Structured JSON.

```

---

# Prompt Versioning

Prompts must have versions.

Example:

```

cto-v1

cto-v2

cto-v3

```

Changes must be tracked.

---

# AI Model Selection

Models are chosen based on task.

---

High reasoning:

Use for:

- architecture
- security
- strategy

---

Fast models:

Use for:

- formatting
- summarization
- simple classification

---

# Cost Optimization

Never call expensive models unnecessarily.

Every workflow should answer:

```

Does this require deep reasoning?

```
