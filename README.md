# Cursor Spec-Driven Starter

A minimal starter template for spec-driven AI-assisted development with Cursor IDE.

## Purpose

Write specs, let the agent implement. This starter provides commands, rules, and workflows for consistent, reliable AI-assisted coding.

## Quick Start

```bash
# Clone into a temp directory
git clone --depth 1 https://github.com/rhyanvargas/rhyan-cursor-docs.git /tmp/cursor-starter

# Copy .cursor folder to your project (no-clobber to avoid overwriting)
cp -rn /tmp/cursor-starter/.cursor ./

# Clean up
rm -rf /tmp/cursor-starter
```

**Next steps**
```bash
# Open in Cursor and run
/quick-start

# Start building
/draft-spec "your feature idea"
```

## What's Included

Everything lives in `.cursor/` for zero conflicts with your project:

```
.cursor/
├── commands/       # Slash commands (/draft-spec, /plan-impl, etc.)
├── docs/           # Documentation and specs
│   └── specs/      # Generated specifications
├── plans/          # Implementation plans
├── rules/          # Persistent rules
└── templates/      # Rule templates
```

## Workflows

| Workflow | When | Flow |
|----------|------|------|
| **Greenfield** | New features | `/draft-spec` → `/plan-impl` → `/implement-spec` → `/review` |
| **Brownfield** | Existing code | `/quick-start` → `/extract-spec` → then greenfield flow |
| **Quick fix** | Trivial changes | Just describe in chat |

See [Greenfield Workflow](.cursor/docs/greenfield-workflow.md) and [Brownfield Workflow](.cursor/docs/brownfield-workflow.md).

## Commands

| Command | When to Use |
|---------|-------------|
| `/draft-spec` | New feature idea |
| `/plan-impl` | Before coding (medium+ changes) |
| `/implement-spec` | After spec approved |
| `/review` | After implementation |
| `/extract-spec` | Document existing code |
| `/quick-start` | First-time setup |
| `/update-readme` | Keep README in sync with codebase |

See [Commands Reference](.cursor/docs/commands-reference.md).

## Documentation

| Doc | Purpose |
|-----|---------|
| [Getting Started](.cursor/docs/getting-started.md) | Installation and setup |
| [Problem Size Guide](.cursor/docs/problem-size-guide.md) | When to use which workflow |
| [Spec Writing Guide](.cursor/docs/spec-writing-guide.md) | Write effective specs |
| [Extending](.cursor/docs/extending.md) | Add rules and commands |
| [Best Practices](.cursor/docs/best-practices.md) | Tips and references |
| [Overview](.cursor/docs/spec-driven-overview.md) | SDD concepts explained |

## Extending

Add rules when the agent makes repeated mistakes:
```bash
cp .cursor/templates/coding-style.rule.md .cursor/rules/my-style.mdc
```

Add commands for workflows you repeat:
```bash
touch .cursor/commands/my-workflow.md
```

See [Extending](.cursor/docs/extending.md).

## References

- [Cursor Agent Best Practices](https://cursor.com/blog/agent-best-practices)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Tessl](https://tessl.io/) – Agent enablement platform with versioned context and evals
- [GitHub Spec Kit](https://github.com/github/spec-kit/blob/main/README.md) – Open source spec-driven development toolkit
- [Microsoft: Diving Into Spec-Driven Development With GitHub Spec Kit](https://developer.microsoft.com/blog/spec-driven-development-spec-kit)
- [Kiro: Specs Concepts](https://kiro.dev/docs/specs/concepts/) – Requirements, design, and implementation planning

## Source Credits

- [Tessl](https://tessl.io/)

## License

MIT
