> Part of [Decision Intelligence Engine Specification](README.md).

# Context Retrieval

Before experts reason, retrieve relevant knowledge.

Sources:

```
PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

DECISIONS.md

Previous discussions

Existing code
```

---

# Context Filtering

Never send everything.

Retrieve only relevant information.

Example:

Authentication decision:

Include:

```
Current stack

Database

Existing auth decisions

Security requirements
```

Exclude:

```
Color palette

Marketing strategy
```

---

# Expert Execution

Experts execute independently.

Input:

```typescript
interface ExpertTask {

problem:string;

context:Context;

constraints:string[];

role:Expert;

}
```

Output:

```typescript
interface ExpertOpinion {

recommendation:string;

reasoning:string;

pros:string[];

cons:string[];

risks:string[];

alternatives:string[];

confidence:number;

vote:"approve"|"reject";

}
```
