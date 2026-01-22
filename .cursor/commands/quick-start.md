# Quick Start

Set up minimal Cursor rules for your project. This is the **recommended approach** for most projects.

## Overview

Creates a single, focused rule file based on YOUR project's unique patterns. Follows Cursor best practices: *"Add rules only when you notice Agent making the same mistake repeatedly."*

## What This Does

1. Asks about your project's unique architecture decisions
2. Creates ONE rule file: `.cursor/rules/project.mdc`
3. Optionally creates `AGENTS.md` for simpler projects

## Questions

**Architecture:**
- What's your folder structure? (feature-based, layer-based, custom)
- What internal libraries should Agent know about?
- What patterns do you use that DIFFER from defaults?
- What anti-patterns should Agent avoid?

**References:**
- Point to 2-3 canonical example files for Agent to follow

## Output

Creates `.cursor/rules/project.mdc`:

```markdown
---
description: Project-specific standards
alwaysApply: true
---

# Project Standards

## Architecture
[Your specific folder structure]

## Internal Libraries
[Libraries Agent doesn't know about]

## Patterns We Use
[Only things that differ from defaults]

## Reference Files
@path/to/example-component.tsx
@path/to/example-api-route.ts
```

## Parameters

- `/quick-start` — interactive setup
- `/quick-start agents-only` — creates only AGENTS.md (simplest option)

## When to Use Extended Templates Instead

Use `/create-general-rules` and extended templates if:
- You need comprehensive documentation for large teams
- You have compliance/audit requirements
- You want detailed rules for code review automation

Extended templates are in `.cursor/templates/extended/rules/`.
