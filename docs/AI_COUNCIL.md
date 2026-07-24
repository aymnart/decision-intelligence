# AI Council System Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

Update the AI Council concept from **"a fixed group of experts"** into a **Dynamic Council Assembly Engine**.

The core intelligence is not the experts. The core intelligence is:

> Given any objective, automatically create the optimal council, run reasoning, challenge assumptions, and produce a decision.

The product is the **Decision Intelligence Engine**.

The AI Council is the temporary expert organization it assembles — an **AI organization generator** other systems can call into.

This direction is stronger than the original coding-only idea.

---

# Purpose

The AI Council is the Dynamic Council Assembly subsystem of the Decision Intelligence Engine.

Its purpose is not to ship a static roster of personas.

Its purpose is to:

1. Analyze any objective
2. Detect domain and impact
3. Assemble the optimal temporary expert organization
4. Debate, challenge assumptions, and reach consensus
5. Return a decision with memory

The council does not generate random opinions.

It creates structured, expert-driven decisions through:

- specialist reasoning
- disagreement
- critique
- debate
- voting
- consensus building

The goal is not maximum agreement.

The goal is the highest-quality decision.

---

# Updated Product Vision

```
AI Agent

↓

Needs a decision

↓

Calls Decision Intelligence Engine

↓

Engine creates temporary expert organization

↓

Experts debate

↓

Decision returned
```

Any agent (or user) that needs a decision should call the Decision Intelligence Engine.

The engine creates a temporary expert organization for that request.

---

# Core Principle

A single AI agent has blind spots.

A dynamically assembled council reduces blind spots.

Each expert represents a different optimization target.

Example:

CTO optimizes:

```
Long-term architecture
```

Security Engineer optimizes:

```
Risk reduction
```

Product Manager optimizes:

```
User value
```

Performance Engineer optimizes:

```
Speed and scalability
```

