# Security Rule Template

> **Usage**: Used by `/create-general-rules` command. Creates `.cursor/rules/security/RULE.md`.

---

```yaml
---
description: Security best practices for applications
alwaysApply: true
---
```

# Security Practices

## Philosophy

Security is not optional. Build security into the development process from day one. Assume inputs are malicious, outputs are monitored, and secrets will leak if not protected.

## Input Validation

### Validate at Boundaries

All external input must be validated before use:

```typescript
const schema = z.object({
  email: z.string().email(),
  age: z.number().int().min(0).max(150),
});

const result = schema.safeParse(requestBody);
if (!result.success) {
  return Response.json({ error: 'Invalid input' }, { status: 400 });
}
```

### Sanitization

- Escape HTML output to prevent XSS
- Use parameterized queries for database access
- Sanitize file uploads (validate type, size, name)

## SQL Injection Prevention

Never concatenate user input into queries:

```typescript
// BAD - SQL injection vulnerability
const query = `SELECT * FROM users WHERE email = '${email}'`;

// GOOD - Parameterized query
const user = await prisma.user.findUnique({ where: { email } });
```

## XSS Prevention

- Framework escapes by default—trust it
- Be careful with `dangerouslySetInnerHTML` or equivalent
- Sanitize user content before rendering as HTML
- Configure Content Security Policy headers

## Secrets Management

- Never commit secrets to version control
- Use `.env.local` for local development (add to `.gitignore`)
- Use secret management services in production
- Validate environment variables at startup

```typescript
const envSchema = z.object({
  DATABASE_URL: z.string().url(),
  JWT_SECRET: z.string().min(32),
});
```

## Authentication

### {{AUTH_PATTERN}}

{{IF JWT}}
**JWT Best Practices:**
- Use short expiration times (15 minutes for access tokens)
- Implement refresh token rotation
- Store refresh tokens in HTTP-only cookies
- Include minimal claims in JWT
{{/IF}}

{{IF session}}
**Session Best Practices:**
- Use secure, HTTP-only cookies
- Implement session expiration
- Rotate session tokens after authentication
- Invalidate sessions on logout
{{/IF}}

### Password Handling

```typescript
// NEVER store plaintext passwords
import bcrypt from 'bcrypt';
const SALT_ROUNDS = 12;

async function hashPassword(password: string): Promise<string> {
  return bcrypt.hash(password, SALT_ROUNDS);
}
```

## Authorization

### Principle of Least Privilege

Users should have only the permissions they need:

```typescript
async function updateUser(userId: string, data: UpdateData, session: Session) {
  if (session.user.id !== userId && session.user.role !== 'admin') {
    throw new ForbiddenError('Cannot update other users');
  }
  // ...
}
```

## Common Protections

- **CSRF**: Use SameSite cookies, CSRF tokens for forms
- **Rate Limiting**: Protect login, password reset endpoints
- **Security Headers**: X-Content-Type-Options, X-Frame-Options, etc.
- **HTTPS**: Always in production, redirect HTTP

## Dependency Security

- Run `npm audit` regularly
- Keep dependencies updated
- Review new dependencies before adding

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Specific compliance requirements (HIPAA, SOC2, etc.)
- Custom security headers
- Audit logging requirements
-->
