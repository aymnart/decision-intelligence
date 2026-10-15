> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Performance Guidelines

Optimize:

- latency
- token usage
- database queries
- workflow execution

---

# AI Performance

Use:

parallel execution

caching

context filtering

model routing

---

Bad:

Send entire repository to every agent.

Good:

Send only relevant context.

---

# Database Performance

Required:

- indexes
- pagination
- query optimization

Avoid:

- N+1 queries
- unnecessary joins

---

# Observability

Every important operation must be observable.

Track:

---

# Agent Metrics

- execution time
- tokens
- failures
- retries

---

# Decision Metrics

- confidence
- disagreement
- final outcome

---

# Workflow Metrics

- duration
- completion rate
- failure points

---

# Logging Standards

Logs must include:

Timestamp

Action

Entity ID

User ID

Result

Error details

---

Bad:

```

Error happened

```

Good:

```

Consensus generation failed

decisionId:

123

expert:

security

reason:

timeout

```
