# Create API Rules (Extended)

> **Note**: Agent already knows REST/GraphQL patterns. Only use this if you have project-specific API conventions.

Create backend API design standards using extended templates. Read API style from @.cursor/project-config.yaml or use parameter.

## Templates (Extended)
- @.cursor/templates/extended/rules/api-rule.md → `.cursor/rules/api/RULE.md`

## When to Use
- You have custom response formats Agent should follow
- You need to document specific auth patterns
- Large teams needing explicit API standards

## Steps
1. Determine API style from parameter or config
2. Create rule from template
3. Replace `{{API_STYLE}}` and `{{AUTH_PATTERN}}` with config values
4. Warn before overwriting

## Parameters
- `/create-api-rules rest`
- `/create-api-rules graphql`
- `/create-api-rules` — use API style from config
