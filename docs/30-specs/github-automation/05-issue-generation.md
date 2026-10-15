> Part of [GitHub Automation Specification](README.md).

# Issue Generation

The AI Planner generates issues.

Every issue must contain:

---

## Title

Clear action.

Bad:

```
Authentication
```

Good:

```
Implement user authentication flow
```

---

## Description

Explain:

Why

Context

Goal

Implementation notes

---

## Acceptance Criteria

Must be measurable.

Example:

```
Given a registered user

When they login

Then they receive a valid session
```

---

## Technical Notes

Include:

Files affected

Libraries

Architecture considerations

---

## Dependencies

Example:

```
Depends on:

#12 Database setup
```

---

## Priority

Required.

---

## Estimate

Example:

```
Small

Medium

Large
```

---

# Issue Example

```
Title:

Create project database schema


Description:

Create initial database models required
for project management.


Acceptance Criteria:

- Project table exists
- Migration created
- Tests pass


Labels:

backend

database

priority-high


Milestone:

MVP


Dependencies:

None

```

---

# Issue Ordering

Issues must be generated in dependency order.

Example:

Wrong:

```
Create dashboard UI

before

Database exists
```

Correct:

```
1. Database schema

2. API layer

3. Authentication

4. UI components
```
