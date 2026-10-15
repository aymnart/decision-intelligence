# Decision Intelligence Engine

For any objective, the Decision Intelligence Engine automatically assembles a temporary council of expert AI agents, runs a structured debate and weighted vote, and returns an explained decision that is stored as memory. The MVP sets out to prove that an automatically generated council makes better decisions than a single AI.

## Status

Specification stage. The repository holds the product, architecture, and planning docs, Cursor rules, and agent skills. No application code exists yet.

The next step is [Phase 0 — Foundation](docs/00-product/roadmap/01-strategy-and-phase-0.md): monorepo, TypeScript configuration, package structure, database, and the AI provider layer. The MVP is [Phase 1 — Autonomous Council Builder](docs/00-product/roadmap/02-phase-1-council-builder-mvp.md): a headless engine with a command-line interface that runs decisions and benchmarks the council against a single AI ([MVP Scope](docs/00-product/mvp-scope.md)). A web app follows once the council wins that benchmark.

## Quick start

```bash
git clone https://github.com/aymnart/decision-intelligence.git
cd decision-intelligence
```

Then open [`docs/README.md`](docs/README.md). Build and run commands will be added here once Phase 0 creates the workspace.

## Docs

| Start here | For |
| --- | --- |
| [docs/README.md](docs/README.md) | Folder map and quick lookup for every topic |
| [MVP Scope](docs/00-product/mvp-scope.md) and [Requirements](docs/00-product/requirements.md) | What the MVP does, and its testable requirements |
| [System Design](docs/10-architecture/system-design.md) | How a decision run executes, fails, and scales |
| [Decision records](docs/90-records/decisions/README.md) | Why things were decided |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to work on the project |

Planned MVP stack: TypeScript monorepo (pnpm, Turborepo) on Node.js 24, PostgreSQL with Drizzle, and the Vercel AI SDK. The web app adds Next.js, Hono, and Inngest. Details in the [tech stack](docs/10-architecture/tech-stack/README.md).
