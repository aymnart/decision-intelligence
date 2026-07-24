# Decision Intelligence Engine

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

Update the AI Council concept from **"a fixed group of experts"** into a **Dynamic Council Assembly Engine**.

The core intelligence is not the experts. The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

The product becomes a general reasoning layer that other AI systems can plug into — stronger than the original coding-only idea.

---

# Vision

You are building the **Decision Intelligence Engine** — not another coding agent.

Repository / workspace: `decision-intelligence`

Naming:

- **Decision Intelligence Engine** — the product
- **Dynamic Council Assembly Engine** — how councils are created
- **AI Council** — the temporary expert organization assembled for a request

The goal: for any objective, automatically assemble the optimal temporary expert organization, challenge assumptions, debate tradeoffs, and return a high-quality decision.

The system is not limited to software engineering personas.

It can assemble councils across engineering, business, legal, product, design, finance, and other domains — plus permanent quality-control agents (Devil's Advocate, Risk Analyst, Critical Thinker, Ethics Reviewer when needed).

The system must think before it codes.

Every important decision must be challenged, debated, justified, voted on, and documented before implementation begins.

Coding is the final step—not the first.

The AI should behave like an elite organization generator: create the right room of experts for the problem, then decide.

---

# Core Philosophy

Planning > Coding

Architecture > Framework

Correctness > Speed

Maintainability > Cleverness

Long-term Thinking > Short-term Convenience

Documentation > Tribal Knowledge

Explicit Decisions > Hidden Decisions

Consensus > Individual Opinions

Dynamic Assembly > Fixed Rosters

Every important decision should have an explanation that survives for years.

The AI must never simply output code because the user asked.

It must first determine whether the requested work aligns with the project's architecture and previously accepted decisions.

---

# Mission

The system should eventually be capable of taking a startup idea and producing:

• Product definition
• Technical architecture
• Visual identity
• Design system
• Repository
• Project setup
• GitHub Project
• Milestones
• Roadmap
• MVP planning
• Issue generation
• Documentation
• Development
• Code reviews
• Refactoring
• Architecture evolution

while preserving complete decision history.

---

# Fundamental Principle

The Decision Intelligence Engine is the product.

The Dynamic Council Assembly Engine is its core mechanism.

Everything else uses the council.

Never embed architectural intelligence directly inside workflows.

Instead:

```
AI Agent / User Request

↓

Needs a decision

↓

Decision Intelligence Engine

↓

Intent + Domain + Impact

↓

Council Assembly Engine

↓

Required Experts + Permanent Experts

↓

Debate → Consensus → Memory

↓

Executor (when applicable)
```

Every future feature must consume the Decision Intelligence Engine.

MVP must not allow user-customized councils. The engine decides.

Custom experts and Eve-agent council members come later.

---

# Non Goals

This project is NOT:

- another Cursor clone

- another Claude Code clone

- another Copilot

- another chat interface

It is an Engineering Operating System.

---

# Design Principles

The system must always:

Think deeply.

Challenge assumptions.

Consider alternatives.

Evaluate tradeoffs.

Document reasoning.

Produce deterministic outputs whenever possible.

Explain why.

Never optimize for short prompts.

Optimize for engineering quality.

---

# Development Philosophy

Prefer boring technology.

Prefer mature libraries.

Avoid unnecessary abstractions.

Optimize for readability.

Optimize for maintainability.

Optimize for explicitness.

Avoid magic.

Avoid hidden state.

Avoid implicit behavior.

Every file should have one responsibility.

Every module should have a clear owner.

---

# Project Rules

Every important feature must be:

Testable

Typed

Documented

Observable

Composable

Reusable

Replaceable

No hardcoded business logic.

No duplicated prompts.

No duplicated expert definitions.

No duplicated workflows.

---

# Architecture Rules

Use clean architecture.

Domain driven design where appropriate.

Business logic must never depend on frameworks.

Frameworks should be replaceable.

The Decision Engine should be framework-agnostic.

The AI Council should be provider-agnostic.

The Executor should be replaceable.

Never couple reasoning to infrastructure.

---

# Coding Standards

Strict TypeScript.

No "any".

Functional where practical.

Dependency injection where appropriate.

Small modules.

Pure functions when possible.

Immutable data preferred.

Interfaces before implementations.

Prefer composition over inheritance.

---

# Error Philosophy

Every failure should:

Explain why.

Suggest recovery.

Be retryable.

Be observable.

Never silently fail.

---

# Decision Philosophy

Not every decision deserves a council.

The system must classify decisions.

Low Impact

↓

Single Expert

Medium Impact

↓

Small Council

High Impact

↓

Full Council

This dramatically reduces latency and cost.

---

# AI Council Philosophy

Experts are specialists drawn from a domain knowledge base.

Experts are assembled per request — not as a fixed always-on roster.

Experts are independent.

Experts disagree.

Experts challenge each other.

Experts can change opinions after debate.

Permanent quality-control agents are mandatory on important decisions:

- Devil's Advocate
- Risk Analyst
- Critical Thinker
- Ethics/Safety Reviewer (sensitive domains)

Consensus is earned.

Consensus is never assumed.

The MVP proves:

> Can an automatically generated council outperform a single AI?

---

# Debate Philosophy

Every debate has stages.

1.

Independent reasoning

1.

Peer review

1.

Challenges

1.

Opinion revisions

1.

Voting

1.

Consensus

The first answer is never the final answer.

---

# Devil's Advocate and Permanent Experts

Devil's Advocate is always present on important decisions.

Its only purpose:

Challenge assumptions.

Find weaknesses.

Propose overlooked alternatives.

Prevent groupthink.

Also always include:

Risk Analyst — risks, consequences, hidden costs

Critical Thinker — logic, evidence, reasoning quality

Ethics/Safety Reviewer — present for sensitive domains

These are quality-control agents, not domain experts.

The Devil is never removed from High Impact decisions.

---

# Decision Quality

Every important decision must include:

Reasoning

Pros

Cons

Tradeoffs

Alternatives

Confidence

Risks

Unknowns

Final Vote

Consensus Percentage

Minority Report

Rejected Alternatives

Future Risks

Migration Strategy

Nothing should be accepted without justification.

---

# Decision Memory

Every accepted decision becomes permanent project knowledge.

Future decisions must reference previous ones.

The system should never forget:

Why React was chosen.

Why PostgreSQL was selected.

Why Railway was rejected.

Why Better Auth was accepted.

Architecture should evolve.

Not reset.

---

# Documentation Philosophy

Every project should eventually contain:

PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

ROADMAP.md

DECISIONS.md

CONTRIBUTING.md

WORKFLOWS.md

PROMPTS.md

Every generated file should become permanent context.

---

# Human Approval

The AI should never automatically:

Create repositories

Delete repositories

Push commits

Merge pull requests

Delete files

Run dangerous commands

Spend money

Purchase services

These require approval.

---

# GitHub Philosophy

GitHub is not storage.

GitHub is project management.

Every issue should have:

Purpose

Context

Acceptance Criteria

Dependencies

Priority

Labels

Milestone

Estimated Complexity

Definition of Done

---

# Design Philosophy

Never generate random UI.

Always define:

Brand

Typography

Spacing

Radius

Animation

Accessibility

Color System

Layout

Component Rules

Interaction Rules

Empty States

Loading States

Error States

Everything belongs in DESIGN.md.

---

# Tech Stack Philosophy

Frameworks should be selected through council decisions.

Never because they are trendy.

Every stack recommendation must justify:

Scalability

Developer Experience

Maintenance

Performance

Security

Hiring

Community

Migration Cost

---

# Observability

Everything should be observable.

Logs

Metrics

Tracing

Decision History

Execution Time

Expert Votes

Consensus Changes

Failures

Retries

Nothing should be hidden.

---

# Security

Security is never optional.

Every feature should consider:

Authentication

Authorization

Secrets

Input Validation

Rate Limiting

Logging

Abuse Prevention

OWASP

Least Privilege

Secure Defaults

---

# Performance

Prefer:

Streaming

Parallel execution

Caching

Incremental updates

Lazy evaluation

Avoid unnecessary LLM calls.

---

# LLM Cost Optimization

Never use the full council unnecessarily.

Use a Decision Classifier.

Low Impact

↓

One Expert

Medium

↓

3–5 Experts

High

↓

Entire Council

Only expensive decisions deserve expensive reasoning.

---

# Framework

Use Vercel Eve as the execution runtime.

Use Eve's:

Subagents

Tools

Skills

Durable execution

Human approvals

Long-running workflows

However:

The Decision Engine MUST remain framework independent.

If Eve disappears tomorrow, only the runtime should change.

The council must survive.

---

# Success Criteria

The project succeeds if it becomes a general decision intelligence layer: any agent or user can submit an objective, the engine assembles the optimal temporary expert organization, and the resulting decision is better than a single AI response — explainable, challengeable, and remembered.

Every future feature must strengthen this vision.

Never compromise the architecture for short-term convenience.

Do not build custom councils before validating autonomous assembly.
