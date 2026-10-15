> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# MVP Technical Stack

The stack should prioritize speed and maintainability.

The MVP is now a headless engine with a CLI ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)). The Frontend, Backend, and Authentication sections below apply to the web app in roadmap Phase 2, where the backend is Hono in `apps/api` rather than Next.js API routes ([Backend and Frontend](../../10-architecture/tech-stack/03-backend-and-frontend.md)). Database, AI layer, and models apply to the MVP as written.

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

cli
```

Do not build:

- GitHub automation
- Eve workflows
- autonomous coding

yet.
