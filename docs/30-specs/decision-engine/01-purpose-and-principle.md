> Part of [Decision Intelligence Engine Specification](README.md).

# Purpose

The Decision Intelligence Engine is the brain of the system.

It controls:

- what decisions require reasoning
- which domains are involved
- which experts participate
- how much reasoning is needed
- how debates happen
- how consensus is reached
- how decisions are stored
- how future decisions use previous knowledge

The Decision Engine is responsible for decision quality.

It is not responsible for execution.

---

# Core Principle

Never directly execute user requests.

Every request must pass through:

```
User Request

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification

↓

Context Retrieval

↓

Retrieve Expert Candidates

↓

Rank Experts

↓

Add Mandatory Experts

↓

Create Council

↓

Expert Reasoning

↓

Debate

↓

Consensus

↓

Decision Memory

↓

Execution Planning
```
