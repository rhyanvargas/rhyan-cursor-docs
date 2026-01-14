# Create API Rules

Create backend API design standards. Read API style from @.cursor/project-config.yaml or use parameter.

## Templates
- @.cursor/templates/rules/api-rule.md → `.cursor/rules/api/RULE.md`

## Steps
1. Determine API style from parameter or config
2. Create rule from template
3. Replace `{{API_STYLE}}` and `{{AUTH_PATTERN}}` with config values
4. Warn before overwriting

## Parameters
- `/create-api-rules rest`
- `/create-api-rules graphql`
- `/create-api-rules` — use API style from config
