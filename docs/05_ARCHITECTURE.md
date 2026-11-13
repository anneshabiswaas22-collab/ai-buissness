# 05 — Proposed Software Architecture

**Status:** Working proposal; no stack is committed or implemented. Focus on an inexpensive MVP that can grow.

## Preferred starter stack (proposal)

- **Web:** React + TypeScript, optionally Next.js for auth/routing if justified.
- **Backend:** Python + FastAPI, Pydantic validation.
- **Data:** PostgreSQL for real tenant isolation and transactions; SQLite only for offline single-user demo.
- **Files:** protected object storage; start with local fixtures for demo.
- **Background jobs:** simple worker / queue when OCR, STT or long inference demands it. Avoid Kubernetes/microservices in MVP.
- **AI:** pluggable LLM provider or self-hosted models with structured output; OCR/STT optional. Always retain human review.
- **Auth:** trusted identity provider or vetted library, server-issued tenant/role scope, secure sessions.
- **Observability:** structured redacted events, latency, token usage, model version, cost and explicit approval audit events.
- **Testing:** Pytest / frontend test runner, seeded synthetic catalogue, offline fake AI adapter.

## Logical services

```mermaid
flowchart TD
  UI["Review UI"] --> API["Authenticated API"]
  API --> DB[("Tenant-scoped database")]
  API --> CAT["Catalogue service"]
  API --> ORD["Order state machine"]
  API --> W["Ingestion job / queue"]
  W --> OCR["OCR / STT adapters"]
  W --> EXT["Structured extraction adapter"]
  EXT --> MATCH["Catalogue matcher"]
  MATCH --> ORD
  API --> STORE[("Protected input / export objects")]
  ORD --> AUDIT[("Audit events")]
  API --> METRICS["Redacted metrics / cost log"]
```

## Responsibilities

1. API authenticates user and derives business scope from session; rejects unauthorized resource access.
2. Ingestion validates type/size and obtains processing permission. For demo, accept pasted text only.
3. Extraction returns a typed structure; no permission to execute instructions in uploaded content.
4. Catalogue matching is tenant-scoped and deterministic-first: normalized exact SKU -> verified alias -> ranked candidates -> unknown.
5. Review state machine enforces valid transition rules; AI cannot approve.
6. Export service renders an authorized CSV and prevents duplicate export effects.
7. Audit service records actor, action, timestamp, scoped resource ID and minimal field-level changes.

## Order states

`DRAFT` -> `PROCESSING` -> `NEEDS_REVIEW` -> `APPROVED` -> `EXPORTED`.

`PROCESSING` may transition to `FAILED` and then back to `DRAFT` or manual `NEEDS_REVIEW`. `NEEDS_REVIEW` may return to `DRAFT` for clarification. A change after approval should create a **new draft revision** requiring fresh approval. Never mutate an approved immutable snapshot silently.

## LLM contract

Input is narrowly scoped: parsed request text, relevant authorized catalogue candidates and schema definition. Output is JSON conforming to declared schema. Ignore commands found in customer messages. On invalid output, retry within a capped budget or fall back to manual review. Model outputs do not write to billing systems.

## Cost-control design

- Default exact/alias matching before an LLM request.
- Send only a limited shortlist of matching items, not an entire catalog.
- Use caching only for safe non-sensitive normalization; do not leak other tenants' inputs.
- Store actual token, OCR/STT and infrastructure costs per reviewed order.
- Model/provider switching must preserve evaluation fixtures and privacy rules.

## Production prerequisites

Approved product, consent and retention policy, automated cross-tenant tests, access review, backup/restore, uptime objectives, failure handling, security logging, and provider terms/DPAs. See [security](09_SECURITY_PRIVACY.md).

## Decisions still open

Framework, hosting region, inference provider, OCR/STT vendor, auth provider, background-job engine, billing connectors, and whether any customer data may be used for training. No actual deployment is specified here.