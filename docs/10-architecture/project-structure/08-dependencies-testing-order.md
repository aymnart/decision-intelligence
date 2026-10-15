> Part of [Project Structure Specification](README.md).

# Dependency Rules

Arrows mean "may depend on". The full rule set, including the `core` ports and the composition root, is in [ADR-015](../../90-records/decisions/02-mvp-design.md#adr-015-repository-layout-and-dependency-direction). `council` reaches `ai` only through the `AIProvider` port in `core`.

Allowed:

```
web

↓

api

↓

workflows

↓

decision-engine

↓

council

↓

ai
```

---

Forbidden:

```
council

↓

web
```

```
database

↓

decision-engine
```

Core must stay independent.

---

# Testing Strategy

Every package requires:

Unit tests

Integration tests

Workflow tests

---

Critical tests:

Decision classification

Expert selection

Consensus calculation

Memory retrieval

Workflow recovery

---

# Development Order

Build in this order:

The MVP (roadmap Phase 1) covers steps 1–4 plus `apps/cli` in place of the UI step ([ADR-018](../../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)). Workflows and Eve integration come after MVP validation ([MVP Scope](../../00-product/mvp-scope.md#out-of-scope)).

## Step 1

Core types

Database

AI abstraction

## Step 2

Council engine

Experts

Decision engine

## Step 3

Consensus engine

## Step 4

Memory system

## Step 5

Workflows

## Step 6

Eve integration

## Step 7

UI

---

# Golden Rule

The codebase should look like a company built this.

Not a collection of AI scripts.

Every component should have a clear purpose, boundary, and owner.
