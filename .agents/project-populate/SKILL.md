---
name: project-populate
description: >-
  Fill empty project docs, Cursor rules, and root files created by project-init,
  one file per pass, using existing docs as sources and asking the user only
  for decisions the docs cannot answer. Use when populating, drafting, or
  filling empty files in docs/, .cursor/rules/, README.md, or CONTRIBUTING.md.
argument-hint: Optional target file or wave, e.g. "docs/90-records/decisions.md" or "wave 1"
---

# Project Populate

Turn the empty skeleton from `project-init` into real project context, one reviewed file at a time.

## Core Rules

1. **One target file per pass.** Draft, show the user, apply feedback, then move on.
2. **Read only the listed sources.** Navigate via `docs/README.md` → folder `README.md` → part file. Never read whole folders.
3. **Never invent product decisions.** If a source doesn't answer it, ask (wave 2) or record it in `docs/90-records/assumptions.md` marked `Unconfirmed`.
4. **One source of truth.** Summarize and link to existing specs; don't copy their text. If two sources conflict, stop and ask which one wins.
5. **Respect the split rule.** Keep files under ~250 lines; if a draft is longer, make it a folder per `.cursor/rules/ai-workflow.mdc`.
6. **No app code**, no placeholders, no TODO stubs. A file is either fully written or still empty.

## Workflow

### 1. Pick the target

- If the user named a file or wave, use it.
- Otherwise list empty files (`find docs .cursor/rules -empty -type f` plus root files) and take the first empty one in wave order below.
- Skip wave-3 files unless the user asks for them.

### 2. Gather

- Read the sources listed for the target in the source map.
- Read the index in `docs/90-records/decisions/README.md` (or `decisions.md` if not yet split), then only the ADRs relevant to the target, so the draft stays consistent with recorded decisions.
- **Wave 2 targets:** before drafting, ask 3–6 multiple-choice questions with the AskQuestion tool. Offer options grounded in the existing docs, recommended option first.

### 3. Draft

- Follow the template for the target.
- Cite sources as relative links, e.g. `[MVP scope rationale](../40-planning/mvp-plan/07-success-and-scope.md)`.
- New facts that come from the user's answers belong in this file only; other files link here.

### 4. Review and apply

- Show the user a short summary (what was written, sources used, any open questions), then write the file.
- If the user had to decide something, add a record to the last part of `decisions/` and its index. If you had to assume something, add it to `assumptions.md`.
- Remove the file from the "Not yet written" list in `docs/README.md`, and add a quick-lookup row if it's a common question.
- Run `graphify update .`.

## Waves

| Wave | Files | Input |
| --- | --- | --- |
| 1 — derive | `90-records/decisions.md`, `00-product/mvp-scope.md`, `00-product/requirements.md`, `10-architecture/database-design.md`, `10-architecture/system-design.md`, `.cursor/rules/*.mdc`, `README.md`, `CONTRIBUTING.md` | Existing docs only |
| 2 — ask | `00-product/user-stories.md`, `10-architecture/api-design.md`, `20-design/ux-flows.md`, `20-design/design-system.md`, `20-design/brand-guidelines.md` | User answers + docs |
| 3 — organic | `90-records/assumptions.md`, `90-records/tech-debt.md`, `CHANGELOG.md`, `.env.example` | Grows during work |

Do `decisions.md` and `mvp-scope.md` first; everything else references them.

## Source Map

