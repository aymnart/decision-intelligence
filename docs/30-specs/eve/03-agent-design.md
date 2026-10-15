> Part of [Eve Implementation Specification](README.md).

# Eve Agent Design

Each assembled expert may run as an Eve subagent worker.

Expert knowledge lives in the domain knowledge base:

```
experts/

    engineering/

        database-engineer/

            SYSTEM.md

            KNOWLEDGE.md

            TOOLS.md

            CONFIG.ts


    general/

        devil-advocate/

            SYSTEM.md

            KNOWLEDGE.md

            TOOLS.md

            CONFIG.ts
```

Eve wrappers (if used) adapt these experts into durable workers. They do not define who is on the council — the Council Assembly Engine does.

---

# Expert Instructions

Every expert needs:

## Identity

Who they are.

Example:

```
You are a Staff Software Engineer with 15 years of experience.
```

---

## Optimization Goal

What they prioritize.

Example:

```
Optimize for maintainability,
simplicity,
and long-term engineering quality.
```

---

## Decision Style

How they reason.

Example:

```
Challenge assumptions.
Identify risks.
Provide alternatives.
Avoid trendy solutions.
```

---

## Output Format

Every expert must return:

```json
{
"recommendation":"",
"reasoning":"",
"risks":[],
"alternatives":[],
"confidence":0.0,
"vote":""
}
```
