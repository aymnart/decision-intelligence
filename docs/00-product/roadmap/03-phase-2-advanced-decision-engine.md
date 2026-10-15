> Part of [Decision Intelligence Engine Implementation Roadmap](README.md).

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

Critical Thinker
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

Risk Analyst
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

## Web App and API

Moved here from the MVP by [ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli), once the CLI MVP has shown the council beats a single AI.

- `apps/api` and `apps/web` on the same engine packages
- Accounts with Better Auth, owner-scoped decisions
- Durable runs on Inngest, progress display, per-user limits
- The [MVP interface](../../40-planning/mvp-plan/06-interface.md) views: decision page, expert views, debate view, final report
- Trust and Repeat usage measured with real users

Design: [System Design — After the MVP](../../10-architecture/system-design.md#after-the-mvp-web-app-and-api).

---

## Deliverable

The council behaves like a temporary expert organization generated per request.
