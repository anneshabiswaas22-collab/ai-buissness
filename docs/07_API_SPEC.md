# 07 — Draft API Contract

**Status:** Proposal / not implemented. Prefix `/api/v1`. Authenticated JSON API with versioned schemas and strict validation.

## Rules

- Auth via secure session / validated token. Workspace scope is **derived server-side** from authenticated membership, not accepted blindly from body/query.
- Every mutating request carries an `Idempotency-Key` when retrying could duplicate work.
- All timestamps ISO 8601 UTC; validated decimal quantities, never float-based money calculations.
- Errors use stable machine-readable code and human-readable detail. No raw LLM output or cross-tenant information in error text.
- Pagination and rate limits apply to list operations.
- Inputs/outputs examples are illustrative and **not shipped endpoints**.

## Endpoints

| Method | Path | Role | Result |
| --- | --- | --- | --- |
| POST | `/workspaces` | permitted owner | create workspace after verification |
| GET | `/catalogues` | member | list scoped catalogue versions |
| POST | `/catalogues/import` | admin | validate CSV, return import preview |
| POST | `/catalogues/{version_id}/activate` | admin | activate checked version |
| POST | `/intakes` | operator | ingest text or signed upload reference |
| POST | `/intakes/{id}/extract` | operator | enqueue extraction; returns job ref |
| GET | `/jobs/{id}` | member | status and redacted error |
| GET | `/orders` | member | workspace-scoped list |
| GET | `/orders/{id}` | member | original evidence, line proposals and exceptions |
| PATCH | `/orders/{id}/lines/{line_id}` | operator / reviewer | validate and save explicit correction |
| POST | `/orders/{id}/approve` | reviewer | approve only if all checks pass |
| POST | `/orders/{id}/exports` | reviewer | create / retrieve approved CSV |
| GET | `/audit` | admin | paginated minimally sensitive audit events |

## Example: submit text intake

```http
POST /api/v1/intakes
Authorization: Bearer <token>
Idempotency-Key: 527c9c96-7ed4-4b7f-a27e-2603a960ef3a
Content-Type: application/json

{
  "input_kind": "text",
  "text": "12 switches and 2 boxes 16 amp",
  "catalogue_version_id": "cv_123"
}
```

Expected `201 Created` with `intake_id`, `state` = `DRAFT`, and `order_id`. Any unrecognized fields should be rejected where possible.

## Example: structured line proposal

```json
{
  "line_id": "line_1",
  "source_text": "12 switches",
  "quantity": "12",
  "unit": "piece",
  "match_status": "AMBIGUOUS",
  "candidates": [
    {"sku": "SW-10A", "reason": "catalogue candidate"},
    {"sku": "SW-16A", "reason": "catalogue candidate"}
  ],
  "resolved_sku": null,
  "review_required": true
}
```

No catalogue-derived authoritative SKU details may come from the LLM alone.

## State and auth failures

- `400 INVALID_INPUT`: unsupported or malformed.
- `401 UNAUTHENTICATED`, `403 FORBIDDEN`: auth / role failure.
- `404 NOT_FOUND`: inaccessible resource (avoid information leaks).
- `409 INVALID_STATE` or `CATALOGUE_VERSION_CHANGED`: approval conflict.
- `422 UNRESOLVED_LINE`: cannot approve an unknown SKU or ambiguous unit.
- `429 RATE_LIMITED`, `503 EXTRACTION_UNAVAILABLE`: degrade to manual workflow.

## Suggested approval request

`POST /orders/{id}/approve` with `{"expected_revision":3}` and idempotency key. Server checks membership, current state, all lines resolved, nonzero valid quantities, catalogue version, optimistic concurrency; returns immutable approval receipt. The model itself cannot call this endpoint.

## Schema ownership

After choosing a stack, encode these contracts in OpenAPI and generate typed client interfaces. Keep versioned integration fixtures; add contract tests for authorization, idempotency and failures.