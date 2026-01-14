# Create General Rules

Create framework-agnostic coding standards using templates. Read project config from @.cursor/project-config.yaml if it exists.

## Templates
- @.cursor/templates/rules/general-rule.md → `.cursor/rules/general/RULE.md`
- @.cursor/templates/rules/git-rule.md → `.cursor/rules/git/RULE.md`
- @.cursor/templates/rules/security-rule.md → `.cursor/rules/security/RULE.md`
- @.cursor/templates/rules/testing-rule.md → `.cursor/rules/testing/RULE.md`
- @.cursor/templates/rules/documentation-rule.md → `.cursor/rules/documentation/RULE.md`

## Steps
1. Read project config for placeholder values
2. Create each rule from its template
3. Replace `{{placeholders}}` with config values
4. Warn before overwriting existing rules
5. Summarize what was created

## Parameters
- `/create-general-rules` — all 5 rules
- `/create-general-rules minimal` — only general + security
- `/create-general-rules skip:git,docs` — skip specific rules
