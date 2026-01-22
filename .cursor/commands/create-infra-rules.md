# Create Infrastructure Rules (Extended)

> **Note**: Agent knows common CI/CD patterns. Only use this if you have project-specific infrastructure conventions.

Create CI/CD and deployment standards using extended templates. Read CI platform from @.cursor/project-config.yaml or use parameter.

## Templates (Extended)
- @.cursor/templates/extended/rules/infrastructure-rule.md → `.cursor/rules/infrastructure/RULE.md`

## When to Use
- You have custom deployment workflows
- You need to document specific CI/CD patterns
- Large teams needing explicit infrastructure standards

## Steps
1. Determine CI/CD platform from parameter or config
2. Create rule from template
3. Replace `{{CI_PLATFORM}}` with config value
4. Warn before overwriting

## Parameters
- `/create-infra-rules github`
- `/create-infra-rules gitlab`
- `/create-infra-rules` — use CI platform from config
