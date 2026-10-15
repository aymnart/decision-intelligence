# Eve Implementation Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

AI Council is a **Dynamic Council Assembly Engine**, not a fixed group of experts.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

Eve is an execution runtime — and later, a way to plug company agents into the shared `CouncilExpert` interface.

MVP does **not** build Eve-agent council members first.

See [AI Council](../ai-council/README.md).

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-purpose-and-architecture.md](01-purpose-and-architecture.md) | Purpose, Official Eve Resources, Core Architecture, Important Rule | 166 |
| [02-project-structure.md](02-project-structure.md) | Project Structure | 85 |
| [03-agent-design.md](03-agent-design.md) | Eve Agent Design, Expert Instructions | 100 |
| [04-skills-and-tools.md](04-skills-and-tools.md) | Eve Skills, Skill Structure, Eve Tools, GitHub Tool, Filesystem Tool, Terminal Tool | 131 |
| [05-approval-and-workflows.md](05-approval-and-workflows.md) | Human Approval System, Durable Workflows, Workflow State, Council Workflow, Parallel Execution | 154 |
| [06-models-context-memory.md](06-models-context-memory.md) | Model Selection, Context Management, Memory Integration | 83 |
| [07-observability-errors-security.md](07-observability-errors-security.md) | Observability, Error Handling, Security | 60 |
| [08-mvp-and-future.md](08-mvp-and-future.md) | MVP Eve Implementation, Future Eve Expansion, Golden Rule | 103 |
