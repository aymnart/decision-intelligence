> Part of [Project Structure Specification](README.md).

# packages/core

The foundation package.

Contains:

- common types
- domain objects
- interfaces
- constants

Example:

```
core/

types/

Decision.ts

Expert.ts

Workflow.ts

Artifact.ts
```

Every package can depend on core.

Core depends on nothing.

---

# packages/decision-engine

The brain — Decision Intelligence Engine.

Contains:

- intent analyzer
- domain detection
- decision classifier
- impact analysis
- council assembly logic
- decision lifecycle

Example:

```
decision-engine/

intent/

domain/

classifier/

assembly/

lifecycle/

rules/
```

---

# packages/council

Responsible for:

- expert registry / knowledge base
- expert execution
- temporary council creation
- permanent expert injection

Contains:

```
council/

experts/

builder/

runner/

registry/
```

MVP: built-in experts only. Custom and Eve-agent types share the same `CouncilExpert` interface but are post-MVP.

---

# packages/consensus

Responsible for:

- debate processing
- voting
- confidence scoring
- final recommendations

Contains:

```
consensus/

debate/

voting/

scoring/

reports/
```

---

# packages/memory

Responsible for project knowledge.

Handles:

- decisions
- documents
- previous conversations
- context retrieval

Contains:

```
memory/

storage/

retrieval/

embeddings/

ranking/
```
