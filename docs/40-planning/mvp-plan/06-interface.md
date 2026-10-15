> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# MVP Interface

The MVP's interface is the CLI ([Commands](../../10-architecture/system-design.md#commands)). The views below are for the web app, which follows in [roadmap Phase 2](../../00-product/roadmap/03-phase-2-advanced-decision-engine.md#web-app-and-api) ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)). The CLI's `show` command prints the same report sections.

The UI should contain:

---

# Home

Input:

```
What decision do you need help with?
```

---

# Decision Page

Display:

```
Question

Impact Level

Experts Participating

```

---

# Expert Views

Show:

```
CTO opinion

Security opinion

Backend opinion

```

---

# Debate View

Show:

```
Expert disagreements

Opinion changes

Arguments
```

---

# Final Report

Display:

```
Recommendation

Confidence

Agreement

Tradeoffs

Minority Opinion

Risks
```
