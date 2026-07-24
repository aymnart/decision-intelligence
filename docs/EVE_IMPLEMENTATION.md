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

See `AI_COUNCIL.md`.

---

# Purpose

This document defines how to implement the AI Engineering Operating System using Vercel Eve.

Eve is used as the agent execution runtime.

The core intelligence must remain independent from Eve.

Eve provides:

- agent orchestration
- subagents
- tools
- skills
- durable workflows
- human approvals
- long-running execution
- state management

The Decision Intelligence Engine remains the core product.

---

# Official Eve Resources

Before implementation, study:

- Eve Documentation:
<https://eve.dev/llms.txt>

- Eve Subagents:
<https://vercel.com/kb/guide/how-to-use-eve-subagents>

- Eve Knowledge Base:
<https://vercel.com/kb/eve>

---

# Core Architecture

The relationship between Eve and the Dynamic Council Assembly Engine:

```
                 User Request

                      |

                      v

        Decision Intelligence Engine

                      |

                      v

              Intent Analyzer

                      |

                      v

              Domain Detection

                      |

                      v

           Council Assembly Engine

                      |

        +-------------+-------------+

        |                           |

        v                           v

 Required Experts            Permanent Experts

 (domain knowledge base)     (quality control)

        |                           |

        +-------------+-------------+

                      |

                      v

         Expert runners (Eve workers)

                      |

                      v

             Debate + Consensus

                      |

                      v

             Decision + Memory

                      |

                      v

             Execution Workflow

                      |

                      v

                  Artifacts
```

MVP: Eve may execute built-in expert roles as workers.

Post-MVP: users can connect custom Eve agents as `type: "eve-agent"` council members through the same `CouncilExpert` interface.

---

# Important Rule

Eve agents are NOT the council.

They are workers executing expert roles selected by the Council Assembly Engine.

The council logic belongs in the application layer.

Future custom Eve agents must still implement:

```
CouncilExpert {
  type: "eve-agent"
  analyze(context): ExpertOpinion
}
```

Example future connection:

```
My Agent

↓

Eve Runtime

↓

Council Expert Interface
```

Company examples:

```
Internal Security Agent

Internal Finance Agent

Company Historian Agent
```

Do not build custom Eve-agent council members before MVP validates autonomous assembly.

---

# Project Structure

Recommended structure:

```
ai-engineering-os/

├── apps/

│   └── web/

│

├── packages/

│

│   ├── council/

│   │
│   ├── decision-engine/

│   │
│   ├── consensus/

│   │
│   ├── memory/

│   │
│   ├── planner/

│   │
│   ├── executor/

│   │
│   ├── github/

│   │
│   ├── eve/

│   │
│   ├── prompts/

│   │
│   └── shared/

│

├── experts/

│   ├── engineering/

│   ├── business/

│   ├── legal/

│   └── general/

│       ├── devil-advocate/

│       ├── critical-thinker/

│       ├── risk-analyst/

│       └── ethics-reviewer/

│

├── agents/   # optional Eve runtime wrappers

│

├── workflows/

│
├── docs/

│
├── tests/

│
└── package.json
```

---

# Eve Agent Design

Each assembled expert may run as an Eve subagent worker.

Expert knowledge lives in the domain knowledge base:

```
experts/

    engineering/

        database-engineer/

            SYSTEM.md

            KNOWLEDGE.md

            TOOLS.md

            CONFIG.ts


    general/

        devil-advocate/

            SYSTEM.md

            KNOWLEDGE.md

            TOOLS.md

            CONFIG.ts
```

Eve wrappers (if used) adapt these experts into durable workers. They do not define who is on the council — the Council Assembly Engine does.

---

# Expert Instructions

Every expert needs:

## Identity

Who they are.

Example:

```
You are a Staff Software Engineer with 15 years of experience.
```

---

## Optimization Goal

What they prioritize.

Example:

```
Optimize for maintainability,
simplicity,
and long-term engineering quality.
```

---

## Decision Style

How they reason.

Example:

```
Challenge assumptions.
Identify risks.
Provide alternatives.
Avoid trendy solutions.
```

---

## Output Format

Every expert must return:

```json
{
"recommendation":"",
"reasoning":"",
"risks":[],
"alternatives":[],
"confidence":0.0,
"vote":""
}
```

---

# Eve Skills

