# GitHub Automation Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

GitHub automation is a **consumer** of the Dynamic Council Assembly Engine — not a replacement for it.

Architecture, stack, and project-setup decisions must pass through Decision Intelligence → Council Assembly → Debate → Consensus before GitHub actions run.

MVP validates autonomous council assembly first. GitHub automation comes later.

See [AI Council](../ai-council/README.md).

---

## Contents

Open only the file that covers what you need.

| File | Sections | Lines |
| --- | --- | --- |
| [01-purpose-and-workflow.md](01-purpose-and-workflow.md) | Purpose, Core Principle, GitHub Workflow | 107 |
| [02-repository-setup.md](02-repository-setup.md) | Repository Creation, Repository Configuration, Repository Metadata, Initial Files | 122 |
| [03-branches-commits-prs.md](03-branches-commits-prs.md) | Branch Strategy, Commit Rules, Pull Request Rules | 94 |
| [04-labels-milestones-projects.md](04-labels-milestones-projects.md) | Labels, Type Labels, Priority Labels, Area Labels, Status Labels, Milestones, Milestone Structure, GitHub Projects | 167 |
| [05-issue-generation.md](05-issue-generation.md) | Issue Generation, Issue Example, Issue Ordering | 172 |
| [06-roadmap-and-dev-loop.md](06-roadmap-and-dev-loop.md) | Roadmap Integration, Automatic Issue Updates, AI Development Loop | 107 |
| [07-permissions-and-health.md](07-permissions-and-health.md) | GitHub Permissions, Human Approval Required, Repository Health Monitoring, Future Features, Golden Rule | 101 |
