# 12 — 90-Day Discovery-to-Pilot Roadmap

**Status:** Proposed sequence derived from October 28 advice. Dates are relative to founder approval, not automatically scheduled. Each phase has a stop/go gate.

## Weeks 1–2 — Discovery, not engineering first

- Identify ~20 wholesalers/distributors, starting with an electrical wholesale niche if approved.
- Interview owners and order desk staff; observe actual orders, current tools and pain.
- Record anonymized workflows, time spent, mistake cost, language and catalogue characteristics.
- Validate procurement decision, price sensitivity, usage frequency and data permissions.
- **Deliverables:** interview script, evidence tracker, problem ranking, candidate ICP, initial SKU fixture dataset.
- **Gate:** enough repeated pain and buyer interest to justify a demo. If weak, revisit the portfolio.

## Weeks 3–4 — Demonstrate a narrow workflow

- Build click-through screens or local text-to-draft prototype using fabricated catalogues.
- Show 3–5 customers; note manual corrections and rejection reasons.
- Seek ~3 paid pilots or meaningful written commitments, with clear safety terms.
- Finalize privacy/consent plan, trial success criteria, and basic integration assumptions.
- **Deliverables:** demo, evaluation fixtures, pilot offer, pilot decision.
- **Gate:** credible pay willingness and feasibility. Do not buy infrastructure in anticipation.

## Weeks 5–8 — Build common repeated workflow

- Build catalogue importer, extraction adapter, candidate matcher, review screen, manual fallback, CSV export.
- Add authentication/tenant isolation if using real customer data.
- Implement audit events, approval state machine and exception path.
- Run offline eval and per-order cost measurements; conduct pilot sessions.
- **Deliverables:** tested limited pilot product + support process.
- **Gate:** reviewers trust results, errors are manageable and gross economics plausible.

## Weeks 9–12 — Prove usage and growth

- Observe active weekly order volume, completion/review time, corrections, support burden.
- Ask pilot users for renewals, referrals and documented ROI.
- Fix top issues, defer unrequested features, choose one expansion opportunity.
- **Deliverables:** retention evidence, pilot outcomes, next 90-day roadmap.
- **Gate:** expand if customers repeat usage and renew; pivot if the use case is not valuable.

## Cross-phase controls

Keep human approval, tenant isolation, privacy, spend caps and honest metrics in place. No automatic WhatsApp/ERP access, payments, external sending or binding order transactions without separately reviewed authorization.

## First 10 tasks

1. Confirm founder product choice and pilot niche.
2. Create interview form and scoring rubric.
3. Schedule 20 buyer conversations.
4. Make synthetic SKU CSV and challenging order fixtures.
5. Wireframe upload -> extraction -> review -> export.
6. Define error / ambiguity acceptance criteria.
7. Implement a local deterministic catalogue matcher.
8. Add structured AI extraction adapter with fake offline mode.
9. Build human review and CSV export with tests.
10. Test live pilot only after privacy and security gate.

Track ownership and acceptance in [backlog](14_DELIVERY_BACKLOG.md).