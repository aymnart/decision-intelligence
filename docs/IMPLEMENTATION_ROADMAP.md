# Decision Intelligence Engine Implementation Roadmap

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**, not a fixed group of experts.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

MVP proves autonomous assembly can outperform a single AI. Custom experts and Eve-agent council members come later.

See `AI_COUNCIL.md`.

---

# Purpose

This document defines the development roadmap for building the Decision Intelligence Engine.

The goal is to build the system progressively.

Each phase must create a usable product before adding complexity.

The project should avoid building the complete autonomous engineering system before validating the core intelligence.

---

# Development Strategy

The system evolves through these stages:

```
Dynamic Council Assembly Engine

↓

Decision Intelligence Engine

↓

Project Intelligence

↓

Custom Experts + Eve Agents

↓

Planning Automation

↓

Engineering Automation

↓

Autonomous Software Organization
```

---

# Phase 0 — Foundation

## Goal

Create the technical foundation.

The system can run basic AI workflows.

---

## Features

### Project Setup

- Monorepo
- TypeScript configuration
- Package structure
- Development environment
- Database setup

### AI Provider Layer

Support:

- OpenAI
- Anthropic
- Google

Create abstraction:

```
AIProvider

generate()

stream()

embed()

```

---

### Database

Create initial schema:

Projects

Decisions

Experts

Workflows

Artifacts

---

## Deliverables

```
Repository created

Database running

AI calls working

Basic architecture ready
```

---

# Phase 1 — Autonomous Council Builder MVP

## Goal

Create the first working Dynamic Council Assembly Engine.

The user can ask a question and receive a multi-expert decision from an **automatically assembled** council.

Users cannot customize councils yet. The engine decides.

---

# Features

## Expert Registry (Knowledge Base)

Create domain-organized experts:

```
experts/engineering
experts/business
experts/legal
experts/general
```

Seed domain experts plus permanent quality-control agents:

- Devil's Advocate (always)
- Risk Analyst (always)
- Critical Thinker (always)
- Ethics Reviewer (sensitive domains)

---

## Domain Classifier

Automatically determine:

- intent
- domain(s)
- impact
- candidate expertise

---

## Council Assembly Engine

Input:

```
Question

Intent

Domain

Impact
```

Process:

```
Retrieve candidates

↓

Rank experts

↓

Add mandatory experts

↓

Create temporary council
```

Output:

```
Selected experts
```

---

## Expert Execution

Run experts independently via shared `CouncilExpert` contract.

Output:

Structured JSON.

---

## Debate Engine

Multi-round debate with permanent experts applying challenge pressure.

---

## Consensus Engine + Memory

Generate final decision, store reasoning.

---

## Deliverable

Example:

User:

```
Should I use PostgreSQL or MongoDB?
```

Engine assembles:

```
CTO, Backend Architect, Database Engineer,
Performance Engineer, Security Engineer,
Devil's Advocate, Risk Analyst
```

Output:

```
Decision: PostgreSQL

Confidence: 89%

...
```

MVP success metric: automatically generated councils outperform single-AI answers.

---

# Phase 2 — Advanced Decision Engine

## Goal

Make decisions significantly better and prepare for extensibility.

---

# Features

## Stronger Classification

Automatically determine:

- category
- multi-domain detection
- impact
- required experts
- ethics reviewer necessity

---

## Dynamic Council Hardening

Do not always use all experts.

Example:

Database question:

```
Database Engineer

Backend Engineer

Security

CTO

Devil's Advocate

Risk Analyst
```

Landing page:

```
Product Manager

UX Designer

UI Designer

Copywriter

Growth Marketer

Critical Thinker

Devil's Advocate
```

---

## Debate System

Add:

Round 1:

Independent opinions

Round 2:

Criticism

Round 3:

Revision

---

## Weighted Consensus

Implement:

- expert weights
- confidence scoring
- evidence evaluation

---

## Decision Memory

Store:

- accepted decisions
- rejected alternatives
- reasoning

---

## Deliverable

The council behaves like a temporary expert organization generated per request.

---

# Phase 2.5 — Custom Experts + Eve Agents (Post-MVP)

Only after MVP validates autonomous assembly.

## Goal

Extend the same `CouncilExpert` interface beyond built-ins.

Do not start here.

---

# Features

## Personal / Custom Experts

Users can create:

