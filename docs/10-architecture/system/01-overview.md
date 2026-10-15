> Part of [System Architecture](README.md).

# Overview

The Decision Intelligence Engine is composed of independent layers.

Every layer has exactly one responsibility.

The system follows a strict pipeline.

```
User Request

↓

Decision Intelligence Engine

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification (impact)

↓

Council Assembly Engine

↓

Required Experts + Permanent Experts

↓

Expert Council

↓

Debate Engine

↓

Consensus Engine

↓

Decision + Memory

↓

Execution Planner

↓

Executor

↓

Artifacts

↓

Human Approval (if needed)

↓

Execution
```

No component should skip another component.

The system must never execute before architectural decisions are finalized.

MVP note: the engine assembles councils automatically. User-customized councils and Eve-agent experts are post-MVP.

---

# High Level Architecture

Simplified view. The canonical tree is in [Project Structure](../project-structure/01-purpose-and-repository.md#repository-structure), per [ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction).

```
apps/
    web/

packages/

    core/

    council/

    decision-engine/

    executor/

    memory/

    planner/

    github/

    prompts/

    shared/

    types/

agents/

docs/
```

Every package must remain independent.

Circular dependencies are forbidden.
