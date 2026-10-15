> Part of [Decision Intelligence Engine Specification](README.md).

# Decision Lifecycle

Every decision follows this lifecycle:

```
CREATED

↓

CLASSIFIED

↓

CONTEXT_LOADED

↓

COUNCIL_SELECTED

↓

EXPERT_ANALYSIS

↓

DEBATE

↓

VOTING

↓

CONSENSUS

↓

APPROVED

↓

STORED

↓

EXECUTED

↓

EVALUATED
```

---

# Decision Object

Every decision must have a structured representation.

```typescript
interface Decision {

id: string;

title: string;

description: string;

category: DecisionCategory;

impact: ImpactLevel;

status: DecisionStatus;

context: Context;

experts: ExpertOpinion[];

debate: DebateSession;

consensus: ConsensusResult;

createdAt: Date;

updatedAt: Date;

}
```

---

# Decision Categories

The system must classify decisions.

Available categories:

```typescript
enum DecisionCategory {

ARCHITECTURE,

TECH_STACK,

DATABASE,

SECURITY,

INFRASTRUCTURE,

PRODUCT,

UX,

UI,

BUSINESS,

MARKETING,

CODE,

REFACTORING,

TESTING,

AI,

OTHER

}
```
