# Project Structure Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**.

Experts are a knowledge base, not a fixed always-on roster.

See `AI_COUNCIL.md`.

---

# Purpose

This document defines the codebase architecture for the AI Engineering Operating System.

The project must be modular, scalable, and maintainable.

The architecture separates:

- Core intelligence (Decision Intelligence Engine)
- Council assembly
- AI orchestration
- Decision making
- Memory
- Execution
- External integrations
- User interface

No package should contain responsibilities belonging to another layer.

---

# Architecture Style

Use:

- Monorepo architecture
- TypeScript everywhere
- Package-based separation
- Clean architecture principles
- Domain-driven organization

Recommended tooling:

- pnpm workspaces
- Turborepo
- TypeScript project references

---

# Repository Structure

```
ai-engineering-os/

│
├── apps/
│
│   ├── web/
│   │
│   └── api/
│
│
├── packages/
│
│   ├── core/
│   │
│   ├── decision-engine/
│   │
│   ├── council/
│   │
│   ├── consensus/
│   │
│   ├── memory/
│   │
│   ├── planner/
│   │
│   ├── executor/
│   │
│   ├── workflows/
│   │
│   ├── github/
│   │
│   ├── eve/
│   │
│   ├── prompts/
│   │
│   ├── database/
│   │
│   ├── ai/
│   │
│   ├── observability/
│   │
│   ├── security/
│   │
│   └── shared/
│
│
├── agents/
│
│   └── (runtime wrappers / Eve adapters — optional)
│
│
├── experts/
│
│   ├── engineering/
│   │
│   │   ├── backend-architect/
│   │   ├── frontend-architect/
│   │   └── database-engineer/
│   │
│   ├── business/
│   │
│   │   ├── cfo/
│   │   ├── startup-advisor/
│   │   └── marketer/
│   │
│   ├── legal/
│   │
│   │   ├── lawyer/
│   │   └── compliance-specialist/
│   │
│   └── general/
│
│       ├── devil-advocate/
│       ├── critical-thinker/
│       ├── risk-analyst/
│       └── ethics-reviewer/
│
│
├── docs/
│
├── scripts/
│
├── tests/
│
├── .env.example
│
├── package.json
│
├── pnpm-workspace.yaml
│
└── turbo.json
```

---

# Package Responsibilities

---

# apps/web

Responsibility:

User interface.

Contains:

- dashboard
- conversations
- decisions
- approvals
- artifacts
- project views

Must NOT contain:

- AI logic
- expert prompts
- decision rules

---

# apps/api

Responsibility:

API layer.

Handles:

- authentication
- requests
- streaming responses
- workflow triggers

Must NOT contain:

- business logic

---

# packages/core

The foundation package.

Contains:

- common types
- domain objects
- interfaces
- constants

Example:

```
core/

types/

Decision.ts

Expert.ts

Workflow.ts

Artifact.ts
```

Every package can depend on core.

Core depends on nothing.

---

# packages/decision-engine

The brain — Decision Intelligence Engine.

Contains:

- intent analyzer
- domain detection
- decision classifier
- impact analysis
- council assembly logic
- decision lifecycle

Example:

```
decision-engine/

intent/

domain/

classifier/

assembly/

lifecycle/

rules/
```

---

# packages/council

Responsible for:

- expert registry / knowledge base
- expert execution
- temporary council creation
- permanent expert injection

Contains:

```
council/

experts/

builder/

runner/

registry/
```

MVP: built-in experts only. Custom and Eve-agent types share the same `CouncilExpert` interface but are post-MVP.

---

# packages/consensus

Responsible for:

- debate processing
- voting
- confidence scoring
- final recommendations

Contains:

```
consensus/

debate/

voting/

scoring/

reports/
```

---

# packages/memory

Responsible for project knowledge.

Handles:

- decisions
- documents
- previous conversations
- context retrieval

Contains:

```
memory/

storage/

retrieval/

embeddings/

ranking/
```

---

# packages/planner

Responsible for converting decisions into execution plans.

Examples:

```
Architecture

↓

Roadmap

↓

Milestones

↓

Tasks

↓

Issues
```

Contains:

```
planner/

roadmap/

milestones/

tasks/

dependencies/
```

---

