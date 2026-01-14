<!-- Template: Used by /create-infra-rules → .cursor/rules/infrastructure/RULE.md -->
---
description: CI/CD and deployment standards
globs:
  - ".github/**"
  - ".gitlab-ci.yml"
  - "**/Dockerfile"
  - "**/docker-compose*.yml"
---

# Infrastructure Standards

## Philosophy

Infrastructure as code should be reviewable, testable, and reproducible. Automate everything that can be automated. Fail fast in CI, deploy safely to production.

## Environment Configuration

- Environment variables for env-specific config
- No secrets in code or config files
- Validate config at application startup
- Document all required env vars in README

## {{CI_PLATFORM}} Conventions

{{IF github-actions}}
### GitHub Actions

```yaml
.github/
  workflows/
    ci.yml            # Lint, test, build on PR
    deploy.yml        # Deploy on merge to main
  actions/
    setup/            # Reusable setup action
```

**Best Practices:**
- Pin action versions with SHA
- Cache dependencies
- Use environments for deployment protection
- Fail fast on PR checks
{{/IF}}

{{IF gitlab-ci}}
### GitLab CI

**Best Practices:**
- Stages: lint, test, build, deploy
- Use `extends` for job templates
- Cache between jobs
- Use rules for conditional jobs
{{/IF}}

## Deployment Safety

- Feature flags for gradual rollout
- Health checks / readiness probes
- Rollback procedures documented
- Database migrations run before deploy

## Container Best Practices

```dockerfile
# Multi-stage builds
FROM node:20-alpine AS builder
# ...

FROM node:20-alpine
# Run as non-root user
USER node
# Health check
HEALTHCHECK CMD curl -f http://localhost:3000/health
```

## Secrets Management

- Use secret managers (not env vars in CI config)
- Least privilege for CI/CD service accounts
- Rotate secrets regularly
- Audit secret access

## Observability

- Structured JSON logs
- Correlation ID propagation
- Define SLOs/SLIs
- Alert on symptoms, not causes

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here -->
