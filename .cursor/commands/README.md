# Cursor Commands

Custom commands for project setup, analysis, and documentation.

## Quick Reference

| Command | Purpose |
|---------|---------|
| `/init-project-config` | Capture architecture decisions → config file |
| `/create-general-rules` | Framework-agnostic standards (5 rules) |
| `/create-lang-rules` | Language-specific rules |
| `/create-frontend-rules` | UI/component standards |
| `/create-api-rules` | Backend/API standards |
| `/create-infra-rules` | CI/CD and deployment |
| `/analyze-codebase` | Audit code against rules |
| `/create-feature-spec` | Generate feature specification |

## Workflow

```
1. /init-project-config       # Answer questions → config file
2. /create-general-rules      # Core standards
3. /create-lang-rules         # Language rules
4. /create-frontend-rules     # If building UI
5. /create-api-rules          # If building APIs
```

## How It Works

**Commands** define workflow and reference templates.  
**Templates** define content with `{{placeholders}}`.  
**Config** stores answers for placeholder replacement.

```
.cursor/
├── commands/           # Workflow (this folder)
├── templates/          # Content templates
│   ├── project-config.yaml
│   └── rules/*.md
└── rules/              # Generated output
```

## Templates

| Template | Used By |
|----------|---------|
| @.cursor/templates/project-config.yaml | `/init-project-config` |
| @.cursor/templates/rules/general-rule.md | `/create-general-rules` |
| @.cursor/templates/rules/git-rule.md | `/create-general-rules` |
| @.cursor/templates/rules/security-rule.md | `/create-general-rules` |
| @.cursor/templates/rules/testing-rule.md | `/create-general-rules` |
| @.cursor/templates/rules/documentation-rule.md | `/create-general-rules` |
| @.cursor/templates/rules/typescript-rule.md | `/create-lang-rules` |
| @.cursor/templates/rules/python-rule.md | `/create-lang-rules` |
| @.cursor/templates/rules/react-rule.md | `/create-frontend-rules` |
| @.cursor/templates/rules/api-rule.md | `/create-api-rules` |
| @.cursor/templates/rules/infrastructure-rule.md | `/create-infra-rules` |
| @.cursor/templates/feature-spec-template.md | `/create-feature-spec` |

## Customization

Generated rules include `<!-- PROJECT-SPECIFIC -->` sections for your additions.
