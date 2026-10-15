> Part of [Project Structure Specification](README.md).

# packages/planner

Responsible for converting decisions into execution plans.

Examples:

```
Architecture

↓

Roadmap

↓

Milestones

↓

Tasks

↓

Issues
```

Contains:

```
planner/

roadmap/

milestones/

tasks/

dependencies/
```

---

# packages/executor

Responsible for performing actions.

Examples:

- create files
- run commands
- modify projects
- generate artifacts

Contains:

```
executor/

commands/

actions/

approvals/

validators/
```

---

# packages/workflows

Contains complete business workflows.

Examples:

```
workflows/

create-project/

architecture-review/

feature-development/

bug-fix/

code-review/
```

A workflow orchestrates multiple packages.

---

# packages/github

GitHub integration.

Contains:

```
github/

repositories/

issues/

projects/

pull-requests/

labels/
```

---

# packages/eve

Eve integration layer.

Important:

Only this package knows Eve exists.

Everything else remains framework independent.

Contains:

```
eve/

agents/

tools/

workflows/

adapters/
```
