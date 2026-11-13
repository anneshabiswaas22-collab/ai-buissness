# 04 — User Stories, End-to-End Flows and Edge Cases

## Personas (hypotheses for validation)

- **Owner/Admin:** imports company catalogue, invites reviewers, sees value metrics, pays subscription.
- **Sales Operator:** receives customer requests and creates draft orders.
- **Reviewer/Approver:** verifies variants, quantities, customer and export mapping.
- **External Buyer:** sends an order through existing channels; not necessarily a user/account in MVP.

## Flow A — First-time setup

1. Authenticated admin creates business workspace.
2. Downloads CSV template: SKU, name, aliases, category, unit, optional price/pack metadata.
3. Uploads catalogue and sees validation preview.
4. Resolves duplicates and missing fields; activates a version.
5. Invites staff with restricted roles (production; simulated locally for offline demo).

**Edge cases:** duplicate SKU; reused item alias; incorrectly encoded CSV; missing units; price changes; stale catalogue; permissions to replace a version.

## Flow B — Order intake / extraction

1. Operator creates new draft and chooses input type.
2. Operator pastes text or uploads a permitted image / audio file.
3. System keeps original evidence and shows ingestion/transcription state.
4. Extractor proposes order lines with source evidence.
5. Matcher checks *only* current tenant catalogue and item units.
6. Unknown/low-confidence lines enter a clear exception state.
7. Operator asks buyer for missing detail outside app, then records a clarification.

**Edge cases:** abbreviations, multilingual terms, handwritten photo unreadable, repeated product names, counts with decimals, negative qty, conflicting units, mixed customer orders, duplicate submission, unsupported file, model unavailable. Model outage should allow manual entry.

## Flow C — Human review / approval

1. Reviewer sees original evidence and proposed lines side by side.
2. Reviewer chooses/changes SKU; confirms quantity, unit, variant, customer.
3. System recomputes validations after each change.
4. Reviewer can save draft, return for clarification or explicitly approve.
5. Only approved and validated items become export-eligible.
6. CSV export carries stable item columns and an order reference; audit event is recorded.

**Critical:** No "approve all" shortcut for unresolved lines. An AI confidence score is never sufficient alone to approve a binding order.

## Flow D — Error recovery

- Failed OCR/transcription: preserve uploaded evidence with consent, permit retry or manual entry.
- Failed match: show original input and "not in catalogue"; never substitute random SKU.
- Export failed: do not change approval state; safe retry with idempotency key.
- Wrong catalogue version: warn / block approval if a line refers to inactive item version.
- Access revoked: deny further reads of drafts/files immediately.

## Suggested UI routes

`/sign-in`, `/workspace/catalogue`, `/orders`, `/orders/new`, `/orders/:id/review`, `/settings/members`, `/settings/audit`. These are a **proposed** layout, not existing routes.

## Acceptance scenarios (Gherkin-style)

```gherkin
Scenario: Unknown SKU cannot pass approval
  Given a tenant-specific catalogue without "20A red plug"
  When an operator submits a request for "20A red plug"
  Then the line is marked unknown
  And approval is blocked until an authorized reviewer resolves it

Scenario: Tenant isolation
  Given business A and business B each have a catalogue
  When a business A user requests B's order ID
  Then access is denied and no B content is returned

Scenario: Repeated export
  Given an approved draft order
  When the same export request is retried with the same idempotency key
  Then the server returns the same export artifact reference
  And does not create a duplicate transaction
```

Use fabricated data in samples and tests.