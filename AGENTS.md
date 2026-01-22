# Project Instructions

> Simple agent instructions for this project. For complex projects, use `.cursor/rules/` instead.

## Quick Context

- **Project**: {{PROJECT_NAME}}
- **Stack**: {{PRIMARY_STACK}}
- **Type**: {{web-app | api | cli | library}}

## Architecture

<!-- Only include what's unique to YOUR project -->

- We organize code by {{feature | layer | domain}}
- State management: {{approach}}
- API style: {{REST | GraphQL | tRPC}}

## Key Conventions

<!-- Don't repeat common patterns - Agent knows those. Only YOUR unique conventions. -->

- {{Convention 1}}
- {{Convention 2}}
- {{Convention 3}}

## Internal Tools

<!-- Things Agent won't know about -->

- Use `@/lib/auth` for authentication
- Use `@/lib/api` for API calls
- Design system components in `@/components/ui`

## What to Avoid

- {{Anti-pattern 1}}
- {{Anti-pattern 2}}

## Reference Files

When creating new code, follow patterns in these files:

- Components: `src/components/Button.tsx`
- API routes: `src/app/api/users/route.ts`
- Tests: `src/__tests__/example.test.ts`