# packages/executor

Responsible for performing actions.

Examples:

- create files
- run commands
- modify projects
- generate artifacts

Contains:

```
executor/

commands/

actions/

approvals/

validators/
```

---

# packages/workflows

Contains complete business workflows.

Examples:

```
workflows/

create-project/

architecture-review/

feature-development/

bug-fix/

code-review/
```

A workflow orchestrates multiple packages.

---

# packages/github

GitHub integration.

Contains:

```
github/

repositories/

issues/

projects/

pull-requests/

labels/
```

---

# packages/eve

Eve integration layer.

Important:

Only this package knows Eve exists.

Everything else remains framework independent.

Contains:

```
eve/

agents/

tools/

workflows/

adapters/
```

---

# packages/prompts

Central prompt management.

Never place prompts inside random files.

Structure:

```
prompts/

experts/

    cto.md

    security.md

    product.md


tasks/

    architecture.md

    planning.md
```

---

# packages/database

Database layer.

Contains:

- schema
- migrations
- queries
- repositories

Recommended:

PostgreSQL.

ORM:

Choose through council.

Possible:

- Drizzle
- Prisma

---

# packages/ai

AI provider abstraction.

Supports:

- OpenAI
- Anthropic
- Google
- local models

Example:

```
ai/

providers/

models/

completion/

embeddings/
```

Never call providers directly.

---

# packages/observability

Contains:

- logging
- tracing
- metrics

Track:

- agent executions
- tokens
- latency
- failures
- decisions

---

# packages/security

Contains:

- permissions
- approvals
- validation
- secret handling

---

# packages/shared

Small utilities.

Examples:

- date helpers
- validation
- formatting

Must remain lightweight.

---

# Expert Structure

Every expert follows the same knowledge-base layout:

```
experts/

engineering/

database-engineer/

├── SYSTEM.md

├── KNOWLEDGE.md

├── TOOLS.md

├── CONFIG.ts

└── TESTS/
```

Permanent / general experts live under `experts/general/`.

Domain experts live under their domain folders.

All experts implement the shared `CouncilExpert` contract (`built-in` | `custom` | `eve-agent`).

MVP only ships `built-in`.

---

# SYSTEM.md

Contains:

Identity

Role

Responsibilities

Reasoning style

Optimization goals

---

Example:

```
You are a CTO.

You optimize for:

- scalability
- maintainability
- business alignment

Challenge unnecessary complexity.
```

---

# KNOWLEDGE.md

Contains:

Domain knowledge.

Example:

CTO:

- architecture patterns
- scalability principles
- tradeoffs

---

# TOOLS.md

Defines allowed tools.

Example:

CTO:

Can:

- inspect architecture
- read files

Cannot:

- deploy

---

# CONFIG.ts

Contains:

Model

Temperature

Permissions

Weight

---

# Database Models

Core entities:

---

# Project

```
id

name

description

status

createdAt
```

---

# Decision

```
id

projectId

title

category

impact

status

result

confidence

createdAt
```

---

# ExpertOpinion

```
id

decisionId

expertId

reasoning

vote

confidence
```

---

# Debate

```
id

decisionId

round

messages
```

---

# Artifact

```
id

projectId

type

content

version
```

---

# Workflow

```
id

type

status

currentStep

state
```

---

# Execution

```
id

workflowId

action

status

result
```

---

# Dependency Rules

Allowed:

```
web

↓

api

↓

workflows

↓

decision-engine

↓

council

↓

ai
```

---

Forbidden:

```
council

↓

web
```

```
database

↓

decision-engine
```

Core must stay independent.

---

# Testing Strategy

Every package requires:

Unit tests

Integration tests

Workflow tests

---

Critical tests:

Decision classification

Expert selection

Consensus calculation

Memory retrieval

Workflow recovery

---

# Development Order

Build in this order:

## Phase 1

Core types

Database

AI abstraction

## Phase 2

Council engine

Experts

Decision engine

## Phase 3

Consensus engine

## Phase 4

Memory system

## Phase 5

Workflows

## Phase 6

Eve integration

## Phase 7

UI

---

# Golden Rule

The codebase should look like a company built this.

Not a collection of AI scripts.

Every component should have a clear purpose, boundary, and owner.
