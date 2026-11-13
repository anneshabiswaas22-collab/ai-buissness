# Contributing

We welcome research, design, engineering, documentation, QA and go-to-market contributions. This is currently a **planning repository**, not a functioning SaaS.

## Before you work

Read `AGENTS.md`, `PROJECT_CONTEXT.md`, the PRD and security requirements. Pick a small issue from `docs/14_DELIVERY_BACKLOG.md`. If work requires a product decision, mark it **BLOCKED — FOUNDER DECISION** rather than guessing.

## Branch and PR flow

1. Branch from `main`: `docs/<topic>`, `feat/<topic>`, `fix/<topic>`, or `research/<topic>`.
2. Write acceptance criteria and tests before changing behavior.
3. Submit a PR using `.github/PULL_REQUEST_TEMPLATE.md`.
4. Supply before/after behavior, test commands/results, cost implications and screenshots for UI.
5. Do not merge a change involving sensitive data, external integrations or bills without an explicit review.
6. Keep secrets out of code and test fixtures; use environment variable placeholders.

## Quality checklist

- Never leak information between businesses or roles.
- Orders remain drafts until an authorized human approves them.
- Unsupported SKUs, currencies, units and catalog references are surfaced; never guessed silently.
- Parsing and AI results are reproducible with offline test fixtures.
- For LLM changes include evaluation cases, baseline, cost/latency measurements and failure analysis.
- Respect accessibility, mobile usability and localization in labels/errors.
- License review for dependencies / model weights / data prior to commercial use.
- Prefer exact, understandable language over buzzwords and unsupported claims.

## Current repo limitation

There is not yet an agreed implementation language, scaffold, deployment target, CI pipeline or software license. Avoid adding a license or asserting compatibility without a founder decision. Research contributions should cite dates and trustworthy sources.

## A useful first PR

A small demo that (1) loads a fictional CSV catalogue, (2) accepts pasted order text, (3) returns candidate SKU matches with unknowns flagged, (4) allows line edits, and (5) exports **human-approved** CSV, with a test suite and README run instructions.