# Project Context, Provenance & Decision Status

## What the founder actually requested

On **2026-10-28**, in the project conversation titled **AI Business Ideas**, the founder asked for detailed software / business ideas suitable for the AI era, with an overriding ambition to attract as many users as possible and grow the business. The founder favors practical, affordable development and has discussed using Codex / GPT-6 Astra for implementation. **No final business selection or product budget approval is evidenced.**

On **2026-11-13**, the founder requested that all available project-related context be pushed to this repository so a developer or AI coding agent could understand it without chat access.

## Recovered recommendation from the 2026-10-28 discussion

The prior recommendation ranked an **AI Order Assistant** first: convert messy distributor/wholesale customer messages, voice, and photos into catalogue-matched draft orders; ask for clarification; require employee review; and export to billing. A first possible target niche was **electrical wholesalers**. It was differentiated from basic WhatsApp chatbots and Tally/invoicing products by focusing on **incoming order interpretation and review**.

Other researched idea categories were:
- Service-operations system for scheduling / tracking technicians and jobs.
- Job-focused English speaking and interview coaching application.
- E-commerce delivery and returns exception assistant.

Suggested discovery approach: **weeks 1–2** ~20 customer interviews, **weeks 3–4** demo and ~3 paid pilots, **weeks 5–8** build the repeated workflow, **weeks 9–12** assess renewals / results / referrals. Suggested validation spend cap: **₹25,000–₹75,000**, to be treated as an exploratory ceiling rather than a committed budget. Suggested subscription ranges and economics remain hypotheses.

## Source-of-truth labels

All contributors MUST use the following meanings:

- **CONFIRMED USER GOAL**: The user explicitly said this (e.g. maximize users, growth, request reusable developer handoff).
- **PRIOR RECOMMENDATION**: A suggestion made in the earlier assistant response, **not** proof that the user selected it.
- **PROPOSED SPECIFICATION**: Details authored in this repository to make implementation feasible; subject to validation.
- **OPEN DECISION**: Requires founder approval or customer discovery.
- **IMPLEMENTED / VERIFIED**: Only used with code, tests or evidence actually present in the repository.

Never turn a recommendation into an approved decision through repetition.

## Current authoritative status

| Topic | State |
| --- | --- |
| Business objective | CONFIRMED USER GOAL |
| AI Order Assistant first | PRIOR RECOMMENDATION |
| Electrical wholesalers pilot niche | PRIOR RECOMMENDATION |
| ₹3k–₹8k monthly wholesale pricing | PRIOR RECOMMENDATION / TEST HYPOTHESIS |
| Specific tech stack, UX, API and schema | PROPOSED SPECIFICATION |
| Third-party WhatsApp or accounting integration | NOT IMPLEMENTED / approval, terms and feasibility pending |
| Repository application code or deployment | NOT IMPLEMENTED at handoff |
| Customer interviews / paying pilots | NOT VERIFIED |
| Founder final product choice | OPEN DECISION |
| Team, legal entity, brand, geographic roll-out | OPEN DECISION |

## Adjacent exploration, not this repository's implementation scope

A separate conversation discussed an **AI English-speaking tutor** that converses naturally and helps Hindi/Bengali speakers practice, correct their English and build confidence, preferably with low operating cost. This overlaps with portfolio idea #3; see [alternative briefs](docs/15_ALTERNATIVE_PRODUCT_BRIEFS.md). Other AI movie/video/editor and interview projects may be separate ventures, but must **not** be silently merged into this codebase.

## How to keep this repository trustworthy

1. Keep claims evidence-bound; add interview notes / experiment records (redacted) when available.
2. Update [decision log](docs/16_DECISION_LOG_AND_OPEN_QUESTIONS.md) when a decision is actually made.
3. Distinguish discovery plans from build requirements in issues and PRs.
4. Keep sensitive customer data, raw chats, credentials and personal identifying information out of Git.
5. If a developer starts tomorrow, they should first read this file and then [AGENTS.md](AGENTS.md).