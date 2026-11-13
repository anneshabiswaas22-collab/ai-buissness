# 16 — Decision Log and Open Questions

**Rules:** Proposed does not mean approved. Date every actual decision. Keep reasoning and evidence.

## Current decision record

| ID | Date | Item | Status | Notes |
| --- | --- | --- | --- | --- |
| D-001 | 2026-10-28 | Build an AI-era software business focused on users and growth | **User goal confirmed** | Broad mission |
| D-002 | 2026-10-28 | AI Order Assistant as first product | **Prior assistant recommendation** | Not founder-approved |
| D-003 | 2026-10-28 | Electrical wholesalers initial niche | **Prior assistant recommendation** | Test market; not committed |
| D-004 | 2026-10-28 | ~20 interviews, ~3 pilots, 90-day milestones | **Prior assistant proposal** | No executions verified |
| D-005 | 2026-10-28 | ₹3k–₹8k/order-assistant business monthly | **Pricing experiment hypothesis** | Not approved price |
| D-006 | 2026-11-13 | Consolidate project context in GitHub | **Explicit user instruction** | Documentation handoff |
| D-007 | 2026-11-13 | Proposed technical architecture and API | **Draft, review needed** | No stack approval |
| D-008 | 2026-11-13 | Any consumer launch / production data processing | **Not authorized** | Needs separate decisions |

## Questions needing an explicit answer

1. Which of the four businesses is the first build? Is the suggested wholesale assistant accepted?
2. Is electrical wholesale the first test niche? Which city/region and business size?
3. What is the approved validation budget? Is ₹25k–₹75k acceptable or too high?
4. Who conducts the 20 interviews and owns 3 pilot conversions?
5. What channels/source data are permitted: paste, CSV, manual uploads, authorized platform APIs?
6. Which language(s), catalogue sizes, units and billing formats do real customers use?
7. What exact stack, hosting region, auth vendor, AI provider and commercial license are approved?
8. What are the consent, retention, deletion, legal/contract obligations and support commitments?
9. Which role can approve a finalized order and which outputs have binding effect?
10. What minimum measured results justify continued spend and expansion?

## Architectural decision record template

```markdown
# ADR-NNN: Decision name
Date:
Status: proposed | approved | superseded
Owner:
Context and user evidence:
Alternatives:
Decision:
Benefits:
Risks and security / privacy:
Cost and rollback:
Links to issue / PR / experiment:
```

When approval occurs, change the relevant status and cite where it was approved. Do not retroactively rewrite the origin of an earlier recommendation.