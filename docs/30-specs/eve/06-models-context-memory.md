> Part of [Eve Implementation Specification](README.md).

# Model Selection

Different experts can use different models.

Example:

High reasoning:

Architecture

↓

Advanced reasoning model

Simple tasks:

Documentation

↓

Fast cheap model

---

# Context Management

Agents receive:

Project context

Previous decisions

Relevant documents

Current task

Constraints

They do NOT receive unnecessary information.

---

# Memory Integration

Before running an expert:

Retrieve:

Relevant decisions

Previous discussions

Project documents

Technology choices

---

Example:

Question:

"Add authentication"

Memory:

```
Previous decision:

Use Better Auth.

Reason:

TypeScript compatibility.

Rejected:

Auth.js.
```

Expert should know this.
