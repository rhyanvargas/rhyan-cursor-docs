# Create Language Rules (Extended)

> **Note**: For most projects, Agent already knows language best practices. Only use this if you have project-specific language conventions.

Create language-specific coding standards using extended templates. Read languages from @.cursor/project-config.yaml or use parameter.

## Templates (Extended)
- @.cursor/templates/extended/rules/typescript-rule.md → `.cursor/rules/typescript/RULE.md`
- @.cursor/templates/extended/rules/python-rule.md → `.cursor/rules/python/RULE.md`

## When to Use
- You have project-specific type conventions
- You need to document custom linting rules
- Large teams needing explicit language standards

## Steps
1. Determine language from parameter or config
2. Create rule from matching template
3. Set appropriate glob patterns
4. Warn before overwriting

## Parameters
- `/create-lang-rules typescript`
- `/create-lang-rules python`
- `/create-lang-rules` — use languages from config
