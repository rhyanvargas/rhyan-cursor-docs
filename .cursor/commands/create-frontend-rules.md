# Create Frontend Rules (Extended)

> **Note**: Agent already knows React/Vue patterns well. Only use this if you have project-specific component conventions.

Create UI component and state management standards using extended templates. Read framework from @.cursor/project-config.yaml or use parameter.

## Templates (Extended)
- @.cursor/templates/extended/rules/react-rule.md → `.cursor/rules/react/RULE.md`

## When to Use
- You have a custom design system Agent should follow
- You need to document specific component patterns
- Large teams needing explicit frontend standards

## Steps
1. Determine framework from parameter or config
2. Create rule from matching template
3. Replace `{{STATE_APPROACH}}` with config value
4. Warn before overwriting

## Parameters
- `/create-frontend-rules react`
- `/create-frontend-rules` — use framework from config
