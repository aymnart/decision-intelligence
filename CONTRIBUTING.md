# Contributing

How to work on the Decision Intelligence Engine. Start with [`docs/README.md`](docs/README.md) to find the spec for whatever you are changing.

## Setup

The repository is at the specification stage, with no application code yet. Phase 0 will create the workspace on Node.js 24 LTS and pnpm, with PostgreSQL for storage. The MVP is a CLI, so there is no app server to run ([Foundation](docs/10-architecture/tech-stack/02-foundation.md)); install, build, and test commands will be added here when it does.

Agents working in this repository follow the Cursor rules in `.cursor/rules/`. `project.mdc` applies to every task; the others load for the files they cover.

## Before you change anything

- Check [MVP Scope](docs/00-product/mvp-scope.md). Out-of-scope work needs a decision first.
- Check the [decision records](docs/90-records/decisions/README.md). Changing an accepted decision needs a new ADR, not a silent override.
- Never invent a product decision. Ask, or record it in [assumptions](docs/90-records/assumptions.md) as `Unconfirmed`.

## Branches

Branch from `main` and merge back through a pull request ([ADR-017](docs/90-records/decisions/02-mvp-design.md#adr-017-short-lived-branches-off-main)).

```text
<type>/<issue-number>-<short-name>
```

`<type>` matches the change's commit type, spelled `feature` for `feat`: `feature`, `fix`, `docs`, `refactor`, `chore`, and so on. Drop the issue number when there is no issue. Examples: `feature/12-council-builder`, `fix/31-vote-weighting`, `docs/api-design`.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/): `type(scope): imperative description`, for example `feat(council): add permanent expert injection`.

- One logical change per commit.
- For anything beyond a trivial change, add a body of short bullet points explaining what changed and why.
- Never add AI tools or agents as co-authors.
- Never bypass Git hooks with `--no-verify` unless you have a specific reason.

The full format, types, and examples are in [`.agents/commit/SKILL.md`](.agents/commit/SKILL.md).

## Pull requests

Every pull request includes:

- **Summary**: what changed and why.
- **Changes**: the main changes as bullets.
- **Testing**: what was run and what it covers.
- **Related**: the issue (`Closes #15`) and the requirement IDs (`FR-`, `NFR-`) it implements.
- **Risk**: what could break, and how it would be noticed.

Reviewers check correctness, architecture fit, security, performance, and maintainability ([Code Review Standards](docs/50-quality/08-documentation-and-review.md#code-review-standards)). AI-generated code gets the same review as human code.

A major dependency upgrade also needs tests, an ADR, and a changelog entry ([ADR-007](docs/90-records/decisions/01-foundations.md#adr-007-stack-governance-for-versions-and-dependencies)).

## Definition of done

A change is done only when all of these hold ([Definition of Done](docs/50-quality/09-done-debt-and-failure.md#definition-of-done)):

1. Code is written and follows `.cursor/rules/`.
2. Tests pass, including tests for any critical path it touches.
3. Documentation is updated to explain why, not only what.
4. Architecture is reviewed against [System Design](docs/10-architecture/system-design.md) and ADR-015.
5. Security is checked against `.cursor/rules/security.mdc`.
6. Any decision made is recorded as an ADR.

Shortcuts and known risks go in [tech debt](docs/90-records/tech-debt.md), so they are tracked rather than forgotten.

## Docs

Keep each doc under about 250 lines. Split larger ones into a folder with a `README.md` index, and update its Contents table. Full rules: `.cursor/rules/ai-workflow.mdc`.
