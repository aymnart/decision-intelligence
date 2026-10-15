> Part of [GitHub Automation Specification](README.md).

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