Skills represent reusable capabilities.

Examples:

```
skills/

├── architecture-analysis

├── code-review

├── database-design

├── ui-design

├── security-review

├── documentation-generation

├── github-management

├── project-planning
```

---

# Skill Structure

Example:

```
architecture-analysis/

    SKILL.md

    prompts/

    examples/

    schemas/
```

---

# Eve Tools

Tools allow agents to interact with external systems.

Examples:

```
tools/

├── github/

├── filesystem/

├── terminal/

├── database/

├── browser/

├── cloud/

└── documentation/
```

---

# GitHub Tool

Capabilities:

Create repository

Create branches

Create issues

Create milestones

Create labels

Create projects

Create pull requests

Review code

Merge (requires approval)

---

# Filesystem Tool

Capabilities:

Read files

Create files

Modify files

Analyze project structure

Generate documentation

---

# Terminal Tool

Capabilities:

Run commands

Install dependencies

Execute scripts

Run tests

Run builds

Important:

Dangerous commands require approval.

---

# Human Approval System

Certain actions require approval.

Example:

```
Agent:

I want to create GitHub repository.

Reason:

Project initialization.

Approve?

[Y/N]
```

Required approvals:

- GitHub creation
- Push
- Deploy
- Delete
- Database migrations
- Installing unknown packages
- Spending money

---

# Durable Workflows

Long workflows must be resumable.

Example:

Create SaaS Project:

```
Step 1

Analyze idea


Step 2

Run council


Step 3

Generate architecture


Step 4

Create DESIGN.md


Step 5

Initialize repository


Step 6

Create issues


Step 7

Generate MVP plan
```

If interrupted:

Resume from last successful step.

---

# Workflow State

Store:

```typescript
interface WorkflowState {

id:string;

currentStep:string;

completedSteps:string[];

artifacts:string[];

decisions:string[];

errors:string[];

}
```

---

# Council Workflow

Implementation:

```
createCouncilDecision()

{

1. classifyDecision()

2. selectExperts()

3. launchAgents()

4. collectOpinions()

5. startDebate()

6. collectVotes()

7. generateConsensus()

8. saveDecision()

}
```

---

# Parallel Execution

Independent experts run simultaneously.

Example:

```
Promise.all([
 CTO,
 Security,
 Backend,
 DevOps
])
```

Do not execute sequentially unless dependency exists.

---

# Model Selection

Different experts can use different models.

Example:

High reasoning:

Architecture

↓

Advanced reasoning model

Simple tasks:

Documentation

↓

Fast cheap model

---

# Context Management

Agents receive:

Project context

Previous decisions

Relevant documents

Current task

Constraints

They do NOT receive unnecessary information.

---

# Memory Integration

Before running an expert:

Retrieve:

Relevant decisions

Previous discussions

Project documents

Technology choices

---

Example:

Question:

"Add authentication"

Memory:

```
Previous decision:

Use Better Auth.

Reason:

TypeScript compatibility.

Rejected:

Auth.js.
```

Expert should know this.

---

# Observability

Track:

Agent execution

Token usage

Latency

Tool calls

Failures

Decision changes

Consensus changes

---

# Error Handling

If Eve agent fails:

```
Retry

↓

Fallback model

↓

Skip non-critical expert

↓

Continue

```

Never lose workflow state.

---

# Security

Never expose:

API keys

Secrets

Private repositories

User data

All tools require scoped permissions.

---

# MVP Eve Implementation

First version only requires durable execution of **built-in** experts assembled by the engine.

Do not implement user-customized Eve council members yet.

## Agents (seed workers)

```
CTO

Backend Architect

Database Engineer

Security Engineer

Devil's Advocate

Risk Analyst

Critical Thinker
```

These are workers for roles selected by Council Assembly — not a fixed always-on roster.

---

## Tools

```
Filesystem

GitHub

Terminal
```

---

## Workflows

```
Architecture Decision

Project Planning

Issue Generation
```

---

## Storage

```
PostgreSQL

Decision table

Workflow table

Artifact table
```

---

# Future Eve Expansion

Phase 2:

More experts

More tools

More workflows

Phase 3:

Autonomous coding

Testing agents

Review agents

Phase 4:

Complete software company simulation

---

# Golden Rule

Eve executes.

The Council decides.

The Decision Engine remembers.

The Human approves.
