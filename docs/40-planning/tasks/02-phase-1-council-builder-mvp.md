> Part of [Decision Intelligence Engine Task List](README.md).

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

- Devil's Advocate (medium and high impact)
- Risk Analyst (medium and high impact)
- Critical Thinker (medium and high impact)
- Ethics Reviewer (sensitive domains)

Inclusion rules per impact level: [ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level).

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
