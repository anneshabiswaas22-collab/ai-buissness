# 13 — Metrics, Experiment Design and Evidence Log

**Status:** Proposed measurement plan; **all numeric results are currently unmeasured**.

## North-star candidates (choose after validation)

For B2B order assistant: **human-approved, correctly mapped draft orders processed weekly per active paying business**, with error-guardrail metrics. This rewards useful, safe repeat usage rather than model calls or registrations.

## Metric dictionary

| Metric | Definition | Source |
| --- | --- | --- |
| Active business | Workspace with >=1 approved, real workflow order in 7 days | Approved order events |
| Weekly approved orders | Number of distinct human-approved order revisions | Approval events |
| Median review time | Time first draft ready -> successful human approval | Workflow timestamps |
| Baseline manual time | Staff minutes/order before or without product | Observational study |
| Correct SKU rate | Correct matches on human-labeled test lines | Evaluation set |
| False resolution rate | Ambiguous/unknown lines incorrectly presented as safe | Evaluation set |
| Correction rate | Lines edited manually / proposed lines | Review events |
| Pilot conversion | Paying/committed pilots / qualified demos | CRM evidence |
| Retention | Paying workspaces continuing after renewal opportunity | Invoices + activity |
| Cost per approved order | Measured hosting/AI direct usage cost / approved orders | Usage and billing data |
| Support load | Human support minutes / paying business / month | Ticket log |

Never include sample results as actual performance.

## Suggested experiments

**E1 — Problem reality:** 20 interviews, record order count, manual minutes, observed errors, willingness to pay. Decision: proceed only if consistent costly pain exists.

**E2 — Rule-based vs LLM:** same synthetic fixture set; compare exact SKU, alias/rule, and structured extraction with cost/latency/error breakdown. Decision: use cheapest workflow that meets safety threshold.

**E3 — Review screen usability:** ask 5–8 order desk workers to correct ambiguous cases; measure completion and comprehension. Decision: revise interface where approvals are unclear.

**E4 — Pricing acceptance:** test genuine pilot offers with two approved pricing options and identical service scope; record objections and conversion. Do not manufacture sales data.

**E5 — Repeat usage:** after pilots, observe weekly use, second-week return, renewal interest, and spontaneous referrals.

## Evidence record format

```markdown
### EXP-YYYY-MM-DD-N
- Hypothesis:
- Owner / source:
- Customer type / sample size:
- Consent and anonymization:
- Method and baseline:
- Actual observed results:
- Costs:
- Confounders and limitations:
- Decision / follow-up:
```

Store sanitized experiment summaries under `research/` when they exist. Never commit raw customer recordings, phone numbers or order payloads without explicit permission and a secure storage design.