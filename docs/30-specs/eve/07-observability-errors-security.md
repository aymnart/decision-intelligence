> Part of [Eve Implementation Specification](README.md).

# Observability

Track:

Agent execution

Token usage

Latency

Tool calls

Failures

Decision changes

Consensus changes

---

# Error Handling

If Eve agent fails:

```
Retry

↓

Fallback model

↓

Skip non-critical expert

↓

Continue

```

Never lose workflow state.

---

# Security

Never expose:

API keys

Secrets

Private repositories

User data

All tools require scoped permissions.
