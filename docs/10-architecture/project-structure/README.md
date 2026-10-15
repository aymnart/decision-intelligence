# Project Structure Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**.

Experts are a knowledge base, not a fixed always-on roster.

See [AI Council](../../30-specs/ai-council/README.md).

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-purpose-and-repository.md](01-purpose-and-repository.md) | Purpose, Architecture Style, Repository Structure | 139 |
| [02-apps.md](02-apps.md) | Package Responsibilities, apps/cli, apps/web, apps/api | 74 |
| [03-packages-core-engine.md](03-packages-core-engine.md) | packages/core, packages/decision-engine, packages/council, packages/consensus, packages/memory | 144 |
| [04-packages-planning-execution.md](04-packages-planning-execution.md) | packages/planner, packages/executor, packages/workflows, packages/github, packages/eve | 140 |
| [05-packages-platform.md](05-packages-platform.md) | packages/prompts, packages/database, packages/ai, packages/observability, packages/security, packages/shared | 128 |
| [06-expert-structure.md](06-expert-structure.md) | Expert Structure, SYSTEM.md, KNOWLEDGE.md, TOOLS.md, CONFIG.ts | 112 |
| [07-database-models.md](07-database-models.md) | Database Models, Project, Decision, ExpertOpinion, Debate, Artifact, Workflow, Execution | 127 |
| [08-dependencies-testing-order.md](08-dependencies-testing-order.md) | Dependency Rules, Testing Strategy, Development Order, Golden Rule | 133 |
