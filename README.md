# Cursor AI Grounding Kit

A minimal, best-practices-aligned starter for grounding Cursor's AI agent with project-specific context.

> **Philosophy**: Per [Cursor's docs](https://cursor.com/docs/context/rules.md), *"Start simple. Add rules only when you notice Agent making the same mistake repeatedly."* Agent already knows common patterns—your rules should focus on what makes YOUR project unique.

## Quick Start

### Option 1: Minimal (Recommended)

Copy just what you need:

```bash
# Copy to your project
cp AGENTS.md your-project/
# OR
mkdir -p your-project/.cursor/rules
cp .cursor/templates/rules/project.mdc your-project/.cursor/rules/
```

Then fill in YOUR project-specific patterns.

### Option 2: Extended (Enterprise/Large Teams)

For comprehensive coverage, use the extended templates:

```bash
cp -r .cursor/ your-project/
# Run commands to generate rules
/init-project-config
/create-general-rules
```

---

## Choosing Your Approach

| Approach | When to Use | Rules Count |
|----------|-------------|-------------|
| **Minimal** | Solo/small teams, new projects, rapid iteration | 1 rule + AGENTS.md |
| **Extended** | Enterprise, large teams, compliance requirements | 10+ rules |

### What NOT to Include in Rules

Per [Cursor best practices](https://cursor.com/docs/context/rules.md):

- ❌ SOLID, KISS, DRY (Agent knows these)
- ❌ TypeScript/React/Python basics (Agent knows frameworks)
- ❌ Conventional commits (Agent knows git)
- ❌ REST/GraphQL conventions (Agent knows APIs)
- ❌ Testing pyramid (Agent knows testing)

### What TO Include

- ✅ YOUR folder structure and architecture decisions
- ✅ Internal libraries Agent doesn't know about
- ✅ Team conventions that DIFFER from defaults
- ✅ Project-specific security requirements
- ✅ References to canonical example files

---

## Project Structure

```
.cursor/
├── commands/                    # Slash command definitions
│   ├── init-project-config.md
│   ├── create-general-rules.md
│   ├── analyze-codebase.md
│   └── create-feature-spec.md
├── templates/
│   ├── rules/
│   │   └── project.mdc          # ⭐ MINIMAL: One focused rule
│   ├── extended/
│   │   └── rules/               # 📚 EXTENDED: Comprehensive templates
│   │       ├── general-rule.md
│   │       ├── typescript-rule.md
│   │       ├── react-rule.md
│   │       └── ...
│   ├── project-config.yaml
│   └── feature-spec-template.md
AGENTS.md                        # ⭐ MINIMAL: Simple alternative
```

---

## Minimal Approach

### Using `AGENTS.md`

The simplest option. Place in your project root:

```markdown
# Project Instructions

## Architecture
- We organize code by feature, not layer
- State: Zustand for global, useState for local

## Internal Tools
- Use `@/lib/auth` for authentication
- Use `@/lib/api` for API calls

## What to Avoid
- Don't use Redux (we use Zustand)
- Don't create new API clients (use @/lib/api)

## Reference Files
- Components: `src/components/Button.tsx`
- API routes: `src/app/api/users/route.ts`
```

### Using `project.mdc`

For more control, use the single rule file at `.cursor/rules/project.mdc`:

```markdown
---
description: Project-specific standards
alwaysApply: true
---

# Project Standards

## Architecture
<!-- YOUR specific decisions only -->

## Internal Libraries
- **Auth**: Use `@/lib/auth` — see @lib/auth/README.md
- **API Client**: Use `@/lib/api` wrapper

## Reference Files
@src/components/Button.tsx
@src/app/api/users/route.ts
```

---

## Extended Approach

For teams needing comprehensive documentation, use templates in `.cursor/templates/extended/rules/`.

### Commands

| Command | Purpose |
|---------|---------|
| `/init-project-config` | Capture architecture decisions |
| `/create-general-rules` | Generate 5 framework-agnostic rules |
| `/create-lang-rules` | TypeScript/Python rules |
| `/create-frontend-rules` | React patterns |
| `/create-api-rules` | API standards |
| `/create-infra-rules` | CI/CD standards |
| `/analyze-codebase` | Audit code against rules |
| `/create-feature-spec` | Generate feature specs |

### Extended Templates

| Template | Lines | Coverage |
|----------|-------|----------|
| `general-rule.md` | 162 | SOLID, naming, error handling |
| `typescript-rule.md` | 114 | Type safety patterns |
| `react-rule.md` | 100 | Component patterns |
| `python-rule.md` | 81 | Python idioms |
| `api-rule.md` | 119 | REST/GraphQL patterns |
| `security-rule.md` | 141 | Security best practices |
| `testing-rule.md` | 146 | Testing strategy |
| `documentation-rule.md` | 141 | Doc standards |
| `git-rule.md` | 156 | Git workflow |
| `infrastructure-rule.md` | 97 | CI/CD patterns |

---

## Template Placeholder System

Extended templates use placeholders processed by the AI:

### Simple Placeholders

```markdown
## {{API_STYLE}} Conventions
```

Becomes `## REST Conventions` when config has `api_style: REST`.

### Conditional Blocks

```markdown
{{IF REST}}
### RESTful URLs
- Use plural nouns for resources
{{/IF}}
```

Only included when config matches.

### Available Placeholders

| Placeholder | Options |
|-------------|---------|
| `{{API_STYLE}}` | `REST`, `GraphQL`, `tRPC` |
| `{{AUTH_PATTERN}}` | `JWT`, `session`, `OAuth-only` |
| `{{TESTING_STRATEGY}}` | `unit-first`, `integration-first`, `e2e-first` |
| `{{CI_PLATFORM}}` | `github-actions`, `gitlab-ci` |

---

## Best Practices (from Cursor Docs)

> *"Keep rules under 500 lines. Split large rules into multiple, composable rules."*

> *"Provide concrete examples or referenced files. Avoid vague guidance."*

> *"Reference files instead of copying their contents—this keeps rules short and prevents them from becoming stale."*

### Do

- ✅ Reference canonical example files with `@filename.ts`
- ✅ Focus on patterns you use frequently
- ✅ Update rules when Agent makes repeated mistakes
- ✅ Check rules into git for team sharing

### Don't

- ❌ Copy entire style guides (use a linter)
- ❌ Document every possible command
- ❌ Add edge case instructions
- ❌ Duplicate what's in your codebase

---

## Contributing

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

[MIT](LICENSE) © Rhyguy
