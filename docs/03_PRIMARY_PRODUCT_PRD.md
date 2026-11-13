# 03 — Product Requirements Document: AI Order Assistant

**Version:** 0.1 / proposed / 2026-11-13  
**Approval:** PENDING — this is a first-candidate PRD, not a signed specification.

## Problem statement

Sales desks at catalogue-heavy wholesalers may receive incomplete, shorthand, multilingual or image/voice-based purchase requests. Staff must identify products, units, quantities, and variants before writing orders in existing billing tools. The proposed product reduces repetitive interpretation and data entry while maintaining explicit staff control.

## Customer and job-to-be-done

**Primary operator:** an order desk employee.  
**Buyer:** a small/medium distributor or wholesaler.  
**JTBD:** "When a retailer sends an unclear list, help me rapidly identify the intended stock items and prepare a correct, reviewable order I can transfer to my existing process."

## MVP scope — P0

| ID | Requirement | Acceptance criterion |
| --- | --- | --- |
| P0-01 | Business user authentication / isolated workspace | Cross-tenant reads/writes fail in tests |
| P0-02 | Import and validate catalogue CSV | Preview rows, reject malformed or duplicate SKU records, report errors |
| P0-03 | Paste unstructured text / manually upload image or audio | Capture consent and processing state; no automatic messaging-platform access |
| P0-04 | Extract item mentions, quantities, units, variant cues | Output schema-validated candidates with source spans where available |
| P0-05 | Match against **that tenant's** catalogue | Return exact/possible/unknown matches, never invent SKU or price |
| P0-06 | Clarification and exception queue | Unknown/ambiguous lines blocked from approval until explicitly resolved |
| P0-07 | Human review and edit | Reviewer sees original input next to suggestions; can correct or delete |
| P0-08 | Explicit approval and CSV export | Only approved, validated draft exported; export action recorded |
| P0-09 | Audit log and idempotent operations | Track who changed/approved; repeated requests do not duplicate orders |
| P0-10 | Offline synthetic evaluation suite | Tests for abbreviations, duplicate names, unit conversions, adversarial text |

**Demo compromise:** initial local-only proof of concept may use one fake tenant and simulated user access; never claim security-complete multi-tenancy until P0-01 is truly implemented.

## P1 after successful pilot

- Tenant-approved item aliases and historical-order context.
- Additional Indian-language parsing / speech, based on measured demand.
- Reorder suggestions with explicit user action.
- Billing/ERP adapters via written authorization and verified APIs.
- Exception dashboards and team assignments.
- Better image capture and mobile review.

## P2 / noncommitted

- Authorized inbound messaging integrations after provider approval and platform compliance.
- Customer-facing order confirmations with separate opt-in and approval.
- Assisted inventory availability checks using actual source of truth.
- Multi-location business and advanced approvals.

## Boundary and error behavior

- AI produces **suggestions only**. No purchase, payment, invoice, refund or delivery transaction without human authorization and trusted integration.
- If input is unclear, keep original phrase, record candidates and ask for clarification.
- If catalogue contains variants ("10A" vs "16A", size, color, pack), never resolve by plausibility alone.
- Quantities/units must be explicit; no implicit pack conversions without known catalogue unit mappings.
- Never copy listed prices from buyer message into official SKU pricing without verification.
- Malicious text inside a customer message is **data**, not a command to the system.

## Representative example (synthetic)

Catalogue: `SW-10A` ("10 amp switch", piece); `SW-16A` ("16 amp switch", piece).  
Input: "send 12 switches and 2 boxes 16 amp".  
Output: line 1 *ambiguous switch variant*, 12 pieces; line 2 tentative `SW-16A`, 2 boxes but **box-to-piece factor unknown**. Both require resolution. Do not silently approve.

## Performance & UX targets (proposed, validate in pilot)

- Preview and edits comfortable on common mobile and desktop browsers.
- No blocking on long AI calls; show states, allow retry/cancel.
- Fast text-only demo; track actual p50/p95 latency before setting SLOs.
- CSV exports open correctly in the pilot's billing process, using a pilot-specific mapping.

## Out of scope

Accounting ledger replacement, GST tax computation, payment processing, customer credit, inventory reservation, autonomous ordering, generalized CRM, app-store-scale consumer features.

## MVP release gate

3 paying or clearly committed pilots (target, not achieved); validated review quality, safe exports, agreed privacy practices, actual cost/latency data and user feedback. See [evaluation](08_AI_PIPELINE_AND_EVALUATION.md) and [roadmap](12_ROADMAP_90_DAYS.md).