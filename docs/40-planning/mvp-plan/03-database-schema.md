> Part of [Decision Intelligence Engine MVP Execution Plan](README.md).

# Database Schema

The schema source of truth is [Database Design](../../10-architecture/database-design.md). This page is the original MVP sketch.

---

# User

```
id

email

createdAt
```

---

# Decision

```
id

userId

title

description

category

impact

status

result

confidence

createdAt
```

---

# Expert

```
id

name

role

prompt

weight
```

---

# Expert Opinion

```
id

decisionId

expertId

reasoning

recommendation

confidence

vote
```

---

# Debate Message

```
id

decisionId

expertId

round

content
```

---

# Consensus

```
id

decisionId

finalDecision

agreement

minorityOpinion

tradeoffs
```
