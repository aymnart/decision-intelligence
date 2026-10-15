> Part of [Tech Stack](README.md).

# Repository Structure

The canonical tree and dependency direction are set in [ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction). The tree and diagram below are the original sketch: API lives in `apps/api`, and dependencies point inward toward the domain.

```
apps/

web/

packages/

ai/

api/

core/

council/

consensus/

database/

decision-engine/

executor/

github/

memory/

observability/

orchestration/

planner/

prompts/

queue/

security/

shared/

tests/

docs/
```

---

# Dependency Rules

The architecture follows Clean Architecture.

Allowed

```
Frontend

↓

API

↓

Application

↓

Domain

↓

Infrastructure
```

Forbidden

Infrastructure

↓

Domain

Never.

---

# Dependency Injection

Services communicate through interfaces.

Never import implementations directly.

Example

```
DecisionEngine

↓

AIProvider Interface

↓

OpenAI Provider
```
