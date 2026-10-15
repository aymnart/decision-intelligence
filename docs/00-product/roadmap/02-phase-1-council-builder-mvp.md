> Part of [Decision Intelligence Engine Implementation Roadmap](README.md).

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

- Devil's Advocate (medium and high impact)
- Risk Analyst (medium and high impact)
- Critical Thinker (medium and high impact)
- Ethics Reviewer (sensitive domains)

Composition per impact level is settled in [ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level).

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
Devil's Advocate, Risk Analyst, Critical Thinker
```

Output:

```
Decision: PostgreSQL

Confidence: 89%

...
```

MVP success metric: automatically generated councils outperform single-AI answers.
