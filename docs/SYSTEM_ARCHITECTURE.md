# System Architecture

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

The product is the **Decision Intelligence Engine** (`decision-intelligence`).

AI Council is not a fixed group of experts.

It is a **Dynamic Council Assembly Engine** inside this product.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

See `AI_COUNCIL.md` for the full product vision, permanent experts, expert interface, and MVP constraints.

---

# Overview

The Decision Intelligence Engine is composed of independent layers.

Every layer has exactly one responsibility.

The system follows a strict pipeline.

```
User Request

↓

Decision Intelligence Engine

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification (impact)

↓

Council Assembly Engine

↓

Required Experts + Permanent Experts

↓

Expert Council

↓

Debate Engine

↓

Consensus Engine

↓

Decision + Memory

↓

Execution Planner

↓

Executor

↓

Artifacts

↓

Human Approval (if needed)

↓

Execution
```

No component should skip another component.

The system must never execute before architectural decisions are finalized.

MVP note: the engine assembles councils automatically. User-customized councils and Eve-agent experts are post-MVP.

---

# High Level Architecture

```
apps/
    web/

packages/

    core/

    council/

    decision-engine/

    executor/

    memory/

    planner/

    github/

    prompts/

    shared/

    types/

agents/

docs/
```

Every package must remain independent.

Circular dependencies are forbidden.

---

# Core Components

The system consists of ten major systems.

---

## 1

Intent Detection

Responsibility

Understand what the user wants.

Examples

Build SaaS

Fix bug

Generate architecture

Create GitHub repo

Review code

Create roadmap

Generate issues

Refactor project

The output is always structured.

Example

```
Intent

Architecture

Confidence

0.97
```

---

## 2

Decision Classifier

One of the most important components.

Every request must be classified.

### Low Impact

Examples

Rename variable

Formatting

Comments

README edits

Single file changes

Uses:

One expert.

---

### Medium Impact

Examples

Folder structure

API design

Database schema

Testing strategy

Uses:

Small council.

Usually

3–5 experts.

---

### High Impact

Examples

Frontend framework

Backend architecture

Database

Authentication

Deployment

AI provider

Project planning

Uses:

Entire council.

This optimization dramatically reduces cost.

---

## 3

Council Assembly Engine

Never instantiate every expert.

Never use a fixed always-on roster.

Instead:

1. Retrieve expert candidates from the expert knowledge base
2. Rank by domain relevance
3. Add mandatory permanent experts (quality-control agents)
4. Create a temporary Expert Council for this request

Example

User

```
Design authentication
```

Council

```
Required:

CTO

Backend

Security

DevOps

Staff Engineer

Permanent:

Devil's Advocate

Risk Analyst

Critical Thinker
```

Example

Landing Page

```
Required:

Product

UI

UX

Marketing

Startup Advisor

Permanent:

Critical Thinker

Devil's Advocate
```

This saves tokens and improves reasoning quality.

Experts live in a domain knowledge base (`experts/engineering`, `experts/business`, `experts/legal`, `experts/general`, etc.), not as hardcoded one-off prompts.

---

## 4

Expert Runner

Every expert runs independently.

Experts cannot initially see each other's responses.

Each receives

Task

Context

Relevant project decisions

Relevant documentation

Constraints

Each expert returns JSON.

Never plain text.

Example

```
Decision

Reasoning

Pros

Cons

Alternatives

Confidence

Vote
```

---

## 5

Debate Engine

The Debate Engine is the heart of the system.

Pipeline

Round 1

Independent reasoning

↓

Round 2

Experts receive summaries of every opinion.

↓

Experts critique each other.

↓

Experts may change opinion.

↓

Vote again.

↓

Consensus.

This prevents anchoring bias.

---

## 6

Consensus Engine

The Consensus Engine never simply counts votes.

It considers

Confidence

Expert priority

Agreement

Tradeoffs

Minority reports

Risk

Unknowns

Example

```
Winner

Next.js

Confidence

92%

Agreement

84%

Minority

TanStack Start

Reason

Performance advantages
did not outweigh ecosystem maturity.
```

---

## 7

Decision Memory

Every accepted decision becomes permanent project knowledge.

Example