```
Name: My CTO
Base: Senior SaaS CTO
Knowledge: Company architecture
Memory: Previous decisions
```

## Eve-Agent Council Members

```
My Agent → Eve Runtime → Council Expert Interface
```

Companies can invite:

- Internal Security Agent
- Internal Finance Agent
- Company Historian Agent

## Private Councils

Company knowledge and private expert sets.

Still optional. Assembly remains the default.

---

# Phase 3 — Project Intelligence

## Goal

Give the council persistent project knowledge.

---

# Features

Generate:

```
PROJECT.md

ARCHITECTURE.md

STACK.md

DESIGN.md

DECISIONS.md
```

---

## Context Retrieval

Before decisions:

Retrieve:

- previous decisions
- documents
- code structure

---

## Decision Graph

Connect decisions.

Example:

```
Framework

↓

State Management

↓

Component Architecture
```

---

## Deliverable

The AI remembers why things were chosen.

---

# Phase 4 — AI Project Architect MVP

## Goal

Turn an idea into a planned software project.

---

# Features

User:

```
Build an AI competitor monitoring SaaS
```

System generates:

---

## Product

```
Target users

Problem

MVP scope

Features

Monetization
```

---

## Technical Architecture

```
Frontend

Backend

Database

Infrastructure

AI systems
```

---

## Design System

Generate:

```
DESIGN.md
```

Containing:

- colors
- typography
- spacing
- components
- interactions

---

## Roadmap

Generate:

```
MVP

Beta

Growth
```

---

# Deliverable

Complete project blueprint.

---

# Phase 5 — GitHub Automation

## Goal

Create projects automatically.

---

# Features

Create:

Repository

README

Documentation

Milestones

Labels

Kanban

Issues

---

## Issue Generation

AI creates:

```
Title

Description

Acceptance criteria

Dependencies

Priority
```

---

## Deliverable

A ready-to-build GitHub project.

---

# Phase 6 — Eve Integration

## Goal

Introduce durable autonomous workflows.

---

# Features

Convert workflows into Eve agents.

Examples:

```
Create Project Agent

Architecture Agent

Planning Agent

Documentation Agent

GitHub Agent
```

---

## Add

- persistent execution
- retries
- approvals
- tool usage

---

## Deliverable

Long-running autonomous workflows.

---

# Phase 7 — Coding Agent Integration

## Goal

The system starts implementing code.

---

# Features

Issue → Implementation

Process:

```
Issue

↓

Council Review

↓

Implementation Plan

↓

Code Generation

↓

Tests

↓

PR

↓

Review
```

---

## Agents

Add:

Frontend Developer

Backend Developer

Testing Engineer

Code Reviewer

Security Reviewer

---

## Deliverable

AI can complete development tasks.

---

# Phase 8 — Autonomous Engineering Team

## Goal

Create a complete AI software organization.

---

# Features

AI can:

Understand product

Plan features

Make architecture decisions

Write code

Review code

Maintain documentation

Find technical debt

Improve systems

---

# Departments

```
Product

Architecture

Engineering

Design

Security

QA

DevOps

Growth
```

---

# Phase 9 — Organizational Intelligence

## Goal

Create company-level memory.

---

# Features

Multiple projects.

Shared knowledge.

Engineering standards.

Reusable decisions.

Organization playbooks.

---

# Long-Term Vision

The final system:

```
Founder Idea

↓

AI Product Team

↓

AI Engineering Team

↓

AI Design Team

↓

AI Operations Team

↓

Production Software
```

---

# MVP Definition

The first valuable version is NOT the autonomous coder.

The first valuable version is NOT user-customized councils.

The MVP is:

```
User asks any decision question

↓

Intent + Domain + Impact

↓

Autonomous Council Assembly

↓

Required Experts + Permanent Experts debate

↓

Consensus decision produced

↓

Decision saved
```

Prove:

> Can an automatically generated council outperform a single AI?

Everything else builds on this.

---

# Success Criteria

Phase 1 success:

- Engine assembles relevant councils without user customization
- Automatically generated consensus outperforms a single AI response
- Decisions are explainable
- Permanent quality-control agents participate on important decisions

Phase 5 success:

- A complete project can be generated automatically

Phase 8 success:

- AI can maintain production software with minimal human involvement

---

# Golden Rule

Build intelligence first.

Automation second.

Autonomy last.

A bad decision automated 100 times is still a bad system.

The quality of reasoning determines the quality of everything built on top.
