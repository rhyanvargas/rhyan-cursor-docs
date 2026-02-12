---
name: devops-strategy-facilitator
description: Facilitates a concise DevOps strategy design session (branching, CI/CD, environments, governance, artifacts, secrets). Use when the user asks to design or refine a DevOps/CI-CD strategy, branching model, environment promotion flow, deployment governance, or when /design-devops-strategy is invoked.
---

# DevOps Strategy Facilitator

Design a DevOps strategy that is **explicit, minimal, and adoptable**.

## Principles

- **Decision-first**: force choices; don’t write prose.
- **Build once, promote** by default (unless constraints require rebuilds).
- **Environment-agnostic code**: configuration via deployment tooling, not code branches.
- **Least privilege + auditability**: especially for Prod deployments.
- **Keep it short**: prefer tables/checklists over paragraphs.

## Working Session Flow

1. **Context** (30 seconds)
   - Platform (ADO/GHA/GitLab), runtime target (K8s/PaaS/VM), IaC, compliance needs.
2. **Decisions** (5–10 questions max)
   - Branching model + merge flow
   - CI responsibilities + artifact format/versioning
   - CD promotion model + environment approvals
   - Secrets/config approach
   - Rollback + observability minimums
3. **Draft strategy doc**
   - Use the command template; keep ≤ ~1–2 pages.
4. **Validate**
   - Call out risks, open questions, and “what we’re not doing”.

## Question Bank (pick only what you need)

- **Platform**: Which CI/CD platform(s)? Any mandated tooling?
- **Runtime**: Where does it run (K8s, App Service, Functions, VMs)?
- **Envs**: What environments exist today and what approvals are required?
- **Promotion**: Build once → promote, or rebuild per env? Why?
- **Release cadence**: continuous, weekly, or date-based release branches?
- **Compliance**: change control, separation-of-duties, evidence needs?
- **Artifacts**: container images? zip packages? helm charts? where stored?
- **Secrets**: where stored and how injected (vault, OIDC, service connections)?
- **Rollback**: blue/green, canary, redeploy previous artifact, DB rollback plan?
- **Observability**: minimum logging/metrics/tracing + alerting expectations?

## Output Requirements

- **Mark assumptions** explicitly.
- Include a **Decision Log** table.
- End with **Next steps** (optional): repo layout + pipeline skeleton + Cursor artifacts.

