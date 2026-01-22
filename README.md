# Cursor AI Grounding Kit

A collection of commands, rules, and templates to ground Cursor's AI coding agent with consistent, project-aware context.

## Features

- **Custom Commands** — Reusable `/slash` commands for project setup and analysis
- **Rule Templates** — Pre-built coding standards for TypeScript, React, APIs, security, and more
- **Config-Driven** — Answer questions once, generate consistent rules across your project
- **Extensible** — Add your own rules and commands following the same patterns

## Quick Start

1. Copy the `.cursor/` folder to your project root
2. Run `/init-project-config` to capture your architecture decisions
3. Run the appropriate `/create-*-rules` commands for your stack
4. Start coding with AI that understands your standards

## Commands

| Command | Purpose |
|---------|---------|
| `/init-project-config` | Capture architecture decisions → config file |
| `/create-general-rules` | Framework-agnostic standards (5 rules) |
| `/create-lang-rules` | Language-specific rules (TypeScript, Python) |
| `/create-frontend-rules` | UI/component standards (React, Vue) |
| `/create-api-rules` | Backend/API standards (REST, GraphQL) |
| `/create-infra-rules` | CI/CD and deployment standards |
| `/analyze-codebase` | Audit code against your rules |
| `/create-feature-spec` | Generate feature specifications |

## Project Structure

```
.cursor/
├── commands/           # Slash command definitions
│   ├── init-project-config.md
│   ├── create-general-rules.md
│   ├── create-lang-rules.md
│   ├── create-frontend-rules.md
│   ├── create-api-rules.md
│   ├── create-infra-rules.md
│   ├── analyze-codebase.md
│   └── create-feature-spec.md
├── templates/          # Content templates with {{placeholders}}
│   ├── project-config.yaml
│   ├── feature-spec-template.md
│   └── rules/
│       ├── general-rule.md
│       ├── typescript-rule.md
│       ├── react-rule.md
│       └── ...
└── rules/              # Generated rules (output)
    ├── general/
    ├── typescript/
    └── ...
```

## How It Works

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Commands   │────▶│  Templates  │────▶│    Rules    │
│  (workflow) │     │  (content)  │     │  (output)   │
└─────────────┘     └─────────────┘     └─────────────┘
                           ▲
                           │
                    ┌──────┴──────┐
                    │   Config    │
                    │ (variables) │
                    └─────────────┘
```

1. **Commands** define the workflow and prompt the AI
2. **Config** stores your project decisions (from `/init-project-config`)
3. **Templates** contain rule content with `{{placeholders}}`
4. **Rules** are generated with placeholders replaced by config values

## Template Placeholder System

Templates use a placeholder syntax that the AI agent processes when generating rules.

### Simple Placeholders

Use `{{PLACEHOLDER_NAME}}` for values that come from the project config:

```markdown
## {{API_STYLE}} Conventions

Your API follows {{API_STYLE}} patterns...
```

When the AI processes this with `api_style: REST` in the config, it becomes:

```markdown
## REST Conventions

Your API follows REST patterns...
```

### Conditional Blocks

Use `{{IF condition}}...{{/IF}}` for content that should only appear based on config values:

```markdown
{{IF REST}}
### RESTful URLs
- Use plural nouns for resources
- Use kebab-case for multi-word paths
{{/IF}}

{{IF GraphQL}}
### GraphQL Conventions
- Clear type naming
- Input types for mutations
{{/IF}}
```

The AI agent will:
1. Read the config value (e.g., `api_style: REST`)
2. Include only the matching conditional block
3. Remove the `{{IF}}` / `{{/IF}}` markers

### Available Placeholders

| Placeholder | Config Key | Options |
|-------------|------------|---------|
| `{{ORGANIZATION_PATTERN}}` | `architecture.organization` | `feature-based`, `layer-based`, `domain-driven` |
| `{{API_STYLE}}` | `architecture.api_style` | `REST`, `GraphQL`, `tRPC`, `gRPC` |
| `{{AUTH_PATTERN}}` | `architecture.auth` | `JWT`, `session`, `OAuth-only` |
| `{{ERROR_STRATEGY}}` | `architecture.error_handling` | `exceptions`, `result-types` |
| `{{TESTING_STRATEGY}}` | `quality.testing` | `unit-first`, `integration-first`, `e2e-first` |
| `{{CI_PLATFORM}}` | `quality.ci_cd` | `github-actions`, `gitlab-ci` |
| `{{MERGE_STRATEGY}}` | `quality.merge_strategy` | `squash`, `rebase`, `merge-commit` |
| `{{STATE_APPROACH}}` | `stack.state_management` | `local-first`, `redux`, `zustand` |

### Processing Flow

```
Template + Config → AI Agent → Generated Rule

{{API_STYLE}}     +  REST   →    REST
{{IF REST}}...    +  REST   →    (content included)
{{IF GraphQL}}... +  REST   →    (content removed)
```

---

## Customization

Generated rules include `<!-- PROJECT-SPECIFIC -->` sections where you can add custom standards. These sections are preserved when regenerating rules.

### Adding New Commands

Create a `.md` file in `.cursor/commands/` with:
- Overview section explaining the command's purpose
- Steps section with numbered instructions
- Optional Parameters section for command arguments

### Adding New Rule Templates

Create a `.md` file in `.cursor/templates/rules/` with:
- YAML frontmatter (`description`, `globs`, `alwaysApply`)
- Rule content with `{{PLACEHOLDER}}` syntax
- `<!-- PROJECT-SPECIFIC -->` section for user additions

## Recommended Workflow

```bash
# Initial setup
/init-project-config          # Answer architecture questions

# Generate rules for your stack
/create-general-rules         # Always run this first
/create-lang-rules typescript # If using TypeScript
/create-frontend-rules react  # If using React
/create-api-rules rest        # If building REST APIs

# Ongoing usage
/analyze-codebase             # Audit against your rules
/create-feature-spec          # Document new features
```

## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

[MIT](LICENSE) © Rhyguy
