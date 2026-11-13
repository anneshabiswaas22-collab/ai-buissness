# 14 — Prioritized Delivery Backlog

**Status:** Planning queue / not evidence of work completed.

Every task needs: problem, scope, acceptance, test/evidence, and owner. Use GitHub issues to claim work; this file is the initial source-of-truth.

## Discovery / blocker queue

| ID | Priority | Task | Definition of done | Dependency |
| --- | --- | --- | --- | --- |
| DISC-01 | BLOCKER | Founder selects first opportunity | Written decision captured in decision log | Founder |
| DISC-02 | P0 | 20 buyer interviews | Redacted insights and observed workflow measures | Outreach |
| DISC-03 | P0 | Pilot niche and ideal customer profile | Evidence-based ICP description | DISC-02 |
| DISC-04 | P0 | Validate price/paid pilot terms | Recorded offers and responses | DISC-02 |
| DISC-05 | P0 | Data consent, retention and processing rules | Approved policy / contracts | Legal/security |
| DISC-06 | P0 | Choose approved implementation stack and license | ADR with alternatives and rationale | Founder / tech lead |

## Design / prototyping

| ID | Priority | Task | Definition of done |
| --- | --- | --- | --- |
| DES-01 | P0 | Synthetic 20+ SKU catalog fixture | Includes duplicate and variant cases |
| DES-02 | P0 | Synthetic ambiguous message fixture set | 50+ cases across normal/error/injection paths |
| DES-03 | P0 | Review screen design | Customer can find uncertain lines and correct them |
| DES-04 | P0 | Manual CSV template | Pilot-specific columns verified with fake export |
| DES-05 | P1 | Onboarding UX | Error handling and upload preview documented |

## Engineering MVP

| ID | Priority | Task | Definition of done |
| --- | --- | --- | --- |
| ENG-01 | P0 | Repository scaffold + local test command | Clean clone runs tests without paid API |
| ENG-02 | P0 | Catalogue CSV parser + validation | Duplicate/missing/error tests |
| ENG-03 | P0 | Deterministic SKU / alias matcher | Tenant-scoped, never fabricates SKU |
| ENG-04 | P0 | Extractor interface + fake/LLM adapters | Strict schema, timeout/manual fallback |
| ENG-05 | P0 | Order state machine | Invalid transitions rejected, revisions immutable |
| ENG-06 | P0 | Human review UI | Keyboard, accessible and mobile-usable |
| ENG-07 | P0 | Export CSV + idempotency | Only approved, no duplicate effects |
| ENG-08 | P0 | Tenant auth/RBAC | Cross-tenant, revoked access tests |
| ENG-09 | P0 | Protected uploads (if enabled) | Validation, privacy and retention tests |
| ENG-10 | P0 | Audit + redacted telemetry | No sensitive payloads in logs |
| ENG-11 | P1 | OCR/STT adapters | Proven value, provider permission, eval and cost |

## Quality / release

| ID | Priority | Task | Definition of done |
| --- | --- | --- | --- |
| QA-01 | P0 | Offline evaluation CI | Baseline stored; critical-error failures visible |
| QA-02 | P0 | Threat-model verification | Cross-tenant, injection, approval and replay tests |
| QA-03 | P0 | Cost and performance trial | Actual per-order spend and p95 latency measured |
| QA-04 | P0 | Pilot runbook and recovery plan | Reviewers know how to stop, correct and delete |
| GTM-01 | P0 | Approved pricing / trial offer | Actual buyer acceptance evidence |
| GTM-02 | P1 | Case study / referrals | Consent and verified outcomes |

## Correct execution order

Until DISC-01 and DISC-05 are resolved, prefer **documentation, interviews, design and synthetic local prototypes**. Never treat this list as authorization to connect paid services, launch publicly, or process real customer data.