# Tech Stack

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

The product is the **Decision Intelligence Engine** (`decision-intelligence`).

AI Council is a **Dynamic Council Assembly Engine**, not a fixed group of experts.

The stack supports a Decision Intelligence Engine that:

1. Analyzes intent
2. Detects domains
3. Assembles Required Experts + Permanent Experts
4. Runs debate and consensus
5. Stores decision memory

MVP does not require user-customized councils or Eve-agent experts.

See [AI Council](../../30-specs/ai-council/README.md).

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-philosophy-and-overview.md](01-philosophy-and-overview.md) | Purpose, Philosophy, Architecture Overview | 100 |
| [02-foundation.md](02-foundation.md) | Monorepo, Runtime, Language, Package Manager | 94 |
| [03-backend-and-frontend.md](03-backend-and-frontend.md) | Backend, Frontend, UI Library, Styling, Animations, Forms, API Validation | 130 |
| [04-ai.md](04-ai.md) | AI SDK, AI Orchestration, AI Provider Layer, AI Models | 121 |
| [05-data-and-infrastructure.md](05-data-and-infrastructure.md) | Database, ORM, Authentication, Background Jobs, Caching, Object Storage, Search, Vector Database | 143 |
| [06-observability.md](06-observability.md) | Observability, Error Tracking, Logging, Analytics | 51 |
| [07-tooling-and-ci.md](07-tooling-and-ci.md) | Documentation, Testing, Linting, Git Hooks, CI/CD | 106 |
| [08-deployment-and-secrets.md](08-deployment-and-secrets.md) | Deployment, Database Hosting, Secrets, File Generation | 65 |
| [09-repository-and-dependencies.md](09-repository-and-dependencies.md) | Repository Structure, Dependency Rules, Dependency Injection | 111 |
| [10-governance.md](10-governance.md) | Version Policy, Stack Governance, Technology Decision Process, Future Technologies, Golden Rules | 102 |
