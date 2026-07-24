# Decision Intelligence Engine Task List

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**.

MVP proves autonomous assembly can outperform a single AI. Do not build custom experts or Eve-agent council members first.

See `AI_COUNCIL.md`.

---

# Purpose

This document converts the implementation roadmap into executable engineering tasks.

Every task should become a GitHub issue.

Tasks are ordered by dependency.

Do not implement future phases before completing required foundations.

---

# Phase 0 — Foundation

## EPIC: Repository Setup

---

## Issue 001

Title:

Initialize monorepo architecture

Description:

Create the initial repository structure using a scalable monorepo setup.

Requirements:

- Configure pnpm workspaces
- Configure Turborepo
- Configure TypeScript
- Create package structure
- Add shared configuration

Acceptance Criteria:

- Repository installs successfully
- Packages resolve correctly
- TypeScript builds successfully

Priority:

Critical

---

## Issue 002

Title:

Configure development environment

Description:

Create the developer environment.

Requirements:

- Environment variables
- Local database
- Development scripts
- Formatting
- Linting

Acceptance Criteria:

Developer can clone repository and run locally.

---

## Issue 003

Title:

Setup database infrastructure

Description:

Create PostgreSQL database layer.

Requirements:

- Database connection
- Migration system
- ORM selection
- Development database

Acceptance Criteria:

Application can connect to database.

---

# EPIC: AI Provider Layer

---

## Issue 004

Title:

Create AI provider abstraction

Description:

Create a provider-independent AI interface.

Requirements:

Support:

- text generation
- streaming
- embeddings
- structured outputs

Interface:

```
AIProvider

generate()

stream()

embed()

```

Acceptance Criteria:

AI providers can be swapped without changing business logic.

---

## Issue 005

Title:

Implement first AI provider

Description:

Connect first production AI model provider.

Requirements:

- API integration
- Error handling
- Retry logic
- Token tracking

Acceptance Criteria:

System can execute AI requests.

---

# Phase 1 — Autonomous Council Builder MVP

---

# EPIC: Expert System

---

## Issue 006

Title:

Create expert registry knowledge base

Description:

Create a database and code system for managing AI experts as a domain knowledge base.

Requirements:

Store:

- name
- domain[]
- type (built-in | custom | eve-agent)
- instructions
- capabilities
- weight
- alwaysIncluded
- permissions

Organize seed content under:

```
experts/engineering
experts/business
experts/legal
experts/general
```

Acceptance Criteria:

Experts can be created, retrieved by domain, and ranked for assembly.

MVP only uses built-in experts.

---

## Issue 007

Title:

Create initial expert definitions

Description:

Create MVP built-in experts.

Permanent / general:

- Devil's Advocate (alwaysIncluded)
- Risk Analyst (alwaysIncluded)
- Critical Thinker (alwaysIncluded)
- Ethics Reviewer (sensitive domains)

Domain seeds:

- CTO
- Backend Architect
- Database Engineer
- Security Engineer
- Product Manager
- UX Designer

Acceptance Criteria:

Each expert has:

- identity
- domains
- goals
- reasoning style
- output format
- shared CouncilExpert contract

---

## Issue 008

Title:

Create expert execution engine

Description:

Build the system that sends tasks to experts.

Requirements:

- Load expert configuration
- Generate prompts
- Validate output against ExpertOpinion contract
- Store responses

Acceptance Criteria:

Multiple experts can analyze one problem through one interface.

---

# EPIC: Decision Engine MVP

---

## Issue 009

Title:

Create decision data model

Description:

Implement decision storage.

Store:

- question
- intent
- domain(s)
- category
- impact
- assembled council
- expert opinions
- final decision

Acceptance Criteria:

Decisions can be saved and retrieved.

---

## Issue 010

Title:

Implement autonomous council decision workflow

Description:

Create first decision pipeline.

Flow:

```
Question

↓

Intent Analyzer

↓

Domain Detection

↓

Impact Classification

↓

Retrieve + Rank Experts

↓

Add Mandatory Experts

↓

Debate

↓

Consensus

↓

Memory
```

Acceptance Criteria:

User receives a council decision from an automatically assembled council.

Users cannot customize council membership in MVP.

---

# EPIC: Consensus MVP

---

## Issue 011

Title:

Implement voting system

Description:

Create basic voting mechanism.

Requirements:

- collect votes
- calculate agreement
- calculate confidence

Acceptance Criteria:

System identifies winning recommendation.

---

## Issue 012

Title:

Generate consensus report

Description:

Create final structured decision output.

Output:

- recommendation
- reasoning
- alternatives
- risks
- minority opinion

Acceptance Criteria:

Decision report is generated.

---

# Phase 2 — Advanced Decision Engine

