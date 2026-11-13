# 10 — UX, Screens and Interaction Specification

**Status:** Proposed UX; no UI implementation yet. Primary interaction must be faster than manually retyping an order.

## Interface principles

- Show original customer request beside structured suggestions at all times.
- Explain uncertainty: `Exact`, `Possible match`, `Unknown`, `Unit needs review`, rather than misleading "AI confidence 99%."
- Every action is visible, undoable while draft, and keyboard accessible.
- Minimize owner setup effort; catalogues upload with an example template.
- Prefer clear English UI initially, design for Hindi/Bengali and regional languages after validation.
- Phone-friendly operation for shop-floor staff; desktop-friendly batch review.

## Screen 1 — Welcome / onboarding

Business info, secure sign-in, upload catalogue, preview rejected rows, activate version, invite employee (once auth exists). Show a synthetic sample order if first-time user.

## Screen 2 — Order inbox

Tabs: Drafts, Processing, Needs Review, Approved, Exported, Failed. Table/cards: reference ID, date, input type, exception count, reviewer, status. Search should never cross tenant boundary.

## Screen 3 — New order

Input choices: paste text (P0), file upload image/audio (P0 conditional on safe ingestion), or manual entry. Clearly explain that the user must have the right to upload the material. Show processing states and a manual fallback.

## Screen 4 — Review workbench

```text
+-------------------------+------------------------------------+
| ORIGINAL REQUEST        | SUGGESTED LINES                    |
| "12 switches..."        | 1) Switch 12 pcs [AMBIGUOUS]       |
|                         |    Choose variant: 10A / 16A       |
|  [View image/audio]     | 2) 16A switch 2 boxes [UNIT?]      |
|                         |    Define units / pack factor      |
+-------------------------+------------------------------------+
| [Save draft] [Request clarification] [Approve (disabled)]  |
+--------------------------------------------------------------+
```

Each line includes original phrase, resolved SKU/variant, unit, editable quantity, matched catalogue item, warning label and correction history. Approval remains disabled until every blocking exception resolves.

## Screen 5 — Export

Approved snapshot, export format preview, explicit "Download CSV" action, repeat-safe export, clear version/audit details. No automatic accounting push in MVP.

## Screen 6 — Admin

Member permissions, catalogue versions, processing costs, privacy/retention settings, audit trail. In early demo only a subset is necessary; label fake functionality as demo.

## Accessibility & localization

Visible keyboard focus, meaningful labels, semantic tables, screen reader announcements for processing/error states, adequate contrast, large touch targets, text resize and mobile layouts. Avoid relying only on color to represent unresolved states.

## Prototype user-testing tasks

1. Upload a 12-row fictional catalogue.
2. Paste an ambiguous two-line order.
3. Find and fix the wrong suggested SKU.
4. Resolve a missing pack size / leave unresolved where needed.
5. Approve and export correctly; repeat export to verify no duplication.
6. Explain what information the assistant used and where it was uncertain.

Observe completion time, misclicks, confusing language and manual workarounds. Improve based on real users.