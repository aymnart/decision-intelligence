> Part of [Decision Intelligence Engine Task List](README.md).

# Phase 2 — Advanced Decision Engine

---

## Issue 013

Title:

Create decision impact classifier

Description:

Automatically classify decisions.

Categories:

- low
- medium
- high

Acceptance Criteria:

System selects correct reasoning depth.

---

## Issue 014

Title:

Create dynamic council assembly engine

Description:

Select experts based on problem using the assembly algorithm.

Input:

Intent, domains, impact

Process:

Retrieve candidates → Rank → Add mandatory experts → Create council

Output:

Required experts + permanent quality-control agents

Acceptance Criteria:

Only relevant experts participate; mandatory experts are always injected when required.

---

## Issue 015

Title:

Implement debate engine

Description:

Create multi-round expert debate.

Rounds:

1. Independent opinions

2. Criticism

3. Revision

Acceptance Criteria:

Experts can update opinions; permanent experts apply challenge pressure.

---

## Issue 016

Title:

Implement weighted consensus

Description:

Improve voting quality.

Requirements:

- expert weights
- confidence
- category relevance

Acceptance Criteria:

Final decision considers expertise.
