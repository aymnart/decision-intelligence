> Part of [Decision Intelligence Engine](README.md).

# Fundamental Principle

The Decision Intelligence Engine is the product.

The Dynamic Council Assembly Engine is its core mechanism.

Everything else uses the council.

Never embed architectural intelligence directly inside workflows.

Instead:

```
AI Agent / User Request

↓

Needs a decision

↓

Decision Intelligence Engine

↓

Intent + Domain + Impact

↓

Council Assembly Engine

↓

Required Experts + Permanent Experts

↓

Debate → Consensus → Memory

↓

Executor (when applicable)
```

Every future feature must consume the Decision Intelligence Engine.

MVP must not allow user-customized councils. The engine decides.

Custom experts and Eve-agent council members come later.

---

# Non Goals

This project is NOT:

- another Cursor clone

- another Claude Code clone

- another Copilot

- another chat interface

It is an Engineering Operating System.

---

# Design Principles

The system must always:

Think deeply.

Challenge assumptions.

Consider alternatives.

Evaluate tradeoffs.

Document reasoning.

Produce deterministic outputs whenever possible.

Explain why.

Never optimize for short prompts.

Optimize for engineering quality.

---

# Development Philosophy

Prefer boring technology.

Prefer mature libraries.

Avoid unnecessary abstractions.

Optimize for readability.

Optimize for maintainability.

Optimize for explicitness.

Avoid magic.

Avoid hidden state.

Avoid implicit behavior.

Every file should have one responsibility.

Every module should have a clear owner.
