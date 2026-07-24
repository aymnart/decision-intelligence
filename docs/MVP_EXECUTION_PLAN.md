# Decision Intelligence Engine MVP Execution Plan

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**, not a fixed group of experts.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

See `AI_COUNCIL.md`.

---

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

---

# MVP Technical Stack

The stack should prioritize speed and maintainability.

---

# Frontend

Use:

```
Next.js

React

TypeScript

Tailwind CSS

shadcn/ui
```

Purpose:

Dashboard

Decision interface

Expert visualization

Reports

---

# Backend

Use:

```
Next.js API Routes

or

Separate Node.js API
```

For MVP:

Prefer Next.js full-stack.

Reason:

- faster development
- fewer moving parts
- easy deployment

---

# Database

Use:

```
PostgreSQL
```

Reason:

The system has highly relational data:

- decisions
- experts
- votes
- debates
- workflows

ORM:

Choose:

```
Drizzle ORM
```

Reason:

- TypeScript first
- lightweight
- SQL control

---

# Authentication

Use:

```
Better Auth
```

Reason:

- TypeScript native
- simple integration
- self-host friendly

---

# AI Layer

Create abstraction.

Do not directly call providers.

Architecture:

```
Application

↓

AI Provider Interface

↓

OpenAI

Anthropic

Google

```

---

# MVP Models

Recommended:

Reasoning model:

Architecture decisions

↓

Claude / GPT reasoning model

Fast model:

Simple summaries

↓

Fast cheaper model

---

# Project Structure

MVP implementation:

```
packages/

core

ai

council

decision-engine

consensus

memory


apps/

web
```

Do not build:

- GitHub automation
- Eve workflows
- autonomous coding

yet.

---

# Database Schema

---

# User

```
id

email

createdAt
```

---

# Decision

```
id

userId

title

description

category

impact

status

result

confidence

createdAt
```

---

# Expert

```
id

name

role

prompt

weight
```

---

# Expert Opinion

```
id

decisionId

expertId

reasoning

recommendation

confidence

vote
```

---

# Debate Message

```
id

decisionId

expertId

round

content
```

---

# Consensus

```
id

decisionId

finalDecision

agreement

minorityOpinion

tradeoffs
```

---

# MVP Implementation Order

---

# Sprint 1

## Foundation

Tasks:

Create repository

Setup Next.js

Setup TypeScript

Setup database

Setup ORM

Create base architecture

Output:

Working application.

---

# Sprint 2

## AI Provider System

Tasks:

Create AI interface.

Implement provider.

Add:

- generation
- structured outputs

Output:

Application can communicate with AI.

---

# Sprint 3

## Expert System

Tasks:

Create expert registry as a domain knowledge base.

Structure:

```
experts/

engineering/

business/

legal/

general/
```

Create seed built-in experts, including permanent quality-control agents:

Devil's Advocate

Risk Analyst

Critical Thinker

Ethics Reviewer

Plus domain seeds (CTO, Backend Architect, etc.).

Implement shared `CouncilExpert` contract:

- id
- name
- domain
- type: built-in | custom | eve-agent (custom/eve post-MVP)
- instructions
- capabilities
- weight
- alwaysIncluded?
- analyze(context)

Implement:

Expert prompts

Expert execution

Output:

Multiple experts can answer one question through one interface.

---

# Sprint 4

## Decision Intelligence / Council Assembly

Tasks:

Create:

Decision model

Intent analyzer

Domain classifier

Impact classifier

Council assembly engine:

- retrieve candidates
- rank experts
- add mandatory experts
- create temporary council

Output:

System automatically decides who should participate.

No user council customization in MVP.

---

# Sprint 5

## Debate System

Tasks:

Implement:

Round 1:

Independent opinions

Round 2:

Critique

Round 3:

Revision

Output:

Experts interact.

---

# Sprint 6

## Consensus Engine

Tasks:

Implement:

Voting

Confidence scoring

Agreement calculation

Final report generation

Output:

Complete council decision.

---

# Sprint 7

## Memory System

Tasks:

Store:

Previous decisions

Reasoning

Alternatives

Implement:

Basic retrieval.

Output:

The council remembers.

---

# MVP Interface

The UI should contain:

---

# Home

Input:

```
What decision do you need help with?
```

---

# Decision Page

Display:

```
Question

Impact Level

Experts Participating

```

---

# Expert Views

Show:

```
CTO opinion

Security opinion

Backend opinion

```

---

# Debate View

Show:

```
Expert disagreements

Opinion changes

Arguments
```

---

# Final Report

Display:

```
Recommendation

Confidence

Agreement

Tradeoffs

Minority Opinion

Risks
```

---

# MVP Success Metrics

The MVP succeeds if:

---

## Quality

Users prefer council answers over single AI answers.

---

## Trust

Users understand why decisions were made.

---

## Repeat Usage

Users return for future decisions.

---

## Technical

System can:

- run multiple experts
- debate
- reach consensus
- store decisions

---

# What NOT to build

Do not build:

❌ User-customized councils

❌ Custom / personal experts

❌ Eve agents as council members

❌ Company private councils

❌ GitHub automation

❌ Code generation

❌ Repository creation

❌ Project planning

❌ Design generation

❌ Autonomous coding agents

❌ Complex memory systems

❌ Multi-agent workflows beyond council debate

---

# Reason

The biggest risk is not technical.

The biggest risk is:

"Does an automatically generated AI council actually outperform a single AI?"

Validate the core intelligence first.

---

# After MVP Validation

Only after users value autonomous council assembly:

Add:

Phase 2:

Custom / personal experts

↓

Phase 3:

Eve-agent council members + company knowledge

↓

Phase 4:

Project Architect

↓

Phase 5:

GitHub Automation

↓

Phase 6:

Coding Agents

↓

Phase 7:

Autonomous Engineering Organization

---

# First Development Goal

Build this:

```
Question

↓

Intent + Domain + Impact

↓

Autonomous Council Assembly

↓

Required Experts + Permanent Experts

↓

Debate

↓

Consensus

↓

Decision Report + Memory
```

Everything else is an expansion of this foundation.
