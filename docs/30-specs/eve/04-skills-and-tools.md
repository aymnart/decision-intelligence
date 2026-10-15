> Part of [Eve Implementation Specification](README.md).

# Eve Skills

Skills represent reusable capabilities.

Examples:

```
skills/

├── architecture-analysis

├── code-review

├── database-design

├── ui-design

├── security-review

├── documentation-generation

├── github-management

├── project-planning
```

---

# Skill Structure

Example:

```
architecture-analysis/

    SKILL.md

    prompts/

    examples/

    schemas/
```

---

# Eve Tools

Tools allow agents to interact with external systems.

Examples:

```
tools/

├── github/

├── filesystem/

├── terminal/

├── database/

├── browser/

├── cloud/

└── documentation/
```

---

# GitHub Tool

Capabilities:

Create repository

Create branches

Create issues

Create milestones

Create labels

Create projects

Create pull requests

Review code

Merge (requires approval)

---

# Filesystem Tool

Capabilities:

Read files

Create files

Modify files

Analyze project structure

Generate documentation

---

# Terminal Tool

Capabilities:

Run commands

Install dependencies

Execute scripts

Run tests

Run builds

Important:

Dangerous commands require approval.
