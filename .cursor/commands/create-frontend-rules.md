# Create Frontend Rules

Create UI component and state management standards. Read framework from @.cursor/project-config.yaml or use parameter.

## Templates
- @.cursor/templates/rules/react-rule.md → `.cursor/rules/react/RULE.md`

## Steps
1. Determine framework from parameter or config
2. Create rule from matching template
3. Replace `{{STATE_APPROACH}}` with config value
4. Warn before overwriting

## Parameters
- `/create-frontend-rules react`
- `/create-frontend-rules vue`
- `/create-frontend-rules` — use framework from config
