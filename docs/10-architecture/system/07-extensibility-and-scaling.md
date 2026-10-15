> Part of [System Architecture](README.md).

# Extensibility

Experts are plugins.

Executors are plugins.

Providers are plugins.

Memory systems are plugins.

Nothing should require changing the core architecture.

---

# Framework Independence

The architecture must not depend on Eve.

The architecture should support replacing Eve with another orchestration runtime.

The following are implementation details

Eve

OpenAI Agents SDK

LangGraph

Temporal

Mastra

etc.

The Decision Engine remains unchanged.

---

# Source of Truth

Only one source of truth exists for each concern.

Examples

Architecture

ARCHITECTURE.md

Design

DESIGN.md

Roadmap

ROADMAP.md

Technical decisions

DECISIONS.md

Never duplicate project knowledge.

---

# Scalability Roadmap

MVP

Single project

↓

V2

Multiple projects

↓

V3

Shared organizational knowledge

↓

V4

Cross-project reasoning

↓

V5

Multi-agent autonomous software company

The architecture should support all future stages without major redesign.

---

# Golden Rule

Every module should answer one question.

Intent Analyzer

"What does the user want?"

Domain Detection

"What domains does this touch?"

Decision Classifier

"How important is this decision?"

Council Assembly Engine

"Who should participate in this temporary organization?"

Expert Runner

"What does each expert think?"

Debate Engine

"Did anyone change their mind?"

Consensus Engine

"What should we do?"

Decision Memory

"Why did we decide this?"

Execution Planner

"How do we accomplish it?"

Executor

"Can we perform it?"

Artifact Generator

"What permanent knowledge should we create?"

If a module answers more than one question, split it.
