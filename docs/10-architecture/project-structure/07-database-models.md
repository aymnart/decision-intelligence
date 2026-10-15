> Part of [Project Structure Specification](README.md).

# Database Models

The schema source of truth is [Database Design](../database-design.md). This page is the original sketch, including post-MVP entities.

Core entities:

---

# Project

```
id

name

description

status

createdAt
```

---

# Decision

```
id

projectId

title

category

impact

status

result

confidence

createdAt
```

---

# ExpertOpinion

```
id

decisionId

expertId

reasoning

vote

confidence
```

---

# Debate

```
id

decisionId

round

messages
```

---

# Artifact

```
id

projectId

type

content

version
```

---

# Workflow

```
id

type

status

currentStep

state
```

---

# Execution

```
id

workflowId

action

status

result
```
