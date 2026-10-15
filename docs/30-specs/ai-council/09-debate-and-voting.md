> Part of [AI Council System Specification](README.md).

# Debate System

The debate has multiple phases.

---

# Phase 1: Independent Opinions

Experts do not see other responses.

Purpose:

Avoid group bias.

---

# Phase 2: Opinion Sharing

Experts receive:

- other recommendations
- reasoning
- concerns

---

# Phase 3: Challenge Round

Experts answer:

```
What do you disagree with?

What risk was ignored?

What assumption is wrong?

Would you change your vote?
```

Permanent experts lead challenge pressure:

- Devil's Advocate attacks assumptions
- Risk Analyst surfaces consequences
- Critical Thinker audits logic and evidence
- Ethics Reviewer (when present) blocks harmful paths

---

# Phase 4: Revision

Experts can update:

- recommendation
- confidence
- vote

Changing opinion is encouraged.

---

# Phase 5: Final Voting

Each expert submits:

```
Decision

Confidence

Vote
```

---

# Voting System

Votes are weighted.

Example:

```
CTO

weight: 1.5


Security

weight: 1.2


UX

weight: 1.0
```

Weights depend on domain relevance to the request.

The system does not simply count votes.

---

# Consensus Output

Example:

```json
{
  "decision": "Use PostgreSQL",
  "confidence": 0.91,
  "agreement": 86,
  "votes": {
    "for": 10,
    "against": 2
  },
  "minorityReport": [
    "MongoDB provides faster iteration"
  ],
  "tradeoffs": [
    "Higher schema discipline"
  ],
  "risks": [
    "Migration complexity"
  ]
}
```
