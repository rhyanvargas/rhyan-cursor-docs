<!-- Template: Used by /create-general-rules → .cursor/rules/general/RULE.md -->
---
description: Core coding principles and clean code conventions
alwaysApply: true
---

# General Coding Principles

## Philosophy

Write code that is **boring, predictable, and maintainable**. Optimize for readability and long-term maintainability over cleverness. Code is read far more often than it is written.

## Core Principles

### SOLID Principles

- **Single Responsibility**: Each module, class, or function should have one reason to change
- **Open/Closed**: Open for extension, closed for modification. Use composition and interfaces
- **Liskov Substitution**: Subtypes must be substitutable for their base types
- **Interface Segregation**: Prefer many specific interfaces over one general-purpose interface
- **Dependency Inversion**: Depend on abstractions, not concretions. Inject dependencies

### Keep It Simple

- **KISS**: Choose the simplest solution that works. Avoid premature optimization
- **YAGNI**: Don't build features until they're actually needed
- **DRY**: Don't repeat yourself, but don't over-abstract. Rule of three: abstract on the third occurrence

## Code Organization

### {{ORGANIZATION_PATTERN}} Structure

{{IF feature-based}}
Organize code by feature/domain, not by technical layer:

```
src/
  features/
    users/
      components/
      hooks/
      api/
      types.ts
      index.ts          # Public API (barrel file)
    orders/
      ...
  shared/
    components/         # Used by 2+ features
    utils/
    hooks/
```

**Benefits**: Colocation, scalability, team ownership, easy refactoring
{{/IF}}

{{IF layer-based}}
Organize code by technical layer:

```
src/
  components/
  hooks/
  services/
  utils/
  types/
```

**Note**: Consider migrating to feature-based when complexity grows (>20 components)
{{/IF}}

### Module Boundaries

- Each feature module should have a clear public API (index.ts barrel file)
- Avoid circular dependencies between modules
- Shared code goes in `shared/` only when used by 2+ features

## Naming Conventions

### General Rules

- Use descriptive, intention-revealing names
- Avoid abbreviations except for widely understood ones (id, url, api)
- Boolean variables: use `is`, `has`, `should`, `can` prefixes
- Functions: use verb phrases (`getUserById`, `validateInput`, `calculateTotal`)
- Constants: use SCREAMING_SNAKE_CASE for true constants

### File Naming

- Components: PascalCase (`UserProfile.tsx`)
- Utilities/hooks: camelCase (`useAuth.ts`, `formatDate.ts`)
- Types/interfaces: PascalCase (`UserTypes.ts`)
- Test files: `*.test.ts` or `*.spec.ts`

## Error Handling

### {{ERROR_STRATEGY}}

{{IF result-types}}
Use Result types for expected failures, exceptions for unexpected:

```typescript
type Result<T, E = Error> = { success: true; data: T } | { success: false; error: E };

// Use exceptions for unexpected failures
throw new Error('Descriptive message with context');
```
{{/IF}}

{{IF exceptions}}
Use exceptions with proper error hierarchies:

```typescript
class AppError extends Error {
  constructor(public code: string, message: string) {
    super(message);
  }
}
```
{{/IF}}

### Error Principles

- Validate inputs at system boundaries (API endpoints, user input)
- Throw errors early rather than propagating invalid state
- Never silently swallow errors
- Always include context in error messages

## Comments

### When to Comment

- Explain **why**, not **what** (code should be self-documenting for "what")
- Document non-obvious business rules
- Explain workarounds with links to issues/tickets
- Add JSDoc for public APIs

### When NOT to Comment

- Don't comment obvious code
- Don't leave commented-out code (use version control)
- Don't write TODOs without ticket references

## Dependencies

- Prefer well-maintained packages with active communities
- Check bundle size impact for frontend dependencies
- Avoid dependencies for trivial functionality
- Pin versions and use lockfiles
- Regular security audits (`npm audit`, `pnpm audit`)

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Domain-specific naming conventions
- Custom error types
- Specific architectural decisions
-->
