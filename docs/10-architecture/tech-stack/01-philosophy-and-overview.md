> Part of [Tech Stack](README.md).

# Purpose

This document is the single source of truth for the technology stack of the Decision Intelligence Engine.

Every architectural decision regarding technologies must originate here.

The stack is intentionally opinionated.

Consistency is preferred over endlessly evaluating technologies.

Any deviation from this stack requires:

1. AI Council approval (via Dynamic Council Assembly)
2. Architecture Decision Record (ADR)
3. Update to this document

---

# Philosophy

The stack optimizes for:

- Developer Experience
- Type Safety
- AI-native development
- Maintainability
- Scalability
- Vendor independence
- Production readiness

Priority:

```
Developer Experience

↓

Correctness

↓

Maintainability

↓

Performance

↓

Scalability

↓

Cost Optimization
```

---

# Architecture Overview

```
                        Users / AI Agents
                          │
                          ▼
                 Next.js Web Application
                          │
                          ▼
                     Hono API Server
                          │
                          ▼
           Decision Intelligence Engine
                          │
                          ▼
              Intent → Domain → Impact
                          │
                          ▼
              Council Assembly Engine
                          │
             ┌────────────┴────────────┐
             ▼                         ▼
      Required Experts          Permanent Experts
      (domain knowledge)        (quality control)
             │                         │
             └────────────┬────────────┘
                          ▼
                   Debate + Consensus
                          │
             ┌────────────┴────────────┐
             ▼                         ▼
      AI Provider Layer          Memory Layer
             │                         │
             ▼                         ▼
       OpenAI / Anthropic      PostgreSQL
             │
             ▼
      Background Jobs
          (Inngest)
```
