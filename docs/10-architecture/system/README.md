# System Architecture

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

The product is the **Decision Intelligence Engine** (`decision-intelligence`).

AI Council is not a fixed group of experts.

It is a **Dynamic Council Assembly Engine** inside this product.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

See [AI Council](../../30-specs/ai-council/README.md) for the full product vision, permanent experts, expert interface, and MVP constraints.

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-overview.md](01-overview.md) | Overview, High Level Architecture | 120 |
| [02-components-intent-classifier-assembly.md](02-components-intent-classifier-assembly.md) | Core Components 1–3: Intent Detection, Decision Classifier, Council Assembly Engine | 200 |
| [03-components-experts-debate-consensus-memory.md](03-components-experts-debate-consensus-memory.md) | Core Components 4–7: Expert Runner, Debate Engine, Consensus Engine, Decision Memory | 168 |
| [04-components-planner-executor-artifacts.md](04-components-planner-executor-artifacts.md) | Core Components 8–10: Execution Planner, Executor, Artifact Generator | 95 |
| [05-pipeline-and-communication.md](05-pipeline-and-communication.md) | Execution Pipeline, Component Communication, Event Driven Architecture, Parallelism | 167 |
| [06-approval-fault-tolerance-logging.md](06-approval-fault-tolerance-logging.md) | Human Approval, Fault Tolerance, Logging | 77 |
| [07-extensibility-and-scaling.md](07-extensibility-and-scaling.md) | Extensibility, Framework Independence, Source of Truth, Scalability Roadmap, Golden Rule | 149 |
