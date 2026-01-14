# Documentation Rule Template

> **Usage**: Used by `/create-general-rules` command. Creates `.cursor/rules/documentation/RULE.md`.

---

```yaml
---
description: Documentation requirements and standards
---
```

# Documentation Standards

## Philosophy

Documentation should reduce friction for future developers (including yourself). Document decisions, not just code. Keep docs close to code so they stay in sync.

## When to Document

### Always Document

- Public APIs and their contracts
- Non-obvious business logic
- Architectural decisions (ADRs)
- Setup and deployment procedures
- Environment variables and configuration

### Don't Over-Document

- Obvious code (self-documenting)
- Implementation details that change frequently
- Anything the type system already describes

## README Structure

Every project should have a README with:

```markdown
# Project Name

Brief description of what this project does.

## Quick Start

Steps to get running in <5 minutes.

## Development Setup

Detailed setup instructions.

## Architecture

Overview or link to architecture docs.

## Contributing

How to contribute, coding standards link.
```

## Inline Documentation

### JSDoc / Docstrings

Document public functions with:

```typescript
/**
 * Calculates the discount for an order based on total value.
 * 
 * @param order - The order to calculate discount for
 * @returns The discount amount in cents
 * @throws {ValidationError} If order total is negative
 */
function calculateDiscount(order: Order): number {
  // ...
}
```

### Code Comments

- Explain **why**, not **what**
- Link to tickets for workarounds
- No commented-out code

{{IF documentation includes ADRs}}
## Architecture Decision Records (ADRs)

Document significant decisions in `docs/adr/`:

```markdown
# ADR-001: Use PostgreSQL for primary database

## Status
Accepted

## Context
We need a relational database for our user and order data...

## Decision
We will use PostgreSQL...

## Consequences
- Pros: ACID compliance, JSON support...
- Cons: Operational complexity...
```

### ADR Guidelines

- Number sequentially (ADR-001, ADR-002...)
- Never delete, only supersede
- Include date and status
- Keep concise but complete
{{/IF}}

## API Documentation

- Document all public endpoints
- Include request/response examples
- Document error responses
- Keep in sync with implementation (or generate from code)

## Keeping Docs Current

- Review docs in code reviews
- Link docs to related code files
- Use `@see` references for related docs
- Delete outdated documentation

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Documentation tools (Storybook, Swagger, etc.)
- Wiki or external doc requirements
- Specific doc review processes
-->
