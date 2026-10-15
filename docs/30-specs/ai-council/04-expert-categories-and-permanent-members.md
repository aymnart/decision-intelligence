> Part of [AI Council System Specification](README.md).

# Expert Categories

Instead of hardcoding a flat expert list, `experts/` becomes a knowledge base.

Example:

```
experts/

engineering/

  backend-architect

  frontend-architect

  database-engineer


business/

  cfo

  startup-advisor

  marketer


legal/

  lawyer

  compliance-specialist


general/

  devil-advocate

  critical-thinker

  risk-analyst

  ethics-reviewer
```

Domain experts are selected by the assembly engine.

General experts provide quality control.

---

# Permanent Council Members

Some experts should always exist.

These are not domain experts.

They are **quality-control agents**.

They sit on every medium- and high-impact council. A low-impact decision may include one of them as a check ([ADR-009](../../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level)).

---

## 1. Devil's Advocate

Present on every medium- and high-impact council.

Purpose:

Attack the decision.

Questions:

* What assumption is wrong?
* What could fail?
* What alternative was ignored?

---

## 2. Risk Analyst

Present on every medium- and high-impact council.

Purpose:

Find:

* risks
* consequences
* hidden costs

---

## 3. Critical Thinker

Present on every medium- and high-impact council.

Purpose:

Check:

* logic
* evidence
* reasoning quality

---

## 4. Ethics/Safety Reviewer

Present for sensitive domains.

Purpose:

Prevent harmful recommendations.