```
Decision

Authentication

Winner

Better Auth

Reason

...

Tradeoffs

...

Date

...

Dependencies
```

Future discussions reference previous decisions.

Nothing is forgotten.

---

## 8

Execution Planner

The planner converts decisions into work.

Architecture

↓

Roadmap

↓

Phases

↓

Milestones

↓

Tasks

↓

Issues

↓

Execution Order

The planner never writes code.

---

## 9

Executor

The executor performs work.

Examples

Run create-better-t-stack

Generate files

Create GitHub repo

Create labels

Generate Kanban

Generate roadmap

Generate documentation

Create issues

Push commits

Run tests

Deploy

The executor never makes architectural decisions.

---

## 10

Artifact Generator

Every execution produces artifacts.

Examples

PROJECT.md

ARCHITECTURE.md

STACK.md

DESIGN.md

ROADMAP.md

DECISIONS.md

ISSUES.md

Every artifact becomes project memory.

---

# Execution Pipeline

```
User Request

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification (impact)

↓

Relevant Context Retrieval

↓

Retrieve + Rank Expert Candidates

↓

Add Mandatory Experts

↓

Create Temporary Council

↓

Independent Expert Opinions

↓

Debate

↓

Voting

↓

Consensus

↓

Store Decision

↓

Execution Planning

↓

Approval

↓

Execution

↓

Artifacts

↓

Project Memory Updated
```

---

# Component Communication

Every component communicates using strongly typed objects.

Never strings.

Never free-form prompts.

Example

```
Intent

↓

DecisionRequest

↓

ExpertOpinion

↓

DebateRound

↓

ConsensusDecision

↓

ExecutionPlan

↓

ExecutionResult
```

---

# Event Driven Architecture

Every important event should emit an event.

Examples

DecisionStarted

ExpertCompleted

DebateStarted

ConsensusReached

ExecutionStarted

ArtifactGenerated

ExecutionFinished

ApprovalRequested

ApprovalGranted

These events power observability.

---

# Parallelism

Experts should execute in parallel.

Debate occurs after all opinions complete.

Executors should execute in parallel where safe.

Example

Generate documentation

+

Generate roadmap

+

Generate design system

can happen simultaneously.

---

# Human Approval

Certain operations pause execution.

Examples

Repository creation

Push

Merge

Deployment

Deleting files

Deleting repos

Billing

Execution resumes after approval.

---

# Fault Tolerance

Every component must support retries.

Expert fails

↓

Retry

↓

Fallback model

↓

Report failure

↓

Continue if possible

No single expert failure should crash the system.

---

# Logging

Every important action should be logged.

Examples

Prompt sent

Tokens used

Latency

Votes

Consensus

Execution time

Errors

Retries

Approval requests

Artifacts generated

---

# Extensibility

Experts are plugins.

Executors are plugins.

Providers are plugins.

Memory systems are plugins.

Nothing should require changing the core architecture.

---

# Framework Independence

The architecture must not depend on Eve.

The architecture should support replacing Eve with another orchestration runtime.

The following are implementation details

Eve

OpenAI Agents SDK

LangGraph

Temporal

Mastra

etc.

The Decision Engine remains unchanged.

---

# Source of Truth

Only one source of truth exists for each concern.

Examples

Architecture

ARCHITECTURE.md

Design

DESIGN.md

Roadmap

ROADMAP.md

Technical decisions

DECISIONS.md

Never duplicate project knowledge.

---

# Scalability Roadmap

MVP

Single project

↓

V2

Multiple projects

↓

V3

Shared organizational knowledge

↓

V4

Cross-project reasoning

↓

V5

Multi-agent autonomous software company

The architecture should support all future stages without major redesign.

---

# Golden Rule

Every module should answer one question.

Intent Analyzer

"What does the user want?"

Domain Detection

"What domains does this touch?"

Decision Classifier

"How important is this decision?"

Council Assembly Engine

"Who should participate in this temporary organization?"

Expert Runner

"What does each expert think?"

Debate Engine

"Did anyone change their mind?"

Consensus Engine

"What should we do?"

Decision Memory

"Why did we decide this?"

Execution Planner

"How do we accomplish it?"

Executor

"Can we perform it?"

Artifact Generator

"What permanent knowledge should we create?"

If a module answers more than one question, split it.
