<!-- Template: Used by /create-api-rules → .cursor/rules/api/RULE.md -->
---
description: Backend API design patterns and conventions
globs:
  - "**/api/**/*.ts"
  - "**/server/**/*.ts"
  - "**/routes/**/*.ts"
---

# API Design Patterns

## Philosophy

Build APIs that are **consistent, predictable, and self-documenting**. Prioritize clear error messages and proper status codes.

## Request Validation

Always validate inputs at the API boundary:

```typescript
const schema = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});

const result = schema.safeParse(body);
if (!result.success) {
  return Response.json(
    { error: 'Validation failed', details: result.error.flatten() },
    { status: 400 }
  );
}
```

## Response Structure

### Success

```json
{
  "data": { ... },
  "meta": { "timestamp": "2024-01-15T10:00:00Z" }
}
```

### Error

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Email is required",
    "details": { ... }
  }
}
```

## Status Codes

| Code | Usage |
|------|-------|
| 200 | Success (GET, PUT, PATCH) |
| 201 | Created (POST) |
| 204 | No content (DELETE) |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not found |
| 422 | Validation error |
| 429 | Rate limited |
| 500 | Server error |

## {{API_STYLE}} Conventions

{{IF REST}}
### RESTful URLs

```
GET    /api/users          # List
POST   /api/users          # Create
GET    /api/users/:id      # Get one
PATCH  /api/users/:id      # Update
DELETE /api/users/:id      # Delete
```

- Plural nouns for resources
- Kebab-case for multi-word paths
{{/IF}}

{{IF GraphQL}}
### GraphQL Conventions

- Clear type naming
- Input types for mutations
- DataLoader for N+1 prevention
{{/IF}}

## Authentication

### {{AUTH_PATTERN}}

- Validate tokens/sessions in middleware
- Return 401 for missing auth, 403 for insufficient permissions
- Never expose internal auth errors

## Error Handling

- Never expose stack traces in production
- Log full details server-side
- Return safe, helpful messages to clients

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here -->
