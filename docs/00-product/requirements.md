# Requirements

Testable requirements for the MVP defined in [MVP Scope](mvp-scope.md): a headless engine with a command-line interface ([ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli)). "The operator" is the person running the CLI. Each requirement links the spec or decision it comes from. User stories reference these IDs.

---

## Functional requirements

### Submission and decision record

| ID | Requirement | Source |
| --- | --- | --- |
| FR-001 | The operator can submit a decision or problem as free text with `decide`, optionally with extra context. The system creates a decision with status `CREATED`. | [MVP definition](../40-planning/mvp-plan/01-definition-and-user-flow.md#mvp-definition), [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) |
| FR-002 | Every decision has `id`, `title`, `description`, `category`, `impact`, `status`, `context`, `experts`, `debate`, `consensus`, `createdAt`, and `updatedAt`. | [Decision Object](../30-specs/decision-engine/02-lifecycle-object-categories.md#decision-object) |
| FR-003 | A decision moves through `CREATED`, `CLASSIFIED`, `CONTEXT_LOADED`, `COUNCIL_SELECTED`, `EXPERT_ANALYSIS`, `DEBATE`, `VOTING`, `CONSENSUS`, `APPROVED`, `STORED`, in that order. States that do not apply to its impact level (such as `DEBATE` for low impact) are skipped. `EXECUTED` and `EVALUATED` are not used in the MVP. | [Decision Lifecycle](../30-specs/decision-engine/02-lifecycle-object-categories.md#decision-lifecycle), [ADR-010](../90-records/decisions/02-mvp-design.md#adr-010-mvp-decision-lifecycle-ends-at-stored-with-human-approval-for-high-impact) |

### Classification

| ID | Requirement | Source |
| --- | --- | --- |
| FR-004 | The classifier assigns each decision exactly one category from `DecisionCategory`, falling back to `OTHER`. | [Decision Categories](../30-specs/decision-engine/02-lifecycle-object-categories.md#decision-categories) |
| FR-005 | The classifier detects one or more domains for each decision. | [Domain Classifier](../30-specs/decision-engine/10-mvp-and-future.md#domain-classifier), [Council Assembly Algorithm](../30-specs/ai-council/07-council-assembly.md#council-assembly-algorithm) |
| FR-006 | The classifier assigns an impact level of `LOW`, `MEDIUM`, or `HIGH`, considering blast radius, reversibility, cost, security impact, and business impact. | [Classification Factors](../30-specs/decision-engine/03-impact-classification.md#classification-factors) |
| FR-007 | Classifier output is a structured object containing category, impact, required experts, and reasoning depth. | [Decision Classifier](../30-specs/decision-engine/03-impact-classification.md#decision-classifier) |

### Council assembly

| ID | Requirement | Source |
| --- | --- | --- |
| FR-008 | The expert registry holds built-in experts organized by domain. Every expert implements the shared `CouncilExpert` contract. | [Expert Registry](../30-specs/decision-engine/10-mvp-and-future.md#expert-registry) |
| FR-009 | The council builder retrieves expert candidates for the detected domains and ranks them. | [Council Builder](../30-specs/decision-engine/10-mvp-and-future.md#council-builder) |
| FR-010 | A low-impact council has one domain expert and may include one permanent expert as a check. | [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| FR-011 | A medium-impact council has 3–5 domain experts plus Devil's Advocate, Risk Analyst, and Critical Thinker. | [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| FR-012 | A high-impact council has all relevant domain experts plus Devil's Advocate, Risk Analyst, and Critical Thinker. | [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| FR-013 | Ethics/Safety Reviewer is added to the council, at any impact level, when a sensitive or regulated domain is detected. | [Permanent Council Members](../30-specs/ai-council/04-expert-categories-and-permanent-members.md#permanent-council-members), [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| FR-014 | Users cannot add, remove, or replace council members. | [ADR-004](../90-records/decisions/01-foundations.md#adr-004-mvp-councils-are-built-autonomously-with-no-user-customization) |

### Analysis, debate, and consensus

| ID | Requirement | Source |
| --- | --- | --- |
| FR-015 | Each expert produces its opinion independently, without seeing other experts' opinions. | [Debate Engine](../30-specs/decision-engine/10-mvp-and-future.md#debate-engine) |
| FR-016 | Debate runs critique and revision rounds: none for low impact, one for medium impact, and at least two for high impact. | [Impact Classification](../30-specs/decision-engine/03-impact-classification.md), [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| FR-017 | Experts vote, and the consensus engine combines the votes with weighted voting. | [Consensus Engine](../30-specs/decision-engine/10-mvp-and-future.md#consensus-engine) |
| FR-018 | The consensus report contains the final decision, the reasoning behind it, and a minority report for each dissenting position. | [Consensus Engine](../30-specs/decision-engine/10-mvp-and-future.md#consensus-engine), [MVP definition](../40-planning/mvp-plan/01-definition-and-user-flow.md#mvp-definition) |

### Approval, storage, and display

| ID | Requirement | Source |
| --- | --- | --- |
| FR-019 | A high-impact decision stays in `APPROVED` until the operator confirms or rejects it, either at the prompt after the report or later with `approve` or `reject`. A rejected decision ends as `REJECTED` with its reasoning kept. Low- and medium-impact decisions pass through without human approval. | [ADR-010](../90-records/decisions/02-mvp-design.md#adr-010-mvp-decision-lifecycle-ends-at-stored-with-human-approval-for-high-impact), [ADR-014](../90-records/decisions/02-mvp-design.md#adr-014-mvp-decision-run-orchestration), [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) |
| FR-020 | A stored decision keeps its classification, council, every expert opinion, the debate, the votes, and the consensus report, and can be retrieved later. | [Decision Storage / Memory](../30-specs/decision-engine/10-mvp-and-future.md#decision-storage--memory) |
| FR-021 | The operator can print the consensus report for any stored decision with `show`, including who sat on the council and why the decision was made. | [MVP user flow](../40-planning/mvp-plan/01-definition-and-user-flow.md#mvp-user-flow), [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) |
| FR-024 | The operator can list decisions with `list`, filtered by status, including those awaiting approval. | [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) |
| FR-025 | `resume` continues an interrupted run from its last stored stage without repeating completed stages. | [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli), [ADR-014](../90-records/decisions/02-mvp-design.md#adr-014-mvp-decision-run-orchestration) |

### Evaluation

| ID | Requirement | Source |
| --- | --- | --- |
| FR-022 | Removed: the report rating left the MVP with the Trust metric. | [ADR-018](../90-records/decisions/02-mvp-design.md#adr-018-the-mvp-is-a-headless-engine-with-a-cli) |
| FR-023 | `eval run` sends a fixed question set through the council and a single-AI baseline and writes anonymized pairs in random order for blind rating. `eval score` reads the ratings and reports the council's preference rate. | [ADR-012](../90-records/decisions/02-mvp-design.md#adr-012-measurable-mvp-success-targets) |

---

## Non-functional requirements

| ID | Requirement | Source |
| --- | --- | --- |
| NFR-001 | Every consensus report explains why the decision was made in terms a user can follow without reading the raw expert output. | [Vision](vision/01-vision-and-mission.md#core-philosophy), [Success metrics](mvp-scope.md#success-metrics) |
| NFR-002 | All classifier, expert, and consensus outputs are validated against typed schemas, and invalid output is rejected rather than stored. | [ADR-005](../90-records/decisions/01-foundations.md#adr-005-typescript-monorepo-with-pnpm-and-turborepo) |
| NFR-003 | Changing the AI provider requires no code change in the decision engine, council, or consensus packages. | [ADR-006](../90-records/decisions/01-foundations.md#adr-006-the-engine-is-independent-of-frameworks-providers-and-eve) |
| NFR-004 | The decision engine package does not import any web, API, or agent-runtime framework. | [ADR-006](../90-records/decisions/01-foundations.md#adr-006-the-engine-is-independent-of-frameworks-providers-and-eve) |
| NFR-005 | Reasoning cost scales with impact: a low-impact decision makes at most two expert calls. | [Impact Classification](../30-specs/decision-engine/03-impact-classification.md), [ADR-009](../90-records/decisions/02-mvp-design.md#adr-009-council-composition-scales-with-impact-level) |
| NFR-006 | The system preserves complete decision history: stored decisions are never deleted as a side effect of new decisions. | [Mission](vision/01-vision-and-mission.md#mission) |
| NFR-007 | At the 95th percentile, time from submission to consensus report is under 15 seconds for low impact, 2 minutes for medium impact, and 5 minutes for high impact. Time spent waiting for human approval is excluded. | [ADR-011](../90-records/decisions/02-mvp-design.md#adr-011-mvp-response-time-targets-per-impact-level) |
