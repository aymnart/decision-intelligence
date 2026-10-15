> Part of [AI Council System Specification](README.md).

# Purpose

The AI Council is the Dynamic Council Assembly subsystem of the Decision Intelligence Engine.

Its purpose is not to ship a static roster of personas.

Its purpose is to:

1. Analyze any objective
2. Detect domain and impact
3. Assemble the optimal temporary expert organization
4. Debate, challenge assumptions, and reach consensus
5. Return a decision with memory

The council does not generate random opinions.

It creates structured, expert-driven decisions through:

- specialist reasoning
- disagreement
- critique
- debate
- voting
- consensus building

The goal is not maximum agreement.

The goal is the highest-quality decision.

---

# Updated Product Vision

```
AI Agent

↓

Needs a decision

↓

Calls Decision Intelligence Engine

↓

Engine creates temporary expert organization

↓

Experts debate

↓

Decision returned
```

Any agent (or user) that needs a decision should call the Decision Intelligence Engine.

The engine creates a temporary expert organization for that request.

---

# Core Principle

A single AI agent has blind spots.

A dynamically assembled council reduces blind spots.

Each expert represents a different optimization target.

Example:

CTO optimizes:

```
Long-term architecture
```

Security Engineer optimizes:

```
Risk reduction
```

Product Manager optimizes:

```
User value
```

Performance Engineer optimizes:

```
Speed and scalability
```

Permanent quality-control agents (Devil's Advocate, Risk Analyst, Critical Thinker) optimize for challenge, consequence, and reasoning quality.

The final decision balances all perspectives.