---

## Issue 013

Title:

Create decision impact classifier

Description:

Automatically classify decisions.

Categories:

- low
- medium
- high

Acceptance Criteria:

System selects correct reasoning depth.

---

## Issue 014

Title:

Create dynamic council assembly engine

Description:

Select experts based on problem using the assembly algorithm.

Input:

Intent, domains, impact

Process:

Retrieve candidates → Rank → Add mandatory experts → Create council

Output:

Required experts + permanent quality-control agents

Acceptance Criteria:

Only relevant experts participate; mandatory experts are always injected when required.

---

## Issue 015

Title:

Implement debate engine

Description:

Create multi-round expert debate.

Rounds:

1. Independent opinions

2. Criticism

3. Revision

Acceptance Criteria:

Experts can update opinions; permanent experts apply challenge pressure.

---

## Issue 016

Title:

Implement weighted consensus

Description:

Improve voting quality.

Requirements:

- expert weights
- confidence
- category relevance

Acceptance Criteria:

Final decision considers expertise.

---

# Phase 3 — Project Intelligence

---

## Issue 017

Title:

Create project memory system

Description:

Store project knowledge.

Store:

- decisions
- documents
- context

Acceptance Criteria:

Future decisions can retrieve previous knowledge.

---

## Issue 018

Title:

Implement context retrieval

Description:

Retrieve relevant project information before decisions.

Sources:

- markdown files
- decisions
- code

Acceptance Criteria:

Experts receive relevant context only.

---

## Issue 019

Title:

Create decision graph

Description:

Connect related decisions.

Example:

```
Framework

↓

Database

↓

Architecture
```

Acceptance Criteria:

Changing one decision reveals dependencies.

---

# Phase 4 — AI Project Architect

---

## Issue 020

Title:

Create product planning workflow

Description:

Generate product specifications.

Output:

- target users
- problems
- features
- MVP

---

## Issue 021

Title:

Create architecture generation workflow

Description:

Generate:

- architecture document
- stack decision
- infrastructure plan

---

## Issue 022

Title:

Create DESIGN.md generator

Description:

Generate complete design system.

Includes:

- colors
- typography
- spacing
- components
- interaction rules

---

## Issue 023

Title:

Create roadmap generator

Description:

Generate:

- phases
- milestones
- priorities

---

# Phase 5 — GitHub Automation

---

## Issue 024

Title:

Create GitHub integration

Description:

Connect GitHub API.

Capabilities:

- repositories
- issues
- projects

---

## Issue 025

Title:

Automate repository creation

Description:

Create repositories from approved projects.

---

## Issue 026

Title:

Generate GitHub project board

Description:

Create Kanban workflow.

Columns:

- Backlog
- Ready
- Progress
- Review
- Done

---

## Issue 027

Title:

Generate GitHub issues from roadmap

Description:

Convert roadmap into executable tasks.

Every issue contains:

- description
- acceptance criteria
- dependencies

---

# Phase 6 — Eve Integration

---

## Issue 028

Title:

Integrate Eve runtime

Description:

Move workflows into Eve execution.

Requirements:

- subagents
- tools
- durable workflows

---

## Issue 029

Title:

Create Eve expert agents

Description:

Convert experts into Eve agents.

---

## Issue 030

Title:

Implement human approval system

Description:

Require approval for dangerous actions.

Examples:

- repository creation
- deployment
- merge

---

# Phase 7 — Coding Agents

---

## Issue 031

Title:

Create coding workflow

Description:

Implement:

Issue

↓

Plan

↓

Code

↓

Test

↓

PR

---

## Issue 032

Title:

Create code review agent

Description:

Review generated code.

Checks:

- architecture
- security
- quality

---

## Issue 033

Title:

Create testing agent

Description:

Generate and execute tests.

---

# Phase 8 — Autonomous Engineering Team

---

## Issue 034

Title:

Create autonomous project manager

Description:

AI manages backlog and priorities.

---

## Issue 035

Title:

Create technical debt agent

Description:

Find:

- outdated dependencies
- bad patterns
- refactoring opportunities

---

## Issue 036

Title:

Create continuous improvement workflow

Description:

AI continuously improves projects.

---

# MVP Completion Definition

The MVP is complete when:

A user can:

1. Ask any decision question

2. System analyzes intent, domain, and impact

3. System automatically assembles Required Experts + Permanent Experts

4. Experts debate

5. Consensus is produced

6. Decision is stored

7. Previous decisions can be referenced

Users cannot customize councils yet.

Success metric:

> Automatically generated councils outperform a single AI.

---

# Recommended First Sprint

Implement only:

```
001

003

004

006

007

008

009

010

011

012
```

Result:

A functional AI Council.

Everything else builds on this.
