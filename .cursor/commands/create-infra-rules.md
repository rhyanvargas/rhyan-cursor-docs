# Create Infrastructure Rules

Create CI/CD and deployment standards. Read CI platform from @.cursor/project-config.yaml or use parameter.

## Templates
- @.cursor/templates/rules/infrastructure-rule.md → `.cursor/rules/infrastructure/RULE.md`

## Steps
1. Determine CI/CD platform from parameter or config
2. Create rule from template
3. Replace `{{CI_PLATFORM}}` with config value
4. Warn before overwriting

## Parameters
- `/create-infra-rules github`
- `/create-infra-rules gitlab`
- `/create-infra-rules` — use CI platform from config
