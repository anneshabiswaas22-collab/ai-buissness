# Agent / Developer Handoff — READ FIRST

This document governs work in this repository by human developers, Codex, or other AI coding tools.

## Mission

Explore and validate an AI software business with a large potential user/customer base and sustainable economics. The lead **proposal** is an AI-assisted wholesale order-intake workflow, **not** a selected or launched product. Build only what is justified by customer evidence or an explicit instruction.

## First reading order

1. `PROJECT_CONTEXT.md` — confirmed facts vs recommendations vs proposed decisions.
2. `README.md` and `docs/01_VISION_AND_STRATEGY.md`.
3. `docs/03_PRIMARY_PRODUCT_PRD.md`, `docs/04_USER_STORIES_AND_WORKFLOWS.md`.
4. `docs/09_SECURITY_PRIVACY.md` and `docs/08_AI_PIPELINE_AND_EVALUATION.md`.
5. `docs/12_ROADMAP_90_DAYS.md`, `docs/14_DELIVERY_BACKLOG.md`.

## Allowed next moves

- Draft interview guides, test hypotheses, and prototype screens backed by the PRD.
- Build a **minimal, local-only demo**: upload a CSV catalogue, paste a customer message, extract line-item proposals, match only known SKUs, review/correct, approve and export CSV.
- Add tests/evaluation fixtures before plugging in expensive AI components.
- Keep architecture swappable; benchmark deterministic parsing / retrieval before large model calls.

## Forbidden assumptions

- Do not declare a product choice final without founder approval.
- Do not claim paying customers, production readiness, integrations, benchmark gains, or prices as facts without evidence.
- Do not auto-submit orders, charge customers, message external contacts, access real accounts or deploy infrastructure merely because these docs describe possible features.
- Do not collect/store customer orders, phone numbers, photos or recordings without data controls, permission and retention policy.
- Do not commit keys, customer payloads, paid data, model weights with incompatible licenses or third-party copyrighted assets.
- Do not merge unrelated AI-video / media projects into this product.

## Engineering quality bar

- Strong schema validation and explicit tenant identity from authenticated server context; never trust `tenant_id` in client input.
- Every extracted line carries provenance and a confidence/ambiguity indication.
- Exact SKU matches should be deterministic; unknown matches are flagged and reviewed.
- Review/approve is auditable and idempotent; no hidden side effects from AI generation.
- Unit, integration, cross-tenant isolation and adversarial prompt-injection tests are part of acceptance.
- Tests must run locally with fixtures and **no mandatory paid API keys**.
- Accessible UI (keyboard, clear states, plain English), India-friendly performance and costs.
- Use small focused PRs. Describe changed behavior, validation, screenshots (for UI), risks and open decisions.

## Definition of done for a milestone

Documented acceptance criteria pass; tests and lint pass; costs and limitations recorded; no unapproved external effects; docs and decision log updated if needed. Label experimentation results as actual data or untested hypotheses.

## Initial deliverable sequence

Discovery script -> anonymized sample orders + catalogue -> basic wireframe -> extraction and match contracts -> local review/export demo -> eval suite -> pilot gate. No production integrations until authorized.

For specifics, consult the linked docs rather than inventing scope.