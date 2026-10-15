> Part of [Tech Stack](README.md).

# Database

PostgreSQL

Reason

- ACID
- Mature
- Excellent tooling
- JSON support
- Full-text search

Alternatives

MongoDB

Rejected

The system is relational.

---

# ORM

Drizzle ORM

Reason

- SQL-first
- Type-safe
- Lightweight

Alternative

Prisma

Rejected

- More abstraction
- Less SQL control
- Larger client

---

# Authentication

Better Auth

Reason

- TypeScript native
- Modern
- Self-host friendly

---

# Background Jobs

Inngest

Responsibilities

- retries
- scheduling
- async jobs
- long-running workflows

Reason

Excellent TypeScript experience.

Simple integration.

---

# Caching

Redis

Technology

Upstash Redis

Uses

- sessions
- AI cache
- rate limiting
- temporary workflows

---

# Object Storage

Cloudflare R2

Uses

- generated files
- reports
- diagrams
- uploads

Reason

No egress fees.

---

# Search

MVP

PostgreSQL Full Text Search

Future

OpenSearch

Reason

Avoid unnecessary infrastructure.

---

# Vector Database

None

Reason

Do not introduce vector search until:

- enough historical decisions exist
- semantic retrieval is required

Future candidates

- pgvector
- Pinecone
- Weaviate
