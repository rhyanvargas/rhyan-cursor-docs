<!-- Template: Used by /create-lang-rules typescript → .cursor/rules/typescript/RULE.md -->
---
description: TypeScript best practices and type safety patterns
globs:
  - "**/*.ts"
  - "**/*.tsx"
---

# TypeScript Best Practices

## Philosophy

TypeScript's value comes from its type system. Use it fully—don't escape hatch with `any`. Types are documentation that the compiler verifies.

## Strict Configuration

Always use strict TypeScript settings:

```json
{
  "compilerOptions": {
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  }
}
```

## Avoiding `any`

- Use `unknown` for truly unknown types, then narrow
- Use generics for flexible but type-safe code
- Use `Record<string, unknown>` for object dictionaries

```typescript
// BAD
function parse(input: any): any { ... }

// GOOD
function parse<T>(input: unknown): T { ... }
```

## Interface vs Type

### Use `interface` for:
- Object shapes that may be extended
- Public API contracts

### Use `type` for:
- Unions and intersections
- Mapped types and utility types
- Function signatures

## Discriminated Unions

Use for type-safe state management:

```typescript
type AsyncState<T> =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: T }
  | { status: 'error'; error: Error };
```

## Null Safety

- Use `T | null` for intentionally nullable values
- Use optional chaining (`?.`) for safe property access
- Use nullish coalescing (`??`) for defaults
- Avoid non-null assertions (`!`) except in tests

## Generics

- Use meaningful names (`TUser`, not just `T`)
- Add constraints to catch errors early
- Don't over-genericize—start concrete

## Const Objects Over Enums

```typescript
// Prefer this
const Status = {
  Pending: 'pending',
  Active: 'active',
} as const;
type Status = typeof Status[keyof typeof Status];

// Over enums (runtime overhead and quirks)
```

## Explicit Return Types

Add for public/exported functions:

```typescript
async function fetchUser(id: string): Promise<User | null> {
  // ...
}
```

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Custom utility types
- Specific type conventions
- Linting rules
-->
