> Part of [Decision Intelligence Engine](README.md).

# Project Rules

Every important feature must be:

Testable

Typed

Documented

Observable

Composable

Reusable

Replaceable

No hardcoded business logic.

No duplicated prompts.

No duplicated expert definitions.

No duplicated workflows.

---

# Architecture Rules

Use clean architecture.

Domain driven design where appropriate.

Business logic must never depend on frameworks.

Frameworks should be replaceable.

The Decision Engine should be framework-agnostic.

The AI Council should be provider-agnostic.

The Executor should be replaceable.

Never couple reasoning to infrastructure.

---

# Coding Standards

Strict TypeScript.

No "any".

Functional where practical.

Dependency injection where appropriate.

Small modules.

Pure functions when possible.

Immutable data preferred.

Interfaces before implementations.

Prefer composition over inheritance.

---

# Error Philosophy

Every failure should:

Explain why.

Suggest recovery.

Be retryable.

Be observable.

Never silently fail.
