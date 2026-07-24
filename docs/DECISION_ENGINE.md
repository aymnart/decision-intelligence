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

See `AI_COUNCIL.md`.

---

# Purpose

The Decision Intelligence Engine is the brain of the system.

It controls:

- what decisions require reasoning
- which domains are involved
- which experts participate
- how much reasoning is needed
- how debates happen
- how consensus is reached
- how decisions are stored
- how future decisions use previous knowledge

The Decision Engine is responsible for decision quality.

It is not responsible for execution.

---

# Core Principle

Never directly execute user requests.

Every request must pass through:

```
User Request

↓

Intent Analyzer

↓

Domain Detection

↓

Decision Classification

↓

Context Retrieval

↓

Retrieve Expert Candidates

↓

Rank Experts

↓

Add Mandatory Experts

↓

Create Council

↓

Expert Reasoning

↓

Debate

↓

Consensus

↓

Decision Memory

↓

Execution Planning
```

---

# Decision Lifecycle

Every decision follows this lifecycle:

```
CREATED

↓

CLASSIFIED

↓

CONTEXT_LOADED

↓

COUNCIL_SELECTED

↓

EXPERT_ANALYSIS

↓

DEBATE

↓

VOTING

↓

CONSENSUS

↓

APPROVED

↓

STORED

↓

EXECUTED

↓

EVALUATED
```

---

# Decision Object

Every decision must have a structured representation.

```typescript
interface Decision {

id: string;

title: string;

description: string;

category: DecisionCategory;

impact: ImpactLevel;

status: DecisionStatus;

context: Context;

experts: ExpertOpinion[];

debate: DebateSession;

consensus: ConsensusResult;

createdAt: Date;

updatedAt: Date;

}
```

---

# Decision Categories

The system must classify decisions.

Available categories:

```typescript
enum DecisionCategory {

ARCHITECTURE,

TECH_STACK,

DATABASE,

SECURITY,

INFRASTRUCTURE,

PRODUCT,

UX,

UI,

BUSINESS,

MARKETING,

CODE,

REFACTORING,

TESTING,

AI,

OTHER

}
```

---

# Impact Classification

Not every decision deserves expensive reasoning.

---

# LOW IMPACT

Examples:

- Rename variable
- Fix typo
- Update documentation
- Formatting
- Simple refactor

Process:

```
One expert

No debate

Fast execution
```

---

# MEDIUM IMPACT

Examples:

- API design
- Component architecture
- Testing strategy
- Folder structure
- Library selection

Process:

```
3-5 experts

One debate round

Weighted voting
```

---

# HIGH IMPACT

Examples:

- Framework selection
- Database choice
- Authentication
- Infrastructure
- Product direction
- Major architecture

Process:

```
Full council

Multiple debate rounds

Devil's Advocate mandatory

Human approval recommended
```

---

# Decision Classifier

The classifier determines:

1. Category

2. Impact

3. Required experts

4. Required reasoning depth

---

Example:

Input:

```
Should we use PostgreSQL or MongoDB?
```

Output:

```json
{
"category":"DATABASE",

"impact":"HIGH",

"reasoningDepth":"DEEP",

"experts":[
"CTO",
"Database Engineer",
"Backend Architect",
"Security Engineer",
"Performance Engineer",
"Devil"
]
}
```

---

# Classification Factors

The classifier considers:

## Blast Radius

How many parts of the system are affected?

---

## Reversibility

Can we easily change this later?

---

## Cost

Does changing this require large effort?

---

## Security Impact

Could this introduce risk?

---

## Business Impact

Does this affect revenue/users?

---

# Expert Selection Algorithm

The Council Assembly Engine uses:

```
Intent

+

Domain Detection

+

Decision Category

+

Impact Level

+

Required Expertise

+

Previous Decisions
```

Then:

```
Retrieve expert candidates from knowledge base

↓

Rank experts

↓

Add mandatory / permanent experts

↓

Create temporary council
```

Permanent experts (quality-control agents):

```
Always:

Devil's Advocate

Risk Analyst

Critical Thinker

When sensitive:

Ethics / Safety Reviewer
```

---

Example:

Database decision:

Required:

```
Database Engineer

Backend Architect

Security Engineer

Performance Engineer

CTO
```

Mandatory:

```
Devil's Advocate

Risk Analyst
```

Not required:

```
UI Designer
```

---

# Context Retrieval

Before experts reason, retrieve relevant knowledge.

Sources:

```
PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

DECISIONS.md

Previous discussions

Existing code
```

---

# Context Filtering

Never send everything.

Retrieve only relevant information.

Example:

Authentication decision:

Include:

```
Current stack

Database

Existing auth decisions

Security requirements
```

Exclude:

```
Color palette

Marketing strategy
```

---

# Expert Execution

Experts execute independently.

Input:

```typescript
interface ExpertTask {

problem:string;

context:Context;

constraints:string[];

role:Expert;

}
```

Output:

