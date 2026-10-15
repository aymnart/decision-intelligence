> Part of [System Architecture](README.md).

# Human Approval

Certain operations pause execution.

Examples

Repository creation

Push

Merge

Deployment

Deleting files

Deleting repos

Billing

Execution resumes after approval.

---

# Fault Tolerance

Every component must support retries.

Expert fails

↓

Retry

↓

Fallback model

↓

Report failure

↓

Continue if possible

No single expert failure should crash the system.

---

# Logging

Every important action should be logged.

Examples

Prompt sent

Tokens used

Latency

Votes

Consensus

Execution time

Errors

Retries

Approval requests

Artifacts generated
