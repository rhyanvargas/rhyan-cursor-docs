<!-- Template: Used by /create-general-rules → .cursor/rules/testing/RULE.md -->
---
description: Testing strategy and patterns for reliable test suites
---

# Testing Strategy

## Philosophy

Tests exist to **give confidence when making changes**. Write tests that catch real bugs, not tests that break on every refactor. Test behavior, not implementation.

## Testing Pyramid

Prioritize tests in this order (more at bottom, fewer at top):

```
       /\
      /  \     E2E Tests (few, slow, high confidence)
     /----\
    /      \   Integration Tests (moderate)
   /--------\
  /          \ Unit Tests (many, fast, focused)
 /____________\
```

### {{TESTING_STRATEGY}}

{{IF unit-first}}
**Focus on unit tests**: Fast feedback, high coverage of business logic. Use integration tests for critical paths.
{{/IF}}

{{IF integration-first}}
**Focus on integration tests**: Test modules working together. Unit tests for complex algorithms only.
{{/IF}}

{{IF e2e-first}}
**Focus on E2E tests**: Test complete user workflows. Fewer but higher confidence tests.
{{/IF}}

## Test Structure: Arrange-Act-Assert

Every test should follow the AAA pattern:

```typescript
describe('calculateDiscount', () => {
  it('should apply 10% discount for orders over $100', () => {
    // Arrange - set up test data
    const order = { total: 150, items: [] };
    
    // Act - perform the action
    const result = calculateDiscount(order);
    
    // Assert - verify the outcome
    expect(result.discount).toBe(15);
    expect(result.finalTotal).toBe(135);
  });
});
```

## Test Naming

Use descriptive names that explain behavior:

```typescript
// Good - describes behavior
it('should return null when user is not found')
it('should throw ValidationError for invalid email')

// Bad - describes implementation
it('calls findById')
it('returns error')
```

## What to Test

- Business logic thoroughly
- Edge cases and error paths
- Critical user paths
- API contracts

## What NOT to Test

- Framework internals
- Trivial code (getters/setters)
- Implementation details
- Third-party libraries

## Mocking Guidelines

### What to Mock

- External APIs and services
- Database calls (for unit tests)
- Time and dates
- Random values

### What NOT to Mock

- The code under test
- Simple utility functions
- Types and interfaces

## Test Data

Use factories for consistent test data:

```typescript
function createTestUser(overrides: Partial<User> = {}): User {
  return {
    id: 'test-user-id',
    email: 'test@example.com',
    name: 'Test User',
    ...overrides,
  };
}
```

## Coverage Guidelines

- Aim for 80%+ coverage on business logic
- Don't chase 100%—focus on meaningful tests
- Exclude from coverage: types, trivial code
- Cover edge cases and error paths

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Specific testing libraries/frameworks
- Custom test utilities
- CI integration requirements
-->
