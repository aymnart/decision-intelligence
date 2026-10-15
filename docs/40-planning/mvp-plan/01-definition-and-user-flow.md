> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# Purpose

This document defines the exact execution plan for building the first usable version of the Decision Intelligence Engine.

The MVP goal is NOT to build an autonomous coding company.

The MVP goal is NOT to let users customize councils.

The MVP goal is:

> Create an Autonomous Council Builder that makes better decisions than a single AI agent.

---

# MVP Definition

A user can:

1. Submit a decision/problem.

2. The system analyzes intent.

3. The system detects domain and impact.

4. The system retrieves and ranks expert candidates from the registry.

5. The system adds mandatory permanent experts.

6. Experts independently analyze the problem.

7. Experts debate.

8. Experts vote.

9. The system produces a final consensus report.

10. The decision is stored for future reference.

The engine decides who participates. Users do not customize councils in MVP.

---

# MVP User Flow

```
User

↓

"Should my startup switch from PostgreSQL to MongoDB?"

↓

Decision Intelligence Engine

↓

Intent Analyzer

↓

Domain Detection: Software Architecture

↓

Impact: High

↓

Council Assembly Engine

↓

Required:

CTO

Backend Architect

Database Engineer

Performance Engineer

Security Engineer

Mandatory:

Devil's Advocate

Risk Analyst

Critical Thinker

↓

Independent Analysis

↓

Debate

↓

Voting

↓

Consensus Report

↓

Save Decision

↓

Display Result
```
