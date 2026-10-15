> Part of [Decision Intelligence Engine Quality Guidelines](README.md).

# Security Guidelines

Security is mandatory.

---

# Secrets

Never:

- hardcode keys
- expose tokens
- store secrets in logs

Use:

- environment variables
- secret managers

---

# Authentication

Must include:

- secure sessions
- authorization checks
- permission boundaries

---

# AI Tool Security

Agents must have minimal permissions.

Example:

Documentation agent:

Can:

read files

Cannot:

deploy

---

# Command Execution Security

Before running commands:

Validate:

- command safety
- user approval
- permissions

Dangerous:

```

rm

delete

production deployment

```

require approval.

---

# Data Privacy

The system must:

- minimize stored data
- encrypt sensitive information
- control access
