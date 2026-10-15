> Part of [System Architecture](README.md). Continues Core Components from [02](02-components-intent-classifier-assembly.md).

## 4

Expert Runner

Every expert runs independently.

Experts cannot initially see each other's responses.

Each receives

Task

Context

Relevant project decisions

Relevant documentation

Constraints

Each expert returns JSON.

Never plain text.

Example

```
Decision

Reasoning

Pros

Cons

Alternatives

Confidence

Vote
```

---

## 5

Debate Engine

The Debate Engine is the heart of the system.

Pipeline

Round 1

Independent reasoning

↓

Round 2

Experts receive summaries of every opinion.

↓

Experts critique each other.

↓

Experts may change opinion.

↓

Vote again.

↓

Consensus.

This prevents anchoring bias.

---

## 6

Consensus Engine

The Consensus Engine never simply counts votes.

It considers

Confidence

Expert priority

Agreement

Tradeoffs

Minority reports

Risk

Unknowns

Example

```
Winner

Next.js

Confidence

92%

Agreement

84%

Minority

TanStack Start

Reason

Performance advantages
did not outweigh ecosystem maturity.
```

---

## 7

Decision Memory

Every accepted decision becomes permanent project knowledge.

Example

```
Decision

Authentication

Winner

Better Auth

Reason

...

Tradeoffs

...

Date

...

Dependencies
```

Future discussions reference previous decisions.

Nothing is forgotten.
