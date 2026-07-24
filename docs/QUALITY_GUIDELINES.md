# AI Engineering Operating System Quality Guidelines

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**. Decision quality standards apply to automatically assembled councils — Required Experts plus Permanent Experts (Devil's Advocate, Risk Analyst, Critical Thinker, Ethics Reviewer when needed).

See `AI_COUNCIL.md`.

---

# Purpose

This document defines the engineering quality standards for the AI Engineering Operating System.

The system is designed to generate and maintain production-quality software.

Quality is not optional.

Every generated artifact, decision, workflow, and piece of code must follow these standards.

---

# Core Quality Principles

The system must optimize for:

```
Correctness

↓

Maintainability

↓

Security

↓

Performance

↓

Developer Experience

↓

Speed
```

Speed is important.

Quality is more important.

---

# Software Engineering Principles

## Principle 1

Prefer simple solutions.

Do not introduce complexity unless justified.

Bad:

```
Add microservices immediately
```

Good:

```
Start with modular monolith.
Split only when required.
```

---

## Principle 2

Every abstraction must earn its existence.

Before creating:

- classes
- services
- wrappers
- frameworks

Ask:

```
Does this remove complexity?

Or create complexity?
```

---

## Principle 3

Optimize for future engineers.

Code should be understandable by someone joining the project six months later.

---

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

---

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

---

# AI Output Quality

AI systems require evaluation.

Every AI component needs:

---

# Accuracy Evaluation

Measure:

Did the output solve the problem?

---

# Consistency Evaluation

Same input should produce similar quality.

---

# Hallucination Evaluation

Check:

Did the AI invent information?

---

# Decision Quality Evaluation

Measure:

Was the final decision reasonable?

---

# Expert Evaluation

Experts should be tested.

Example:

CTO Agent Test:

Input:

```
Choose database for SaaS
```

Expected:

Must discuss:

- scalability
- migrations
- operations
- cost

```

---

# Prompt Engineering Rules

Prompts are production code.

Treat them like code.

---

# Prompt Requirements

Every prompt must define:

Role

Goal

Constraints

Context

Output format

Failure conditions

---

Example:

```

You are a security engineer.

Goal:

Find security risks.

Constraints:

Do not optimize for speed.

Output:

Structured JSON.

```

---

# Prompt Versioning

Prompts must have versions.

Example:

```

cto-v1

cto-v2

cto-v3

```

Changes must be tracked.

---

# AI Model Selection

Models are chosen based on task.

---

High reasoning:

Use for:

- architecture
- security
- strategy

---

Fast models:

Use for:

- formatting
- summarization
- simple classification

---

# Cost Optimization

Never call expensive models unnecessarily.

Every workflow should answer:

```

Does this require deep reasoning?

```

---

# Security Guidelines

Security is mandatory.

---

# Secrets

Never:

- hardcode keys
- expose tokens
- store secrets in logs

Use:

- environment variables
- secret managers

---

# Authentication

Must include:

- secure sessions
- authorization checks
- permission boundaries

---

# AI Tool Security

Agents must have minimal permissions.

Example:

Documentation agent:

Can:

read files

Cannot:

deploy

---

# Command Execution Security

Before running commands:

Validate:

- command safety
- user approval
- permissions

Dangerous:

```

rm

delete

production deployment

```

require approval.

---

# Data Privacy

The system must:

- minimize stored data
- encrypt sensitive information
- control access

---

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

---

# Documentation Standards

Every project must maintain:

```

README.md

PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

DECISIONS.md

ROADMAP.md

```

---

# Documentation Rules

Documentation must explain:

Why

Not only:

What

---

Bad:

```

Using PostgreSQL.

```

Good:

```

PostgreSQL was selected because relational consistency
and complex querying were more important than schema flexibility.

```

---

# Code Review Standards

Every change should be reviewed against:

---

## Correctness

Does it work?

---

## Architecture

Does it fit the design?

---

## Security

Can it be abused?

---

## Performance

Will it scale?

---

## Maintainability

Will future engineers understand it?

---

# AI Generated Code Review

Before accepting AI-generated code:

The system should run:

```

Architecture Review

Security Review

Quality Review

Testing Review

```

---

# Definition of Done

A task is complete only when:

```

Code written

↓

Tests pass

↓

Documentation updated

↓

Architecture reviewed

↓

Security checked

↓

Decision recorded

```

---

# Technical Debt Management

The system must track:

- shortcuts
- compromises
- known risks

Create:

```

TECH_DEBT.md

```

---

# Failure Philosophy

Failures are information.

Every failure should improve the system.

Store:

- what failed
- why
- fix
- prevention

---

# Golden Rule

The AI Engineering Operating System must produce software that a world-class engineering team would be proud to maintain.

The goal is not generating more code.

The goal is generating better software.
