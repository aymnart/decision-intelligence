> Part of [AI Council System Specification](README.md).

# Council Assembly Algorithm

The engine does:

```
Input:

User request

↓

Analyze intent

↓

Determine domain

↓

Determine impact

↓

Retrieve expert candidates

↓

Rank experts

↓

Add mandatory experts

↓

Create council

↓

Run debate

↓

Consensus
```

---

# Expert Selection Examples

## Question

"Should I launch a crypto payment product?"

Engine:

Domain:

```
Business + Finance + Legal + Technology
```

Council:

```
Startup Advisor

CFO

Crypto Expert

Legal Expert

CTO

Market Researcher


Mandatory:

Devil's Advocate

Risk Analyst

Critical Thinker
```

---

## Question

"Design a landing page"

Council:

```
Product Manager

UX Designer

UI Designer

Copywriter

Growth Marketer


Mandatory:

Critical Thinker

Devil's Advocate

Risk Analyst
```

---

## Question

"Choose database"

Council:

```
CTO

Backend Architect

Database Engineer

Security Engineer

Performance Engineer


Mandatory:

Devil's Advocate

Risk Analyst

Critical Thinker
```

---

# Decision Impact Levels

Settled in [ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level).

## Low

No debate.

One domain expert + optional permanent check.

Examples:

- naming variables
- formatting
- small refactors

---

## Medium

Small council.

3–5 domain experts + Devil's Advocate, Risk Analyst, Critical Thinker.

Examples:

- API design
- component architecture
- testing strategy

---

## High

Full relevant council.

Domain experts + all applicable permanent experts.

Examples:

- framework choice
- database choice
- authentication
- infrastructure
- business strategy
- regulated / sensitive domains (include Ethics Reviewer)
