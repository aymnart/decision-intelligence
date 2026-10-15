# Technical Debt

Known technical debt, shortcuts, compromises, and deferred fixes. Update whenever debt is incurred or paid down.

| ID | Debt | Impact | Fix | Added |
| --- | --- | --- | --- | --- |
| TD-001 | Single file prompts in `experts/` synced to DB at startup | Re-syncing required on prompt changes | Automated file watcher or database-backed versioned prompt catalog in Phase 2 | 2026-10-15 |
