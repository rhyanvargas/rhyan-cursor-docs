---
name: spec-driven-workflow
description: Spec-driven development workflow for AI-assisted coding. Use when drafting specs, planning implementation, implementing from specs, reviewing code, extracting specs from existing code, or when the user asks about spec-driven development, greenfield/brownfield workflows, or problem sizing.
---

# Spec-Driven Workflow

Spec-Driven Development (SDD) shifts coding from ad-hoc prompts to structured specifications. Use this skill when the user is working with specs, planning features, implementing from specs, or documenting existing code.

## When to Use

- User invokes `/draft-spec`, `/plan-impl`, `/implement-spec`, `/review`, `/extract-spec`, `/quick-start`, or `/update-readme`
- User asks about spec-driven development, greenfield vs brownfield, or problem sizing
- User is writing or refining a specification
- User is working with existing code and needs to document it first

## Quick Reference

| Size | Workflow |
|------|----------|
| Trivial | Skip workflow, describe in chat |
| Small | `/draft-spec` → `/implement-spec` |
| Medium | `/draft-spec` → `/plan-impl` → `/implement-spec` → `/review` |
| Large | Research first, then full workflow |

## Key Commands

- `/draft-spec "idea"` - Generate spec from feature idea
- `/plan-impl spec.md` - Create implementation plan
- `/implement-spec spec.md` - Generate code from spec
- `/review` or `/review --spec spec.md` - Quality check
- `/extract-spec path/` - Document existing code
- `/quick-start` - Initialize workflow
- `/update-readme` - Sync README with codebase

## References

See `references/` for detailed documentation:

| Reference | Purpose |
|-----------|---------|
| [getting-started](references/getting-started.md) | Setup and first run |
| [spec-driven-overview](references/spec-driven-overview.md) | SDD intro and rationale |
| [problem-size-guide](references/problem-size-guide.md) | When to use which workflow |
| [greenfield-workflow](references/greenfield-workflow.md) | New features flow |
| [brownfield-workflow](references/brownfield-workflow.md) | Existing codebase flow |
| [spec-writing-guide](references/spec-writing-guide.md) | Write effective specs |
| [commands-reference](references/commands-reference.md) | Full command reference |
| [extending](references/extending.md) | Add rules and commands |
| [best-practices](references/best-practices.md) | Tips and references |
