> Part of [Decision Intelligence Engine Specification](README.md).

# Consensus Engine

The consensus engine calculates the final recommendation.

It considers:

- votes
- expert weight
- confidence
- evidence
- risks
- alternatives

---

# Expert Weight

Example:

```json
{
"CTO":1.5,

"Security Engineer":1.3,

"Developer":1.0,

"Designer":0.8
}
```

Weights depend on decision category.

---

Example:

Database decision:

```
Database Engineer:
1.5

Backend Architect:
1.5

Security:
1.2

Designer:
0.5
```

---

# Consensus Score

Formula:

```
Consensus Score =

Weighted Agreement

+

Confidence Average

+

Evidence Quality

-

Risk Penalty
```

---

# Consensus Output

Example:

```json
{
"decision":

"Use PostgreSQL",

"confidence":

0.92,

"agreement":

88,

"supportingExperts":

[
"CTO",
"Backend",
"Database"
],

"minorityOpinion":

"MongoDB provides faster iteration",

"tradeoffs":

[
"Requires schema discipline"
],

"risks":

[
"Migration complexity"
]
}
```

---

# Minority Report

Never hide disagreement.

If an expert disagrees:

Store:

```
Who disagreed

Why

When their argument could become correct
```

Example:

```
Minority:

Use MongoDB.

Valid if:

The product becomes schema-flexible.
```
