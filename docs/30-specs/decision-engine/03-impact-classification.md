> Part of [Decision Intelligence Engine Specification](README.md).

# Impact Classification

Not every decision deserves expensive reasoning.

Council composition per level is settled in [ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level).

---

# LOW IMPACT

Examples:

- Rename variable
- Fix typo
- Update documentation
- Formatting
- Simple refactor

Process:

```
One domain expert

Optional permanent check

No debate

Fast execution
```

---

# MEDIUM IMPACT

Examples:

- API design
- Component architecture
- Testing strategy
- Folder structure
- Library selection

Process:

```
3-5 domain experts

Devil's Advocate, Risk Analyst, Critical Thinker

One debate round

Weighted voting
```

---

# HIGH IMPACT

Examples:

- Framework selection
- Database choice
- Authentication
- Infrastructure
- Product direction
- Major architecture

Process:

```
Full council

Multiple debate rounds

Devil's Advocate, Risk Analyst, Critical Thinker mandatory

Human approval required (ADR-010)
```

---

# Decision Classifier

The classifier determines:

1. Category

2. Impact

3. Required experts

4. Required reasoning depth

---

Example:

Input:

```
Should we use PostgreSQL or MongoDB?
```

Output:

```json
{
"category":"DATABASE",

"impact":"HIGH",

"reasoningDepth":"DEEP",

"experts":[
"CTO",
"Database Engineer",
"Backend Architect",
"Security Engineer",
"Performance Engineer",
"Devil's Advocate",
"Risk Analyst",
"Critical Thinker"
]
}
```

---

# Classification Factors

The classifier considers:

## Blast Radius

How many parts of the system are affected?

---

## Reversibility

Can we easily change this later?

---

## Cost

Does changing this require large effort?

---

## Security Impact

Could this introduce risk?

---

## Business Impact

Does this affect revenue/users?
