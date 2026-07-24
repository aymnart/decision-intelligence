# STACK.md

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

The product is the **Decision Intelligence Engine** (`decision-intelligence`).

AI Council is a **Dynamic Council Assembly Engine**, not a fixed group of experts.

The stack supports a Decision Intelligence Engine that:

1. Analyzes intent
2. Detects domains
3. Assembles Required Experts + Permanent Experts
4. Runs debate and consensus
5. Stores decision memory

MVP does not require user-customized councils or Eve-agent experts.

See `AI_COUNCIL.md`.

---

# Purpose

This document is the single source of truth for the technology stack of the Decision Intelligence Engine.

Every architectural decision regarding technologies must originate here.

The stack is intentionally opinionated.

Consistency is preferred over endlessly evaluating technologies.

Any deviation from this stack requires:

1. AI Council approval (via Dynamic Council Assembly)
2. Architecture Decision Record (ADR)
3. Update to this document

---

# Philosophy

The stack optimizes for:

- Developer Experience
- Type Safety
- AI-native development
- Maintainability
- Scalability
- Vendor independence
- Production readiness

Priority:

```
Developer Experience

↓

Correctness

↓

Maintainability

↓

Performance

↓

Scalability

↓

Cost Optimization
```

---

# Architecture Overview

```
                        Users / AI Agents
                          │
                          ▼
                 Next.js Web Application
                          │
                          ▼
                     Hono API Server
                          │
                          ▼
           Decision Intelligence Engine
                          │
                          ▼
              Intent → Domain → Impact
                          │
                          ▼
              Council Assembly Engine
                          │
             ┌────────────┴────────────┐
             ▼                         ▼
      Required Experts          Permanent Experts
      (domain knowledge)        (quality control)
             │                         │
             └────────────┬────────────┘
                          ▼
                   Debate + Consensus
                          │
             ┌────────────┴────────────┐
             ▼                         ▼
      AI Provider Layer          Memory Layer
             │                         │
             ▼                         ▼
       OpenAI / Anthropic      PostgreSQL
             │
             ▼
      Background Jobs
          (Inngest)
```

---

# Monorepo

## Technology

Turborepo

Reason:

- Excellent TypeScript support
- Incremental builds
- Remote caching
- Package isolation
- Industry standard

Alternative Considered

Nx

Reason Rejected

- More complex
- Higher learning curve
- Unnecessary for MVP

---

# Runtime

## Technology

Node.js 24 LTS

Reason

- Mature ecosystem
- Excellent package compatibility
- Long-term support
- Stable

Alternative

Bun

Reason Rejected

Still evolving.

May become an optional runtime later.

---

# Language

TypeScript

Configuration

Strict Mode

Rules

- strict=true
- no implicit any
- exact optional property types
- no unchecked indexed access

Reason

The project relies heavily on structured AI outputs.

Maximum type safety is mandatory.

---

# Package Manager

pnpm

Reason

- Fastest installs
- Efficient storage
- Excellent workspace support
- Preferred by Turborepo

Alternatives

npm

Yarn

Rejected because pnpm provides better monorepo support.

---

# Backend

## Technology

Hono

Reason

- Extremely fast
- Tiny
- Type-safe
- Framework agnostic
- Works on:

Node

Bun

Cloudflare

Workers

Lambda

Future runtimes

Why not Express?

- Older architecture
- Weaker typing
- Slower

Why not NestJS?

- Too opinionated
- Too much boilerplate
- Heavy

---

# Frontend

Next.js

App Router

React 19

Reason

- Server Components
- Excellent ecosystem
- Vercel support
- Mature AI integrations

---

# UI Library

shadcn/ui

Reason

- Copy-paste components
- No vendor lock-in
- Accessible
- Highly customizable

Alternatives

Material UI

Ant Design

Rejected

Too opinionated.

---

# Styling

Tailwind CSS v4

Reason

- Utility first
- Fast
- Standard ecosystem

---

# Animations

Motion

Reason

Official successor to Framer Motion.

---

# Forms

React Hook Form

Validation

Zod

Reason

- Type-safe
- Fast
- Excellent DX

---

# API Validation

Zod

Used for:

- requests
- responses
- AI outputs
- environment variables

---

# AI SDK

Vercel AI SDK

Reason

Unified interface for:

- OpenAI
- Anthropic
- Gemini
- Grok
- DeepSeek
- Local models

Avoids provider lock-in.

---

# AI Orchestration

Vercel Eve

Role

Agent runtime only.

Important

The Decision Engine must never depend directly on Eve.

Architecture

```
Decision Engine

↓

Orchestration Layer

↓

Eve Adapter

↓

Vercel Eve
```

Future adapters

- LangGraph
- OpenAI Agents SDK
- Temporal
- Custom runtime

---

# AI Provider Layer

Create abstraction.

Never call providers directly.

```
AIProvider

↓

OpenAIProvider

ClaudeProvider

GeminiProvider

DeepSeekProvider

Future Providers
```

Every provider implements:

