# Decision Intelligence Engine Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

This document specifies the **Decision Intelligence Engine** product (`decision-intelligence`).

AI Council is not a fixed group of experts. It is a **Dynamic Council Assembly Engine** inside this product.

The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

MVP must prove an automatically generated council can outperform a single AI.

Do not build custom experts, Eve-agent council members, or user-customized councils first.

See [AI Council](../ai-council/README.md).

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-purpose-and-principle.md](01-purpose-and-principle.md) | Purpose, Core Principle | 84 |
| [02-lifecycle-object-categories.md](02-lifecycle-object-categories.md) | Decision Lifecycle, Decision Object, Decision Categories | 133 |
| [03-impact-classification.md](03-impact-classification.md) | Impact Classification, LOW IMPACT, MEDIUM IMPACT, HIGH IMPACT, Decision Classifier, Classification Factors | 161 |
| [04-expert-selection.md](04-expert-selection.md) | Expert Selection Algorithm | 99 |
| [05-context-and-execution.md](05-context-and-execution.md) | Context Retrieval, Context Filtering, Expert Execution | 101 |
| [06-debate-engine.md](06-debate-engine.md) | Debate Engine, Round 1, Round 2, Round 3, Opinion Revision | 78 |
| [07-consensus-engine.md](07-consensus-engine.md) | Consensus Engine, Expert Weight, Consensus Score, Consensus Output, Minority Report | 154 |
| [08-decision-memory.md](08-decision-memory.md) | Decision Memory, Stored Information, Decision Graph, Decision Updates, Decision Evaluation | 117 |
| [09-cost-failures-anti-patterns.md](09-cost-failures-anti-patterns.md) | Cost Optimization, Failure Handling, Anti-Patterns | 68 |
| [10-mvp-and-future.md](10-mvp-and-future.md) | MVP Implementation, Future Improvements, Golden Rule | 90 |