Permanent quality-control agents (Devil's Advocate, Risk Analyst, Critical Thinker) optimize for challenge, consequence, and reasoning quality.

The final decision balances all perspectives.

---

# New AI Council Architecture

```text
                    User Request

                         ↓

              Decision Intelligence Engine

                         ↓

                  Intent Analyzer

                         ↓

                  Domain Detection

                         ↓

              Council Assembly Engine

                         ↓

        ┌────────────────────────────────┐
        │                                │
        ▼                                ▼

 Required Experts                 Permanent Experts

 CTO                             Devil's Advocate

 Lawyer                          Critical Thinker

 Designer                        Risk Analyst

 Doctor                          Ethics Reviewer

 etc.

        │                                │

        └──────────────┬─────────────────┘

                       ↓

                Expert Council

                       ↓

                 Debate Engine

                       ↓

              Consensus Engine

                       ↓

              Decision + Memory
```

---

# MVP: Autonomous Council Builder

The MVP should **not allow users to customize councils yet**.

The engine decides.

Example:

User:

> "Should my startup switch from PostgreSQL to MongoDB?"

The engine detects:

```
Domain:
Software Architecture

Impact:
High

Required experts:

✓ CTO
✓ Backend Architect
✓ Database Engineer
✓ Performance Engineer
✓ Security Engineer

Mandatory:

✓ Devil's Advocate
✓ Risk Analyst
```

Then it runs.

## MVP Must Prove

> Can an automatically generated council outperform a single AI?

## MVP Build Order

1. Expert registry
2. Domain classifier
3. Council builder
4. Permanent experts
5. Debate engine
6. Consensus engine
7. Memory

## Explicitly Later (Not MVP)

- custom experts
- Eve agents as council members
- company knowledge
- private councils
- user-customized councils

---

# Expert Categories

Instead of hardcoding a flat expert list, `experts/` becomes a knowledge base.

Example:

```
experts/

engineering/

  backend-architect

  frontend-architect

  database-engineer


business/

  cfo

  startup-advisor

  marketer


legal/

  lawyer

  compliance-specialist


general/

  devil-advocate

  critical-thinker

  risk-analyst

  ethics-reviewer
```

Domain experts are selected by the assembly engine.

General experts provide quality control.

---

# Permanent Council Members

Some experts should always exist.

These are not domain experts.

They are **quality-control agents**.

---

## 1. Devil's Advocate

Always present.

Purpose:

Attack the decision.

Questions:

* What assumption is wrong?
* What could fail?
* What alternative was ignored?

---

## 2. Risk Analyst

Always present.

Purpose:

Find:

* risks
* consequences
* hidden costs

---

## 3. Critical Thinker

Always present.

Purpose:

Check:

* logic
* evidence
* reasoning quality

---

## 4. Ethics/Safety Reviewer

Present for sensitive domains.

Purpose:

Prevent harmful recommendations.

---

# Future: User-Customized Councils

Later users can create personal and external experts.

---

## Personal Expert

Example:

```
Name:

My CTO


Base:

Senior SaaS CTO


Knowledge:

My company architecture


Memory:

Previous decisions
```

---

## Custom Eve Agent

A user can connect:

```
My Agent

↓

Eve Runtime

↓

Council Expert Interface
```

Example:

A company has:

```
Internal Security Agent

Internal Finance Agent

Company Historian Agent
```

The council can invite them.

Do **not** build this in MVP.

---

# Expert Interface

Everything should follow the same contract.

```ts
interface CouncilExpert {

  id: string;

  name: string;

  domain: string[];

  type:
    | "built-in"
    | "custom"
    | "eve-agent";

  instructions: string;

  capabilities: Capability[];

  weight: number;

  alwaysIncluded?: boolean;

  analyze(context): ExpertOpinion;

}
```

Built-in experts ship with the product.

Custom and Eve-agent types are post-MVP extensions of the same interface.

---

# Expert Output Contract

Experts must never return unstructured text.

Every response must follow:

```typescript
interface ExpertOpinion {

  expertId: string;

  recommendation: string;

  reasoning: string;

  assumptions: string[];

  advantages: string[];

  disadvantages: string[];

  alternatives: Alternative[];

  risks: Risk[];

  confidence: number;

  vote: Vote;

}
```

---

# Council Assembly Algorithm

The engine does:

```
Input:

User request

↓

Analyze intent

↓

Determine domain

↓

Determine impact

↓

Retrieve expert candidates

↓

Rank experts

↓

Add mandatory experts

↓

Create council

↓

Run debate

↓

Consensus
```

---

# Expert Selection Examples

## Question

"Should I launch a crypto payment product?"

Engine:

Domain:

```
Business + Finance + Legal + Technology
```

Council:

```
Startup Advisor

CFO

Crypto Expert

Legal Expert

CTO

Market Researcher


Mandatory:

Devil's Advocate

Risk Analyst
```

---

## Question

"Design a landing page"

Council:

```
Product Manager

UX Designer

UI Designer

Copywriter

Growth Marketer


Mandatory:

Critical Thinker

Devil's Advocate
```

---

## Question

"Choose database"

Council:

```
CTO

Backend Architect

Database Engineer

Security Engineer

Performance Engineer


Mandatory:

Devil's Advocate

Risk Analyst
```

---

# Decision Impact Levels

## Low

No debate.

One domain expert + optional permanent check.

Examples:

- naming variables
- formatting
- small refactors

---

## Medium

Small council.

3–5 domain experts + mandatory quality-control agents.

Examples:

- API design
- component architecture
- testing strategy

---

## High

Full relevant council.

Domain experts + all applicable permanent experts.

Examples:

- framework choice
- database choice
- authentication
- infrastructure
- business strategy
- regulated / sensitive domains (include Ethics Reviewer)

---

# Built-in Domain Expert Library (Seed Knowledge Base)

The system ships with predefined domain experts as registry entries — not as a fixed always-on council.

Seed examples (non-exhaustive):

1. Chief Technology Officer (CTO)
2. Staff Software Engineer
3. Backend Architect
4. Frontend Architect
5. Database Engineer
6. DevOps Engineer
7. Security Engineer
8. Performance Engineer
9. UX Designer
10. UI Designer
11. Product Manager
12. Startup Advisor
13. QA Engineer
14. AI Engineer
15. CFO / Finance Expert
16. Lawyer / Compliance Specialist
17. Marketer / Growth Marketer
18. Copywriter

Each expert remains a structured entity with domain tags, instructions, weight, and capabilities.

---

# Domain Expert Responsibilities (Seed)

## CTO

Own overall technical strategy.

Optimizes for: scalability, maintainability, technical direction, business alignment.

## Staff Software Engineer

Deep engineering quality.

Optimizes for: simplicity, correctness, maintainability.

## Backend Architect

Backend systems.

Optimizes for: APIs, databases, services, reliability.

## Frontend Architect

Frontend architecture.

Optimizes for: component design, state management, performance.

## Database Engineer

Data architecture.

Optimizes for: correctness, performance, query efficiency.

## DevOps Engineer

Infrastructure.

Optimizes for: deployment, reliability, automation.

## Security Engineer

Security.

Optimizes for: risk reduction, privacy, attack prevention.

## Performance Engineer

Speed and efficiency.

Optimizes for: latency, resource usage, scalability.

## UX Designer

User experience.

Optimizes for: usability, user flow, clarity.

## UI Designer

Visual design.

Optimizes for: consistency, aesthetics, design systems.

## Product Manager

Product decisions.

Optimizes for: user value, business impact, priorities.

## Startup Advisor

Business thinking.

Optimizes for: market success, speed, differentiation.

## QA Engineer

Quality assurance.

Optimizes for: reliability, testing, edge cases.

## AI Engineer

AI architecture.

Optimizes for: model quality, cost, reliability.

---

# Debate System

The debate has multiple phases.

---

# Phase 1: Independent Opinions

Experts do not see other responses.

Purpose:

Avoid group bias.

---

# Phase 2: Opinion Sharing

Experts receive:

- other recommendations
- reasoning
- concerns

---

# Phase 3: Challenge Round

Experts answer:

```
What do you disagree with?

What risk was ignored?

What assumption is wrong?

Would you change your vote?
```

Permanent experts lead challenge pressure:

- Devil's Advocate attacks assumptions
- Risk Analyst surfaces consequences
- Critical Thinker audits logic and evidence
- Ethics Reviewer (when present) blocks harmful paths

---

# Phase 4: Revision

Experts can update:

- recommendation
- confidence
- vote

Changing opinion is encouraged.

---

# Phase 5: Final Voting

Each expert submits:

```
Decision

Confidence

Vote
```

---

# Voting System

Votes are weighted.

Example:

```
CTO

weight: 1.5


Security

weight: 1.2


UX

weight: 1.0
```

Weights depend on domain relevance to the request.

The system does not simply count votes.

---

# Consensus Output

Example:

```json
{
  "decision": "Use PostgreSQL",
  "confidence": 0.91,
  "agreement": 86,
  "votes": {
    "for": 10,
    "against": 2
  },
  "minorityReport": [
    "MongoDB provides faster iteration"
  ],
  "tradeoffs": [
    "Higher schema discipline"
  ],
  "risks": [
    "Migration complexity"
  ]
}
```

---

# Expert Memory

Experts should improve over time.

Store:

- previous decisions
- accepted recommendations
- rejected recommendations
- project context

Before answering:

Experts receive relevant history.

---

# Council Failure Handling

If experts strongly disagree:

Example:

```
Agreement < 60%
```

The system must:

1. Explain disagreement

2. Identify missing information

3. Request user clarification

or

1. Run another debate round

---

# Anti-Patterns

Never:

- treat the council as a fixed always-on roster
- let users customize councils before MVP validation
- create fake consensus
- hide disagreement
- average opinions blindly
- let one expert dominate
- skip mandatory quality-control agents on important decisions
- use identical prompts for all experts
- hardcode domain experts outside the registry/knowledge base

---

# Success Metric

The council succeeds when:

1. An automatically assembled council outperforms a single AI on decision quality.
2. A senior practitioner reading the final decision says:

"I would have made a similar decision after reviewing the tradeoffs."

The goal is not AI confidence.

The goal is decision quality — across engineering, business, legal, product, and other domains.