```
generate()

stream()

structuredOutput()

embeddings()
```

---

# AI Models

Reasoning

Use the strongest available reasoning model.

Tasks

- architecture
- security
- planning
- debate
- consensus

Fast Models

Use lightweight models for

- summaries
- classifications
- formatting

Embedding Models

Only introduced when semantic retrieval becomes necessary.

---

# Database

PostgreSQL

Reason

- ACID
- Mature
- Excellent tooling
- JSON support
- Full-text search

Alternatives

MongoDB

Rejected

The system is relational.

---

# ORM

Drizzle ORM

Reason

- SQL-first
- Type-safe
- Lightweight

Alternative

Prisma

Rejected

- More abstraction
- Less SQL control
- Larger client

---

# Authentication

Better Auth

Reason

- TypeScript native
- Modern
- Self-host friendly

---

# Background Jobs

Inngest

Responsibilities

- retries
- scheduling
- async jobs
- long-running workflows

Reason

Excellent TypeScript experience.

Simple integration.

---

# Caching

Redis

Technology

Upstash Redis

Uses

- sessions
- AI cache
- rate limiting
- temporary workflows

---

# Object Storage

Cloudflare R2

Uses

- generated files
- reports
- diagrams
- uploads

Reason

No egress fees.

---

# Search

MVP

PostgreSQL Full Text Search

Future

OpenSearch

Reason

Avoid unnecessary infrastructure.

---

# Vector Database

None

Reason

Do not introduce vector search until:

- enough historical decisions exist
- semantic retrieval is required

Future candidates

- pgvector
- Pinecone
- Weaviate

---

# Observability

OpenTelemetry

Purpose

Tracing

Metrics

Instrumentation

---

# Error Tracking

Sentry

Purpose

Exceptions

Performance

Replays

---

# Logging

Pino

Reason

Fastest structured logger.

---

# Analytics

PostHog

Purpose

Product analytics

Feature adoption

Funnels

---

# Documentation

Markdown

Mermaid

TypeDoc

Generated docs remain human-readable.

---

# Testing

Unit

Vitest

Integration

Vitest

API

MSW

E2E

Playwright

Reason

Modern TypeScript stack.

---

# Linting

Biome

Purpose

Formatting

Linting

Imports

Reason

Replace

- ESLint
- Prettier

Single tool.

Much faster.

---

# Git Hooks

Husky

Checks

- lint
- types
- tests

before commits.

---

# CI/CD

GitHub Actions

Pipeline

```
Install

↓

Type Check

↓

Lint

↓

Tests

↓

Build

↓

Deploy
```

---

# Deployment

Frontend

Vercel

Backend

Vercel Functions (MVP)

Future

Docker

Fly.io

Railway

Kubernetes

---

# Database Hosting

Neon

Reason

Serverless PostgreSQL

Branching

Excellent DX

---

# Secrets

Environment Variables

Future

Cloud Secret Manager

Vault

---

# File Generation

Libraries

PDF

ReportLab (Python services if needed)

Markdown

Native

DOCX

python-docx (if a Python worker is introduced)

---

# Repository Structure

```
apps/

web/

packages/

ai/

api/

core/

council/

consensus/

database/

decision-engine/

executor/

github/

memory/

observability/

orchestration/

planner/

prompts/

queue/

security/

shared/

tests/

docs/
```

---

# Dependency Rules

The architecture follows Clean Architecture.

Allowed

```
Frontend

↓

API

↓

Application

↓

Domain

↓

Infrastructure
```

Forbidden

Infrastructure

↓

Domain

Never.

---

# Dependency Injection

Services communicate through interfaces.

Never import implementations directly.

Example

```
DecisionEngine

↓

AIProvider Interface

↓

OpenAI Provider
```

---

# Version Policy

Always use

Latest stable versions.

Avoid beta releases in production.

Major upgrades require:

- testing
- ADR
- changelog

---

# Stack Governance

Adding a dependency requires answering:

1. What problem does it solve?

2. Can an existing dependency solve it?

3. Is it maintained?

4. Does it improve developer experience?

5. Does it introduce vendor lock-in?

If the answer is unclear,

Do not add it.

---

# Technology Decision Process

Every major technology choice follows:

```
Proposal

↓

AI Council Review

↓

Architecture Decision Record

↓

STACK.md Update

↓

Implementation
```

---

# Future Technologies

Potential future additions

- Temporal
- OpenSearch
- pgvector
- Kubernetes
- Bun runtime
- Rust services
- MCP integrations
- Multi-region deployment

These are intentionally excluded from the MVP.

---

# Golden Rules

1. Prefer simplicity over novelty.

2. Prefer type safety over convenience.

3. Prefer portability over vendor lock-in.

4. Keep the Decision Engine framework-independent.

5. Eve is an implementation detail, not the architecture.

6. AI providers must be interchangeable.

7. Do not introduce infrastructure before it is needed.

8. Every major stack change must be documented.

9. The stack serves the architecture—not the other way around.

10. Consistency beats perfection.