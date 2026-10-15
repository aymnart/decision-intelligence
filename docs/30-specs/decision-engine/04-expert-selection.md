> Part of [Decision Intelligence Engine Specification](README.md).

# Expert Selection Algorithm

The Council Assembly Engine uses:

```
Intent

+

Domain Detection

+

Decision Category

+

Impact Level

+

Required Expertise

+

Previous Decisions
```

Then:

```
Retrieve expert candidates from knowledge base

↓

Rank experts

↓

Add mandatory / permanent experts

↓

Create temporary council
```

Permanent experts (quality-control agents):

```
Medium and high impact (ADR-009):

Devil's Advocate

Risk Analyst

Critical Thinker

When sensitive:

Ethics / Safety Reviewer
```

---

Example:

Database decision:

Required:

```
Database Engineer

Backend Architect

Security Engineer

Performance Engineer

CTO
```

Mandatory:

```
Devil's Advocate

Risk Analyst

Critical Thinker
```

Not required:

```
UI Designer
```
