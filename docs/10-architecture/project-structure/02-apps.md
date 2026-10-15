> Part of [Project Structure Specification](README.md).

# Package Responsibilities

---

# apps/cli

The MVP's only app ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)).

Responsibility:

Command-line interface and composition root.

Handles:

- commands (`decide`, `show`, `list`, `approve`, `reject`, `resume`, `eval`)
- wiring adapters into the engine
- progress and report output
- approval prompts

Must NOT contain:

- business logic
- expert prompts
- decision rules

Commands: [System Design](../system-design.md#commands).

---

# apps/web

Roadmap Phase 2.

Responsibility:

User interface.

Contains:

- dashboard
- conversations
- decisions
- approvals
- artifacts
- project views

Must NOT contain:

- AI logic
- expert prompts
- decision rules

---

# apps/api

Roadmap Phase 2.

Responsibility:

API layer.

Handles:

- authentication
- requests
- streaming responses
- workflow triggers

Must NOT contain:

- business logic
