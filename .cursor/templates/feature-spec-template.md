# Feature Specification: {{FEATURE_NAME}}

> **Type**: {{FEATURE_TYPE}}  
> **Target Area**: {{TARGET_AREA}}  
> **Priority**: {{PRIORITY}}  
> **Owner**: {{OWNER}}  
> **Created**: {{DATE}}  
> **Status**: Draft

---

## Summary

{{BRIEF_DESCRIPTION}}

---

## Problem Statement

{{PROBLEM_STATEMENT}}

### Business/User Goal

{{MEASURABLE_GOAL}}

---

## Success Criteria

- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}
- [ ] {{CRITERION_3}}

---

## Non-Goals / Out of Scope

- {{NON_GOAL_1}}
- {{NON_GOAL_2}}

---

## Technical Requirements

### Data Requirements

| Aspect | Details |
|--------|---------|
| PII Involved | {{PII_YES_NO}} |
| Data Retention | {{RETENTION_POLICY}} |
| Storage | {{STORAGE_DETAILS}} |

### API Changes

{{API_CHANGES_OR_NONE}}

### Database Changes

{{DB_CHANGES_OR_NONE}}

### Security & Compliance

- {{SECURITY_CONSTRAINT_1}}
- {{SECURITY_CONSTRAINT_2}}

### Observability

- Logging: {{LOGGING_REQUIREMENTS}}
- Metrics: {{METRICS_REQUIREMENTS}}
- Alerts: {{ALERTING_REQUIREMENTS}}

---

## Implementation Plan

### Phase 1: {{PHASE_1_NAME}}

- [ ] Task 1
- [ ] Task 2

### Phase 2: {{PHASE_2_NAME}}

- [ ] Task 1
- [ ] Task 2

---

## Rollout Strategy

| Stage | Description | Success Criteria |
|-------|-------------|------------------|
| Feature Flag | {{FF_DETAILS}} | {{FF_SUCCESS}} |
| Canary | {{CANARY_DETAILS}} | {{CANARY_SUCCESS}} |
| Full Rollout | {{ROLLOUT_DETAILS}} | {{ROLLOUT_SUCCESS}} |

### Backout Plan

{{BACKOUT_PROCEDURE}}

---

## Open Questions

> Items marked **TBD** above are mirrored here for tracking.

| # | Question | Owner | Due Date | Resolution |
|---|----------|-------|----------|------------|
| 1 | {{QUESTION_1}} | {{OWNER}} | {{DATE}} | Pending |

---

## Sources & References

> Minimum 3 official documentation links required.

| # | Title | URL | Accessed | Relevance |
|---|-------|-----|----------|-----------|
| 1 | {{SOURCE_TITLE_1}} | {{SOURCE_URL_1}} | {{ACCESS_DATE_1}} | {{RELEVANCE_1}} |
| 2 | {{SOURCE_TITLE_2}} | {{SOURCE_URL_2}} | {{ACCESS_DATE_2}} | {{RELEVANCE_2}} |
| 3 | {{SOURCE_TITLE_3}} | {{SOURCE_URL_3}} | {{ACCESS_DATE_3}} | {{RELEVANCE_3}} |

---

## Spike Research (if applicable)

### Research Questions

1. {{RESEARCH_Q1}}
2. {{RESEARCH_Q2}}
3. {{RESEARCH_Q3}}

### Options Evaluated

| Option | Pros | Cons | Fit Score |
|--------|------|------|-----------|
| {{OPTION_1}} | {{PROS_1}} | {{CONS_1}} | {{SCORE_1}} |
| {{OPTION_2}} | {{PROS_2}} | {{CONS_2}} | {{SCORE_2}} |

### Recommendation

{{RECOMMENDATION_OR_DEFERRED}}

### POC Plan (if proceeding)

{{POC_STEPS}}

---

## Approvals

| Role | Name | Date | Status |
|------|------|------|--------|
| Engineering | | | Pending |
| Product | | | Pending |
| Security | | | Pending (if applicable) |

---

<!-- 
TEMPLATE USAGE NOTES:
- Replace all {{PLACEHOLDER}} values with actual content
- Use "TBD" for unknown values and mirror in Open Questions section
- Delete sections not applicable (e.g., Spike Research for well-defined features)
- Ensure minimum 3 sources with access dates
-->
