# Git Rule Template

> **Usage**: Used by `/create-general-rules` command. Creates `.cursor/rules/git/RULE.md`.

---

```yaml
---
description: Git workflow and commit conventions
---
```

# Git Workflow

## Philosophy

Git history should tell the story of how the project evolved. Clear commits and branches make code review easier and debugging with `git bisect` possible.

## Conventional Commits

Use conventional commit format for clear, parseable history:

```
<type>(<scope>): <subject>

[optional body]

[optional footer]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no code change |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf` | Performance improvement |
| `test` | Adding or updating tests |
| `chore` | Build process, dependencies, tooling |
| `ci` | CI configuration |
| `revert` | Reverting a previous commit |

### Examples

```bash
feat(auth): add OAuth2 login with Google
fix(api): handle null response from payment provider
docs(readme): add deployment instructions
refactor(users): extract validation logic to separate module
```

### Breaking Changes

Use `!` or footer for breaking changes:

```bash
feat(api)!: change user endpoint response format

BREAKING CHANGE: User endpoint now returns { data: user } instead of user directly
```

## Branch Naming

```bash
feature/user-authentication
feature/TICKET-123-add-payment-flow
fix/login-redirect-loop
chore/upgrade-dependencies
docs/api-documentation
```

## Branch Strategy

- `main` — Production-ready code, always deployable
- Feature branches from `main`, merged via PR

## Commit Best Practices

### Atomic Commits

Each commit should:
- Represent one logical change
- Leave the codebase in a working state
- Be independently reviewable

### Commit Message Guidelines

**Subject line:**
- Use imperative mood ("add", not "added" or "adds")
- No period at the end
- Max 50 characters
- Capitalize first letter

**Body (when needed):**
- Wrap at 72 characters
- Explain what and why, not how
- Reference issues/tickets

## Pull Request Guidelines

### PR Size

- Keep PRs small and focused (<400 lines preferred)
- Split large features into multiple PRs
- Easier to review = faster to merge

### PR Description

```markdown
## Summary
Brief description of changes

## Changes
- Change 1
- Change 2

## Testing
- [ ] Unit tests pass
- [ ] Manual testing completed

## Related Issues
Fixes #123
```

## Code Review

### As Reviewer

- Review within 24 hours
- Be constructive, suggest solutions
- Approve when "good enough", not perfect
- Use conventional comments: `nit:`, `suggestion:`, `question:`, `issue:`

## Merge Strategy

{{MERGE_STRATEGY}}

- **Squash and Merge** (recommended): Clean linear history
- **Rebase and Merge**: When individual commits are valuable
- **Merge Commit**: For long-running branches

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here:
- Branch protection rules
- Required reviewers
- CI checks required before merge
-->
