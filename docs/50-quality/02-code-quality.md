> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Code Quality Standards

---

# TypeScript Rules

All TypeScript must:

- use strict mode
- avoid any
- use explicit types
- validate external inputs
- use meaningful names

---

Bad:

```ts
const x:any = data;
```

Good:

```ts
const user: User = parseUser(data);
```

---

# Naming Rules

Names must communicate intent.

Bad:

```
handleData()
process()
manager()
```

Good:

```
createDecisionReport()

validateGitHubRepository()

calculateConsensusScore()
```

---

# Function Rules

Functions should:

- do one thing
- be small
- have clear inputs
- have predictable outputs

Avoid:

```
500 line functions
```

---

# Error Handling

Errors must:

- be meaningful
- include context
- be recoverable
- be logged

Bad:

```ts
throw Error("failed")
```

Good:

```ts
throw new DecisionExecutionError(
"Consensus generation failed",
{
decisionId,
expertId
}
)
```

---

# Architecture Quality

Every feature must respect:

```
Presentation Layer

↓

Application Layer

↓

Domain Layer

↓

Infrastructure Layer
```

---

# Dependency Rules

Domain logic cannot depend on:

- frameworks
- databases
- APIs
- UI

Infrastructure depends on domain.

Not the opposite.
