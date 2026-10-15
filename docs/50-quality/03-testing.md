> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Testing Strategy

Every important feature requires testing.

---

# Unit Tests

Required for:

- business logic
- decision calculations
- scoring
- validators

---

Example:

Test:

```
Consensus score calculation
```

Input:

```
5 experts

80% agreement
```

Expected:

```
High confidence
```

---

# Integration Tests

Required for:

- AI providers
- databases
- GitHub API
- Eve workflows

---

# Workflow Tests

Critical workflows require full tests.

Example:

```
Create Project

↓

Council

↓

Decision

↓

Artifacts
```

---

# Test Coverage

Coverage is not the goal.

Quality is the goal.

Prioritize:

Critical paths

Security

Business logic

Decision engine
