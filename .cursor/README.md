# .cursor Folder

Cursor IDE configuration for spec-driven development.

## Contents

```
.cursor/
├── commands/       # Slash commands (/draft-spec, /plan-impl, etc.)
├── docs/           # Documentation and specs
├── plans/          # Generated implementation plans (output of /plan-impl)
├── rules/          # Persistent rules (always loaded)
└── templates/      # Rule templates for customization
```

## Quick Start

```
/quick-start
```

## Commands Available

- `/draft-spec` - Generate spec from idea
- `/plan-impl` - Create implementation plan
- `/implement-spec` - Generate code from spec
- `/review` - Quality check
- `/extract-spec` - Document existing code
- `/quick-start` - Initialize workflow
- `/update-readme` - Sync README with codebase

## Customization

See [templates/](templates/) for rule templates (`architecture.rule.md`, `coding-style.rule.md`, `project-cmds.rule.md`). Example:

```bash
cp templates/coding-style.rule.md rules/my-style.mdc
```

Edit for your project; the agent picks up changes automatically.

## Documentation

Full documentation in [docs/](docs/):

| Doc | Purpose |
|-----|---------|
| [Getting Started](docs/getting-started.md) | Installation and setup |
| [Spec-Driven Overview](docs/spec-driven-overview.md) | SDD intro and rationale |
| [Problem Size Guide](docs/problem-size-guide.md) | When to use which workflow |
| [Greenfield Workflow](docs/greenfield-workflow.md) | New features flow |
| [Brownfield Workflow](docs/brownfield-workflow.md) | Existing codebase flow |
| [Spec Writing Guide](docs/spec-writing-guide.md) | Write effective specs |
| [Commands Reference](docs/commands-reference.md) | Full command reference |
| [Extending](docs/extending.md) | Add rules and commands |
| [Best Practices](docs/best-practices.md) | Tips and references |
