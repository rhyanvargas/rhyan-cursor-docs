# Agentic Dev Starter Kit (ADS Kit)

A cross-platform starter kit for agentic AI-assisted development. Works with Cursor, Windsurf, Claude Code, and other AI coding tools.

## Purpose

Portable skills, workflows, and tooling for consistent AI-assisted development across any agentic platform.

## Quick Start

```bash
# Clone into a temp directory
git clone --depth 1 https://github.com/rhyanvargas/ads-kit.git /tmp/ads

# Copy .agents folder (works with any AI tool)
cp -rn /tmp/ads/.agents ./

# Optionally copy .cursor folder (for Cursor IDE)
cp -rn /tmp/ads/.cursor ./

# Clean up
rm -rf /tmp/ads
```

## What's Included

```
.agents/                    # Cross-platform portable content
└── skills/                 # Reusable skills (portable across tools)
    ├── spec-driven-workflow/
    ├── find-skills/
    └── devops-strategy-facilitator/

.cursor/                    # Cursor IDE-specific
├── commands/               # Slash commands (/draft-spec, /plan-impl, etc.)
├── docs/specs/             # Generated specs (output of /draft-spec, /extract-spec)
├── plans/                  # Implementation plans (output of /plan-impl)
├── rules/                  # Persistent rules
├── skills/                 # Cursor skills (spec-driven-workflow, etc.)
└── templates/              # Rule templates
```

## Platform Support

| Platform | Directory | Status |
|----------|-----------|--------|
| Cursor | `.cursor/` | Full support (skills, commands, rules) |
| Windsurf | `.agents/` | Skills only |
| Claude Code | `.agents/` | Skills only |
| Other | `.agents/` | Skills only |

## Cursor-Specific Features

If using Cursor IDE, you get additional features:

### Workflows

| Workflow | When | Flow |
|----------|------|------|
| **Greenfield** | New features | `/draft-spec` → `/plan-impl` → `/implement-spec` → `/review` |
| **Brownfield** | Existing code | `/quick-start` → `/extract-spec` → then greenfield flow |
| **Quick fix** | Trivial changes | Just describe in chat |

### Commands

| Command | When to Use |
|---------|-------------|
| `/draft-spec` | New feature idea |
| `/plan-impl` | Before coding (medium+ changes) |
| `/implement-spec` | After spec approved |
| `/review` | After implementation |
| `/extract-spec` | Document existing code |
| `/quick-start` | First-time setup |
| `/update-readme` | Keep README in sync with codebase |

See [Commands Reference](.cursor/skills/spec-driven-workflow/references/commands-reference.md).

### Documentation

| Doc | Purpose |
|-----|---------|
| [Getting Started](.cursor/skills/spec-driven-workflow/references/getting-started.md) | Installation and setup |
| [Spec-Driven Overview](.cursor/skills/spec-driven-workflow/references/spec-driven-overview.md) | SDD intro and rationale |
| [Problem Size Guide](.cursor/skills/spec-driven-workflow/references/problem-size-guide.md) | When to use which workflow |
| [Greenfield Workflow](.cursor/skills/spec-driven-workflow/references/greenfield-workflow.md) | New features flow |
| [Brownfield Workflow](.cursor/skills/spec-driven-workflow/references/brownfield-workflow.md) | Existing codebase flow |
| [Spec Writing Guide](.cursor/skills/spec-driven-workflow/references/spec-writing-guide.md) | Write effective specs |
| [Extending](.cursor/skills/spec-driven-workflow/references/extending.md) | Add rules and commands |
| [Best Practices](.cursor/skills/spec-driven-workflow/references/best-practices.md) | Tips and references |

## Available Skills

| Skill | Description |
|-------|-------------|
| `spec-driven-workflow` | Spec-driven development workflow (greenfield + brownfield) |
| `find-skills` | Discover and install skills from the open ecosystem |
| `devops-strategy-facilitator` | Facilitate a concise DevOps strategy design session |

## Extending

### Add custom skills

Create a new skill in `.agents/skills/`:

```
.agents/skills/my-skill/
├── SKILL.md           # Skill definition and instructions
├── references/        # Documentation files
└── scripts/           # Example code
```

### Add Cursor rules

See [`.cursor/templates/rule-templates.md`](.cursor/templates/rule-templates.md). Copy the section you need to `.cursor/rules/<name>.mdc` and customize.

### Add Cursor commands

```bash
touch .cursor/commands/my-workflow.md
```

## Updating

To pull the latest version:

```bash
# Clone fresh copy
git clone --depth 1 https://github.com/rhyanvargas/ads-kit.git /tmp/ads

# Copy new files (no-clobber preserves your changes)
cp -rn /tmp/ads/.agents ./
cp -rn /tmp/ads/.cursor ./

# Clean up
rm -rf /tmp/ads
```

## References

- [Cursor Agent Best Practices](https://cursor.com/blog/agent-best-practices)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Tessl](https://tessl.io/) – Agent enablement platform
- [GitHub Spec Kit](https://github.com/github/spec-kit/blob/main/README.md) – Spec-driven development toolkit
- [Kiro: Specs Concepts](https://kiro.dev/docs/specs/concepts/) – Requirements, design, and implementation planning

## License

MIT
