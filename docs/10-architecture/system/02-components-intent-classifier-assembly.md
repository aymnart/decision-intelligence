> Part of [System Architecture](README.md).

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

One domain expert, optional permanent check.

---

### Medium Impact

Examples

Folder structure

API design

Database schema

Testing strategy

Uses:

Small council.

3–5 domain experts plus the permanent experts.

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

Entire relevant council plus the permanent experts.

This optimization dramatically reduces cost. Composition per level is settled in [ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level).

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

Risk Analyst
```

This saves tokens and improves reasoning quality.

Experts live in a domain knowledge base (`experts/engineering`, `experts/business`, `experts/legal`, `experts/general`, etc.), not as hardcoded one-off prompts.
