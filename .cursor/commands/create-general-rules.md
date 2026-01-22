# Create General Rules (Extended)

> **Note**: For most projects, use `/quick-start` instead. This command creates comprehensive rules from the extended templates, which may include patterns Agent already knows.

Create framework-agnostic coding standards using extended templates. Read project config from @.cursor/project-config.yaml if it exists.

## Templates (Extended)
- @.cursor/templates/extended/rules/general-rule.md → `.cursor/rules/general/RULE.md`
- @.cursor/templates/extended/rules/git-rule.md → `.cursor/rules/git/RULE.md`
- @.cursor/templates/extended/rules/security-rule.md → `.cursor/rules/security/RULE.md`
- @.cursor/templates/extended/rules/testing-rule.md → `.cursor/rules/testing/RULE.md`
- @.cursor/templates/extended/rules/documentation-rule.md → `.cursor/rules/documentation/RULE.md`

## When to Use
- Large teams needing comprehensive documentation
- Enterprise/compliance requirements
- Code review automation

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