| Target | Sources |
| --- | --- |
| `decisions.md` | `10-architecture/tech-stack/` (README + `10-governance.md`), `10-architecture/project-structure/01`, `30-specs/ai-council/01`, `03`, `00-product/vision/02` |
| `mvp-scope.md` | `40-planning/mvp-plan/01`, `07`, `30-specs/ai-council/03-mvp.md`, `30-specs/decision-engine/10-mvp-and-future.md` |
| `requirements.md` | `00-product/vision/01`, `mvp-scope.md`, `30-specs/decision-engine/02`, `03`, `30-specs/ai-council/07` |
| `database-design.md` | `10-architecture/project-structure/07-database-models.md`, `40-planning/mvp-plan/03-database-schema.md`, `10-architecture/tech-stack/05` |
| `system-design.md` | `10-architecture/system/01`, `05`, `06`, `30-specs/eve/05` |
| `user-stories.md` | `40-planning/mvp-plan/01-definition-and-user-flow.md`, `requirements.md` |
| `api-design.md` | `10-architecture/tech-stack/03`, `10-architecture/project-structure/02-apps.md`, `database-design.md` |
| `ux-flows.md` | `40-planning/mvp-plan/01`, `06-interface.md` |
| `design-system.md`, `brand-guidelines.md` | `00-product/vision/06-design-and-stack.md`, `10-architecture/tech-stack/03` |
| `project.mdc` | `00-product/vision/01`, `02`, `mvp-scope.md` |
| `architecture.mdc` | `10-architecture/system/01`, `10-architecture/project-structure/08`, `10-architecture/tech-stack/09` |
| `coding-standards.mdc` | `50-quality/02-code-quality.md`, `00-product/vision/03` |
| `testing.mdc` | `50-quality/03-testing.md` |
| `security.mdc` | `50-quality/06-security.md`, `00-product/vision/07-operations.md` |
| `README.md` (root) | `docs/README.md`, `00-product/vision/01`, `mvp-scope.md` |
| `CONTRIBUTING.md` | `30-specs/github-automation/03-branches-commits-prs.md`, `50-quality/08`, `09`, `.agents/commit/SKILL.md` |

Paths are relative to `docs/` unless they start with `.` or are root files.

## Templates

**`decisions.md`** — one ADR per decision, newest last:

```markdown
## ADR-001: <title>

- Status: Accepted | Proposed | Superseded by ADR-00X
- Date: YYYY-MM-DD
- Source: <link>

**Context** — the problem.
**Options** — what was considered.
**Decision** — what was chosen.
**Consequences** — what this makes easier and harder.
```

**`assumptions.md`** — `| ID | Assumption | Status (Unconfirmed / Confirmed / Rejected) | Owner | Link |`

**`tech-debt.md`** — `| ID | Debt | Impact | Fix | Added |`

**`mvp-scope.md`** — Goal (one sentence) · In scope · Out of scope (with reason) · Success metrics · Exit criteria.

**`requirements.md`** — Functional requirements `FR-001 …` and non-functional `NFR-001 …`, each one testable, each linking its source spec.

**`user-stories.md`** — grouped by persona: `As a <persona>, I want <action> so that <outcome>` + acceptance criteria + linked `FR-` IDs.

**`database-design.md`** — Entities table · relationships (Mermaid `erDiagram`) · indexes · migration policy. This becomes the schema source of truth; the other two schema docs link here.

**`system-design.md`** — Request lifecycle (Mermaid `sequenceDiagram`) · failure modes and handling · scaling limits for MVP.

**`api-design.md`** — Style and auth · conventions (errors, pagination, versioning) · endpoint table `| Method | Path | Purpose | FR |`.

**`ux-flows.md`** — one Mermaid `flowchart` per flow, plus screens and empty/error states.

**`design-system.md` / `brand-guidelines.md`** — tokens (color, type, spacing, radius), components, voice and tone, do/don't examples.

**`.cursor/rules/*.mdc`** — frontmatter (`description`, `globs` or `alwaysApply`), under 50 lines, imperative bullets, one ✅/❌ example where it helps, link to the full doc for detail. Only `project.mdc` is `alwaysApply: true`; scope the rest with `globs` (e.g. `**/*.ts`, `**/*.test.ts`).

**`README.md` (root)** — what it is (2 sentences) · status · quick start (only commands that exist) · docs link.

**`CONTRIBUTING.md`** — setup · branch/commit/PR rules · definition of done · link to `docs/README.md`.

## Final Validation

- ✓ Every claim traces to a cited source, a user answer, or an `assumptions.md` entry
- ✓ No text duplicated from another doc; links instead
- ✓ File under ~250 lines (or split into a folder with index)
- ✓ `docs/README.md` "Not yet written" list updated
- ✓ New decisions and assumptions recorded

## Output Summary

```
Populated: <file> (<lines> lines)
Sources: <links>
Decisions added: <ADR IDs or none>
Assumptions added: <IDs or none>
Open questions: <list or none>
Next: <next empty file in wave order>
```
