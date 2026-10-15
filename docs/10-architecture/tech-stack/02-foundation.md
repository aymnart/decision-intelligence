> Part of [Tech Stack](README.md).

# Monorepo

## Technology

Turborepo

Reason:

- Excellent TypeScript support
- Incremental builds
- Remote caching
- Package isolation
- Industry standard

Alternative Considered

Nx

Reason Rejected

- More complex
- Higher learning curve
- Unnecessary for MVP

---

# Runtime

## Technology

Node.js 24 LTS

Reason

- Mature ecosystem
- Excellent package compatibility
- Long-term support
- Stable

Alternative

Bun

Reason Rejected

Still evolving.

May become an optional runtime later.

---

# Language

TypeScript

Configuration

Strict Mode

Rules

- strict=true
- no implicit any
- exact optional property types
- no unchecked indexed access

Reason

The project relies heavily on structured AI outputs.

Maximum type safety is mandatory.

---

# Package Manager

pnpm

Reason

- Fastest installs
- Efficient storage
- Excellent workspace support
- Preferred by Turborepo

Alternatives

npm

Yarn

Rejected because pnpm provides better monorepo support.