```typescript
interface ExpertOpinion {

recommendation:string;

reasoning:string;

pros:string[];

cons:string[];

risks:string[];

alternatives:string[];

confidence:number;

vote:"approve"|"reject";

}
```

---

# Debate Engine

The debate engine creates productive disagreement.

---

# Round 1

Independent Analysis

Rules:

- No expert sees other opinions.
- Each expert creates their own recommendation.

Purpose:

Avoid herd mentality.

---

# Round 2

Peer Review

Experts receive:

```
Other recommendations

Arguments

Tradeoffs
```

They answer:

```
What do you disagree with?

What risk was ignored?

What alternative is stronger?

Would you change your vote?
```

---

# Round 3

Challenge Round

Mandatory for high-impact decisions.

Devil's Advocate attacks:

- assumptions
- weak arguments
- missing alternatives

---

# Opinion Revision

Experts may update:

```
Recommendation

Confidence

Vote
```

Changing opinion is considered positive.

---

# Consensus Engine

The consensus engine calculates the final recommendation.

It considers:

- votes
- expert weight
- confidence
- evidence
- risks
- alternatives

---

# Expert Weight

Example:

```json
{
"CTO":1.5,

"Security Engineer":1.3,

"Developer":1.0,

"Designer":0.8
}
```

Weights depend on decision category.

---

Example:

Database decision:

```
Database Engineer:
1.5

Backend Architect:
1.5

Security:
1.2

Designer:
0.5
```

---

# Consensus Score

Formula:

```
Consensus Score =

Weighted Agreement

+

Confidence Average

+

Evidence Quality

-

Risk Penalty
```

---

# Consensus Output

Example:

```json
{
"decision":

"Use PostgreSQL",

"confidence":

0.92,

"agreement":

88,

"supportingExperts":

[
"CTO",
"Backend",
"Database"
],

"minorityOpinion":

"MongoDB provides faster iteration",

"tradeoffs":

[
"Requires schema discipline"
],

"risks":

[
"Migration complexity"
]
}
```

---

# Minority Report

Never hide disagreement.

If an expert disagrees:

Store:

```
Who disagreed

Why

When their argument could become correct
```

Example:

```
Minority:

Use MongoDB.

Valid if:

The product becomes schema-flexible.
```

---

# Decision Memory

Every final decision becomes searchable knowledge.

---

# Stored Information

```
Decision

Reasoning

Alternatives

Votes

Confidence

Date

Dependencies

Outcome
```

---

# Decision Graph

Decisions are connected.

Example:

```
Framework

↓

Frontend Architecture

↓

State Management

↓

Component Strategy
```

Changing one decision reveals affected decisions.

---

# Decision Updates

When new information appears:

The system checks:

```
Does this invalidate previous decisions?
```

Example:

Previous:

```
Use Firebase
```

New requirement:

```
Enterprise compliance
```

System:

```
Firebase decision requires review.
```

---

# Decision Evaluation

After implementation:

The system compares:

Prediction

vs

Reality

Example:

Decision:

```
PostgreSQL chosen because scalability.
```

After 6 months:

```
Database performance good.

Decision confirmed.
```

This improves future decisions.

---

# Cost Optimization

The Decision Engine controls AI spending.

Rules:

Simple task:

```
Fast model
One expert
```

Complex architecture:

```
High reasoning model

Full council
```

---

# Failure Handling

If consensus is impossible:

Conditions:

```
Agreement < 60%

OR

High uncertainty

OR

Missing information
```

Actions:

1. Request clarification

OR

1. Gather more information

OR

1. Present multiple valid options

---

# Anti-Patterns

Never:

- use one model as every expert
- force agreement
- hide uncertainty
- skip tradeoffs
- make decisions without context
- store only the final answer
- ignore previous decisions

---

# MVP Implementation

First version must prove:

> Can an automatically generated council outperform a single AI?

MVP requires:

## Expert Registry

- domain-organized knowledge base
- built-in experts only
- shared `CouncilExpert` contract

## Domain Classifier

- domain detection
- multi-domain support

## Council Builder

- candidate retrieval
- ranking
- mandatory expert injection
- no user customization yet

## Permanent Experts

- Devil's Advocate
- Risk Analyst
- Critical Thinker
- Ethics Reviewer (sensitive domains)

## Debate Engine

- independent opinions
- critique
- revision

## Consensus Engine

- weighted voting
- minority reports

## Decision Storage / Memory

- save decisions and reasoning

Do not build first:

- custom experts
- Eve agents as council members
- company private councils
- user-assembled councils

---

# Future Improvements

V2:

- learned expert weights

- outcome-based scoring

- custom / personal experts

- Eve-agent council members

- organizational knowledge graph

V3:

- autonomous engineering leadership

- cross-project intelligence

- predictive architecture recommendations

- private company councils

---

# Golden Rule

The Decision Engine exists to answer:

"Given this objective, what temporary expert organization should we assemble, and given all available knowledge, constraints, risks, and expert perspectives, what is the best decision we can make right now?"
