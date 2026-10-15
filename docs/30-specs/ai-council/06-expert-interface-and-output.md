> Part of [AI Council System Specification](README.md).

# Expert Interface

Everything should follow the same contract.

```ts
interface CouncilExpert {

  id: string;

  name: string;

  domain: string[];

  type:
    | "built-in"
    | "custom"
    | "eve-agent";

  instructions: string;

  capabilities: Capability[];

  weight: number;

  alwaysIncluded?: boolean;

  analyze(context): ExpertOpinion;

}
```

Built-in experts ship with the product.

Custom and Eve-agent types are post-MVP extensions of the same interface.

---

# Expert Output Contract

Experts must never return unstructured text.

Every response must follow:

```typescript
interface ExpertOpinion {

  expertId: string;

  recommendation: string;

  reasoning: string;

  assumptions: string[];

  advantages: string[];

  disadvantages: string[];

  alternatives: Alternative[];

  risks: Risk[];

  confidence: number;

  vote: Vote;

}
```
