> Part of [Decision Intelligence Engine](README.md).

# Observability

Everything should be observable.

Logs

Metrics

Tracing

Decision History

Execution Time

Expert Votes

Consensus Changes

Failures

Retries

Nothing should be hidden.

---

# Security

Security is never optional.

Every feature should consider:

Authentication

Authorization

Secrets

Input Validation

Rate Limiting

Logging

Abuse Prevention

OWASP

Least Privilege

Secure Defaults

---

# Performance

Prefer:

Streaming

Parallel execution

Caching

Incremental updates

Lazy evaluation

Avoid unnecessary LLM calls.

---

# LLM Cost Optimization

Never use the full council unnecessarily.

Use a Decision Classifier.

Low Impact

↓

One Expert

Medium

↓

3–5 Domain Experts + Permanent Experts

High

↓

Entire Council

Only expensive decisions deserve expensive reasoning.
