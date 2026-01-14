# Create Language Rules

Create language-specific coding standards. Read languages from @.cursor/project-config.yaml or use parameter.

## Templates
- @.cursor/templates/rules/typescript-rule.md → `.cursor/rules/typescript/RULE.md`
- @.cursor/templates/rules/python-rule.md → `.cursor/rules/python/RULE.md`

## Steps
1. Determine language from parameter or config
2. Create rule from matching template
3. Set appropriate glob patterns
4. Warn before overwriting

## Parameters
- `/create-lang-rules typescript`
- `/create-lang-rules python`
- `/create-lang-rules` — use languages from config
