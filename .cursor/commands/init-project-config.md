# Initialize Project Configuration

Capture architecture decisions through a questionnaire. Save answers to `.cursor/project-config.yaml` for use by other rule-creation commands.

## Template
@.cursor/templates/project-config.yaml

## Questions to Ask

**Project & Architecture:**
- Application type (web-app, api, cli, library, monorepo)
- Team size (solo, small, medium, large)
- Code organization (feature-based, layer-based, domain-driven)
- API style (REST, GraphQL, tRPC, none)
- Auth pattern (JWT, session, OAuth-only, none)

**Quality & Stack:**
- Testing strategy (unit-first, integration-first, e2e-first)
- CI/CD platform (github-actions, gitlab-ci, none)
- Primary language(s)
- Frontend/backend frameworks

## Steps
1. Check if `.cursor/project-config.yaml` exists — offer to update or replace
2. Auto-detect stack from `package.json`, `tsconfig.json`, etc. if present
3. Ask questions, use detected values as defaults
4. Save config file
5. Suggest next commands based on answers

## Completion Checklist
- [ ] Project & Architecture questions answered
- [ ] Quality & Stack questions answered
- [ ] Config file saved to `.cursor/project-config.yaml`
- [ ] Suggested next commands shown based on answers