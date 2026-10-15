# Decision Intelligence Engine — Docs

Every spec is split into short topic files. Each folder has a `README.md` index listing which sections live in which file.

How to read:

1. Find the topic below.
2. Open that folder's `README.md`.
3. Open only the file(s) that cover the task.

---

## Map

| Folder | Contents |
| --- | --- |
| [00-product/vision](00-product/vision/README.md) | Vision, mission, principles, project and coding rules, decision and council philosophy (master prompt) |
| [00-product/roadmap](00-product/roadmap/README.md) | Implementation roadmap, Phase 0 through Phase 9 |
| [10-architecture/system](10-architecture/system/README.md) | Layers, core components, execution pipeline, events, fault tolerance, scaling |
| [10-architecture/tech-stack](10-architecture/tech-stack/README.md) | Chosen technologies per layer, dependency rules, stack governance |
| [10-architecture/project-structure](10-architecture/project-structure/README.md) | Monorepo layout, package responsibilities, expert file structure, database models |
| [30-specs/decision-engine](30-specs/decision-engine/README.md) | Decision lifecycle, impact classification, expert selection, debate, consensus, decision memory |
| [30-specs/ai-council](30-specs/ai-council/README.md) | Dynamic council assembly, permanent experts, expert interface, debate and voting |
| [30-specs/eve](30-specs/eve/README.md) | Eve agents, skills, tools, durable workflows, human approval |
| [30-specs/github-automation](30-specs/github-automation/README.md) | Repo setup, branches and PRs, labels, milestones, issue generation |
| [40-planning/mvp-plan](40-planning/mvp-plan/README.md) | MVP definition, MVP stack and schema, sprints 1–7, MVP interface, success metrics |
| [40-planning/tasks](40-planning/tasks/README.md) | Issue-level task list by phase |
| [50-quality](50-quality/README.md) | Code quality, testing, AI output quality, prompts, security, performance, review, definition of done |
| [20-design](20-design/README.md) | Design system, brand guidelines, and UX flows (roadmap Phase 2 web app) |
| [90-records/decisions](90-records/decisions/README.md) | Architecture decision records with a status index |

Not yet written (empty placeholders):

- `00-product/`: `user-stories.md`
- `10-architecture/`: `api-design.md` (HTTP API, roadmap Phase 2)
- `20-design/`: `design-system.md`, `brand-guidelines.md`, `ux-flows.md` (web app, roadmap Phase 2)

---

## Quick lookup

| Looking for | Open |
| --- | --- |
| What the product is and why | `00-product/vision/01-vision-and-mission.md` |
| What to build first | `40-planning/mvp-plan/04-sprints-1-3.md`, `40-planning/tasks/09-mvp-completion-and-first-sprint.md` |
| What is in or out of scope for MVP | `00-product/mvp-scope.md` |
| What the MVP must do (FR / NFR IDs) | `00-product/requirements.md` |
| How a council is assembled | `30-specs/ai-council/07-council-assembly.md`, `30-specs/decision-engine/04-expert-selection.md` |
| Where code goes | `10-architecture/project-structure/01-purpose-and-repository.md` |
| Which library to use | `10-architecture/tech-stack/README.md` |
| Coding rules | `50-quality/02-code-quality.md`, `00-product/vision/03-project-and-code-rules.md` |
| Database tables, enums, indexes, migrations | `10-architecture/database-design.md` |
| How a decision run executes, fails, and scales | `10-architecture/system-design.md` |
| MVP CLI commands | `10-architecture/system-design.md#commands` |
| Why something was decided | `90-records/decisions/README.md` |
| What is still unconfirmed | `90-records/assumptions.md` |
| Tracked technical debt | `90-records/tech-debt.md` |
