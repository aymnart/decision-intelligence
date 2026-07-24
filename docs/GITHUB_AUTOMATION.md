# GitHub Automation Specification

Version: 2.0

---

# Architecture Direction

Yes. This is the correct architecture direction.

GitHub automation is a **consumer** of the Dynamic Council Assembly Engine — not a replacement for it.

Architecture, stack, and project-setup decisions must pass through Decision Intelligence → Council Assembly → Debate → Consensus before GitHub actions run.

MVP validates autonomous council assembly first. GitHub automation comes later.

See `AI_COUNCIL.md`.

---

# Purpose

This document defines how the Decision Intelligence Engine interacts with GitHub.

GitHub is not just a code repository.

GitHub is the execution management system for AI-generated projects.

The AI system should be able to transform:

```
Idea

↓

Architecture

↓

Roadmap

↓

Milestones

↓

Issues

↓

Implementation
```

inside GitHub automatically.

---

# Core Principle

The AI should create a professional engineering environment.

A generated repository should look like a senior engineering team created it.

It must include:

- proper repository structure
- documentation
- milestones
- labels
- project board
- issues
- priorities
- dependencies
- contribution guidelines

---

# GitHub Workflow

Complete flow:

```
User approves project creation

↓

Create GitHub repository

↓

Initialize repository

↓

Generate documentation

↓

Create labels

↓

Create milestones

↓

Create GitHub Project

↓

Generate roadmap

↓

Generate issues

↓

Assign dependencies

↓

Ready for development
```

---

# Repository Creation

The GitHub Executor creates:

Repository

README

.gitignore

LICENSE

CONTRIBUTING.md

docs/

project files

---

# Repository Configuration

Default settings:

```
Visibility:

User choice

Default branch:

main

Issues:

Enabled

Projects:

Enabled

Wiki:

Disabled

Discussions:

Optional
```

---

# Repository Metadata

Generate:

Name

Description

Topics

Homepage

About section

Example:

```
Name:

decision-intelligence


Description:

Decision Intelligence Engine —
automatically assembles expert councils,
debates, and returns high-quality decisions.


Topics:

ai

agents

software-engineering

automation

typescript

```

---

# Initial Files

Every project starts with:

```
README.md

PROJECT.md

ARCHITECTURE.md

DESIGN.md

STACK.md

ROADMAP.md

DECISIONS.md

CONTRIBUTING.md

CHANGELOG.md
```

---

# Branch Strategy

Default:

```
main
```

Development:

```
develop
```

Feature branches:

```
feature/<issue-number>-<name>
```

Bug fixes:

```
fix/<issue-number>-<name>
```

---

# Commit Rules

AI-generated commits must follow:

```
type(scope): description
```

Examples:

```
feat(auth): add authentication flow

fix(api): handle invalid requests

docs(readme): update setup instructions

refactor(db): simplify queries
```

---

# Pull Request Rules

Every PR should include:

Title

Summary

Changes

Testing

Related issue

Risk assessment

---

Example:

```
## Summary

Implemented user authentication.


## Changes

- Added Better Auth
- Created user schema
- Added login UI


## Testing

npm test


## Related

Closes #15
```

---

# Labels

Create standard labels.

---

# Type Labels

```
feature

bug

documentation

refactor

security

performance

testing

research
```

---

# Priority Labels

```
priority-critical

priority-high

priority-medium

priority-low
```

---

# Area Labels

```
frontend

backend

database

devops

ai

design

infrastructure
```

---

# Status Labels

```
blocked

needs-review

ready

in-progress

completed
```

---

# Milestones

Milestones represent roadmap phases.

Example:

```
MVP

Beta

Public Launch

Growth

Scale
```

---

# Milestone Structure

Each milestone contains:

Goal

Description

Success criteria

Issues

Deadline

---

Example:

```
Milestone:

MVP

Goal:

Validate core product.


Success Criteria:

- Users can create projects
- Council can make decisions
- Reports generated

```

---

# GitHub Projects

Create a Kanban board.

Columns:

```
Backlog

↓

Ready

↓

In Progress

↓

Review

↓

Testing

↓

Done
```

---

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

---

# Roadmap Integration

The roadmap becomes GitHub milestones.

Example:

```
ROADMAP.md

↓

Milestones

↓

Issues

↓

Execution
```

---

# Automatic Issue Updates

The AI can update issues.

Examples:

When implementation starts:

Add:

```
Status:
In Progress
```

When blocked:

Add:

```
Blocked by:
#25
```

When complete:

Add:

```
Completed

Test results

Documentation updated
```

---

# AI Development Loop

Future workflow:

```
Select next issue

↓

Analyze issue

↓

Council review

↓

Create implementation plan

↓

Human approval

↓

Code

↓

Run tests

↓

Create PR

↓

Review

↓

Merge
```

---

# GitHub Permissions

Minimum permissions:

Repository:

Read/write

Issues:

Read/write

Projects:

Read/write

Pull requests:

Read/write

Contents:

Read/write

Dangerous actions require approval.

---

# Human Approval Required

Before:

Create repository

Delete repository

Merge PR

Push to main

Change permissions

Delete branches

---

# Repository Health Monitoring

The AI should monitor:

Open issues

Failed builds

Dependencies

Security alerts

Technical debt

Documentation gaps

---

# Future Features

Phase 2:

Automatic PR creation

Code review agents

Issue prioritization

Phase 3:

Autonomous feature development

Bug fixing agents

Continuous refactoring

Phase 4:

Complete AI engineering team

---

# Golden Rule

GitHub should become the external memory and execution system of the AI engineering organization.

Every decision becomes documentation.

Every plan becomes an issue.

Every action becomes traceable.
