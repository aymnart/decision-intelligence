> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# MVP Success Metrics

Numeric targets and the measurement method are in [ADR-012](../../90-records/decisions/02-mvp-design.md#adr-012-measurable-mvp-success-targets).

The MVP succeeds if:

---

## Quality

Blind raters prefer council answers over single AI answers.

---

Trust and Repeat Usage left the MVP with the web app ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)). They are measured with real users in roadmap Phase 2.

---

## Technical

System can:

- run multiple experts
- debate
- reach consensus
- store decisions

---

# What NOT to build

Do not build:

❌ User-customized councils

❌ Custom / personal experts

❌ Eve agents as council members

❌ Company private councils

❌ GitHub automation

❌ Code generation

❌ Repository creation

❌ Project planning

❌ Design generation

❌ Autonomous coding agents

❌ Complex memory systems

❌ Multi-agent workflows beyond council debate

---

# Reason

The biggest risk is not technical.

The biggest risk is:

"Does an automatically generated AI council actually outperform a single AI?"

Validate the core intelligence first.

---

# After MVP Validation

Only after users value autonomous council assembly, expansion follows the [roadmap](../../00-product/roadmap/README.md). This MVP is roadmap Phase 1. Custom experts, Eve-agent council members, and private councils arrive in [Phase 2.5](../../00-product/roadmap/04-phase-2.5-custom-experts.md).

---

# First Development Goal

Build this:

```
Question

↓

Intent + Domain + Impact

↓

Autonomous Council Assembly

↓

Required Experts + Permanent Experts

↓

Debate

↓

Consensus

↓

Decision Report + Memory
```

Everything else is an expansion of this foundation.
