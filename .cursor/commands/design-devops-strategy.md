# /design-devops-strategy

Collaborate with the user to design a **concise, project-specific DevOps strategy** (branching, CI/CD, environments, governance) without baking in assumptions.

## Usage

```
/design-devops-strategy
```

Optional context:
```
/design-devops-strategy "Azure DevOps + AKS + 2 envs (dev/prod), quarterly releases"
```

## Behavior

1. **Scope** - Identify project type, delivery constraints, and target platform(s) (Azure DevOps, GitHub Actions, GitLab, etc.).
2. **Decide** - Drive to explicit decisions (with defaults) and record rationale.
3. **Draft** - Produce a short “DevOps Strategy” doc the team can adopt immediately.
4. **Refine** - Ask only the minimum follow-ups needed to remove ambiguity.
5. **Next steps (optional)** - Offer to translate the strategy into repo scaffolding and/or Cursor artifacts (rules/commands/skills) for that project.

## Strategy Output Template (keep it tight)

```markdown
# DevOps Strategy — {Project Name}

## Goals
- {Goal 1}
- {Goal 2}

## Non-Goals
- {Non-goal 1}

## Delivery Model
- **Release cadence**: {e.g., on-demand | weekly | date-based release branches}
- **Promotion model**: {e.g., build once → promote artifacts}

## Branching & PR Policy
- **Branch types**: {e.g., feature/*, release/*, main}
- **Merge flow**: {e.g., feature/* → release/* → main}
- **PR gates**: {tests, lint, approvals, CODEOWNERS}

## CI (Build + Validate)
- **Triggers**: {PRs, pushes, schedule}
- **Responsibilities**: {lint, tests, package, SBOM, sign}
- **Artifacts**: {what, where stored, version metadata}

## CD (Deploy)
- **Environments**: {dev, prod, ...}
- **Dev**: {auto/manual}, **Prod**: {auto/manual + approvals}
- **Rollback**: {strategy}

## Secrets & Configuration
- **Secret store**: {Key Vault, etc.}
- **Config**: {pipeline vars, config files, runtime config}

## Governance & Access
- **Who can deploy to Prod**: {groups}
- **Audit trail**: {where tracked}

## Observability
- **Logs/metrics/traces**: {tools + minimum SLOs}

## Open Questions
- {Question 1}

## Decision Log
| Area | Decision | Rationale |
|------|----------|-----------|
| Branching | {…} | {…} |
```

## Instructions

When the user invokes `/design-devops-strategy`:

1. Ask **5–10 targeted questions max**, prioritizing:
   - Platform (Azure DevOps/GHA/other), hosting target (VM/K8s/PaaS), IaC (Y/N)
   - Environments + approval model
   - Artifact strategy (build once/promote vs rebuild per env)
   - Branching/release model + PR gates
   - Secrets/config management and required compliance controls
2. Propose a **default strategy** when inputs are missing; clearly mark assumptions.
3. Produce the doc using the template above (≤ ~1–2 pages).
4. Offer an optional follow-up: “Want me to generate repo structure + pipeline skeletons and/or Cursor rules from this?”

