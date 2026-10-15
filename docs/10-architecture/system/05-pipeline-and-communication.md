> Part of [System Architecture](README.md).

# Execution Pipeline

```
User Request

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification (impact)

↓

Relevant Context Retrieval

↓

Retrieve + Rank Expert Candidates

↓

Add Mandatory Experts

↓

Create Temporary Council

↓

Independent Expert Opinions

↓

Debate

↓

Voting

↓

Consensus

↓

Store Decision

↓

Execution Planning

↓

Approval

↓

Execution

↓

Artifacts

↓

Project Memory Updated
```

---

# Component Communication

Every component communicates using strongly typed objects.

Never strings.

Never free-form prompts.

Example

```
Intent

↓

DecisionRequest

↓

ExpertOpinion

↓

DebateRound

↓

ConsensusDecision

↓

ExecutionPlan

↓

ExecutionResult
```

---

# Event Driven Architecture

Every important event should emit an event.

Examples

DecisionStarted

ExpertCompleted

DebateStarted

ConsensusReached

ExecutionStarted

ArtifactGenerated

ExecutionFinished

ApprovalRequested

ApprovalGranted

These events power observability.

---

# Parallelism

Experts should execute in parallel.

Debate occurs after all opinions complete.

Executors should execute in parallel where safe.

Example

Generate documentation

+

Generate roadmap

+

Generate design system

can happen simultaneously.
