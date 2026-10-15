> Part of [AI Council System Specification](README.md).

# Expert Memory

Experts should improve over time.

Store:

- previous decisions
- accepted recommendations
- rejected recommendations
- project context

Before answering:

Experts receive relevant history.

---

# Council Failure Handling

If experts strongly disagree:

Example:

```
Agreement < 60%
```

The system must:

1. Explain disagreement

2. Identify missing information

3. Request user clarification

or

1. Run another debate round

---

# Anti-Patterns

Never:

- treat the council as a fixed always-on roster
- let users customize councils before MVP validation
- create fake consensus
- hide disagreement
- average opinions blindly
- let one expert dominate
- skip mandatory quality-control agents on important decisions
- use identical prompts for all experts
- hardcode domain experts outside the registry/knowledge base

---

# Success Metric

The council succeeds when:

1. An automatically assembled council outperforms a single AI on decision quality.
2. A senior practitioner reading the final decision says:

"I would have made a similar decision after reviewing the tradeoffs."

The goal is not AI confidence.

The goal is decision quality — across engineering, business, legal, product, and other domains.
