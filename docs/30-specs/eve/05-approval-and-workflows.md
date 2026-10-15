> Part of [Eve Implementation Specification](README.md).

# Human Approval System

Certain actions require approval.

Example:

```
Agent:

I want to create GitHub repository.

Reason:

Project initialization.

Approve?

[Y/N]
```

Required approvals:

- GitHub creation
- Push
- Deploy
- Delete
- Database migrations
- Installing unknown packages
- Spending money

---

# Durable Workflows

Long workflows must be resumable.

Example:

Create SaaS Project:

```
Step 1

Analyze idea


Step 2

Run council


Step 3

Generate architecture


Step 4

Create DESIGN.md


Step 5

Initialize repository


Step 6

Create issues


Step 7

Generate MVP plan
```

If interrupted:

Resume from last successful step.

---

# Workflow State

Store:

```typescript
interface WorkflowState {

id:string;

currentStep:string;

completedSteps:string[];

artifacts:string[];

decisions:string[];

errors:string[];

}
```

---

# Council Workflow

Implementation:

```
createCouncilDecision()

{

1. classifyDecision()

2. selectExperts()

3. launchAgents()

4. collectOpinions()

5. startDebate()

6. collectVotes()

7. generateConsensus()

8. saveDecision()

}
```

---

# Parallel Execution

Independent experts run simultaneously.

Example:

```
Promise.all([
 CTO,
 Security,
 Backend,
 DevOps
])
```

Do not execute sequentially unless dependency exists.
