# Cursor Commands

Custom commands for project setup, analysis, and rule generation.

## Quick Reference

| Command | Purpose | Recommended For |
|---------|---------|-----------------|
| `/quick-start` | **Create minimal, focused rules** | ⭐ Most projects |
| `/init-project-config` | Capture architecture decisions → config | Extended setup |
| `/create-general-rules` | Framework-agnostic standards (5 rules) | Large teams |
| `/create-lang-rules` | Language-specific rules | Custom conventions |
| `/create-frontend-rules` | UI/component standards | Custom design systems |
| `/create-api-rules` | Backend/API standards | Custom API patterns |
| `/create-infra-rules` | CI/CD and deployment | Custom pipelines |
| `/analyze-codebase` | Audit code against rules | Code review |
| `/create-feature-spec` | Generate feature specification | Planning |

## Recommended Workflow

### Minimal (Most Projects)

```bash
/quick-start              # Creates ONE focused rule file
```

Done! Add more rules only when Agent makes repeated mistakes.

### Extended (Large Teams)

```bash
/init-project-config      # Answer architecture questions → config file
/create-general-rules     # 5 framework-agnostic rules
/create-lang-rules        # Language-specific rules (if needed)
/create-frontend-rules    # Frontend rules (if needed)
/create-api-rules         # API rules (if needed)
```

## Project Structure

```
.cursor/
├── commands/                    # This folder
│   ├── quick-start.md          # ⭐ Recommended starting point
│   ├── init-project-config.md
│   ├── create-general-rules.md
│   └── ...
├── templates/
│   ├── rules/
│   │   └── project.mdc         # ⭐ Minimal template
│   ├── extended/
│   │   └── rules/              # 📚 Comprehensive templates
│   ├── project-config.yaml
│   └── feature-spec-template.md
```

## Philosophy

Per [Cursor's documentation](https://cursor.com/docs/context/rules.md):

> *"Start simple. Add rules only when you notice Agent making the same mistake repeatedly. Don't over-optimize before you understand your patterns."*

Agent already knows:
- SOLID, KISS, DRY principles
- TypeScript, React, Python best practices
- REST/GraphQL conventions
- Conventional commits
- Testing patterns

**Your rules should focus on:**
- YOUR project's unique architecture
- Internal libraries Agent doesn't know
- Patterns that DIFFER from common conventions
- References to canonical example files

## Templates

### Minimal Templates

| Template | Used By | Purpose |
|----------|---------|---------|
| `templates/rules/project.mdc` | `/quick-start` | Single focused rule |
| `AGENTS.md` (root) | Direct use | Simplest option |

### Extended Templates

| Template | Used By | Lines |
|----------|---------|-------|
| `templates/extended/rules/general-rule.md` | `/create-general-rules` | 162 |
| `templates/extended/rules/typescript-rule.md` | `/create-lang-rules` | 114 |
| `templates/extended/rules/react-rule.md` | `/create-frontend-rules` | 100 |
| `templates/extended/rules/python-rule.md` | `/create-lang-rules` | 81 |
| `templates/extended/rules/api-rule.md` | `/create-api-rules` | 119 |
| `templates/extended/rules/security-rule.md` | `/create-general-rules` | 141 |
| `templates/extended/rules/testing-rule.md` | `/create-general-rules` | 146 |
| `templates/extended/rules/documentation-rule.md` | `/create-general-rules` | 141 |
| `templates/extended/rules/git-rule.md` | `/create-general-rules` | 156 |
| `templates/extended/rules/infrastructure-rule.md` | `/create-infra-rules` | 97 |

## Customization

All templates include `<!-- PROJECT-SPECIFIC -->` sections for your additions.
