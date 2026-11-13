# 15 — Alternative Businesses: Short Product Briefs

These were discussed as **options**, not concurrent build commitments. Do not combine them into the wholesale order-assistant backend.

## A. Field service operations platform

**Customer:** HVAC/repair/installation/service businesses, local operations managers.  
**Problem:** Incoming jobs, scheduling, technician updates, service history and follow-ups live in scattered tools.  
**MVP:** Job intake -> technician assignment -> status tracking -> work notes -> completion -> maintenance reminder.  
**AI option:** Turn customer voice/text into structured job descriptions with operator review.  
**Monetization hypothesis:** ₹2,000–₹6,000/business/month.  
**Validation:** 15–20 owners/dispatchers, number of jobs per day, missed visits, time to assign, willingness to pay.  
**Risks:** Crowded field-service landscape, habit switching, calendar/technician coordination.

## B. Job-focused English speaking and interview coach

**Customer:** Job seekers and English learners who want realistic spoken practice, including Hindi/Bengali support.  
**Problem:** Learners lack affordable conversational practice and timely, natural corrections.  
**MVP:** Typed or push-to-talk interview scenarios, realistic voice dialogue, correction of grammar/phrasing only when appropriate, speaking feedback, progress dashboard, coach vs conversation mode.  
**Important distinction:** Respect valid regional varieties of English; don't mark an acceptable sentence "wrong" merely because American phrasing differs.  
**Low-cost architecture to evaluate:** React/TS, FastAPI, faster-whisper, a locally runnable small model via Ollama, browser TTS, and SQLite for a local demo; deployable provider selection should be based on quality/latency/cost. Codex/Astra is a **development assistant**, not automatically the consumer-facing model.  
**Monetization hypothesis:** ₹199–₹499/learner/month; conversion and inference unit economics are uncertain.  
**Validation:** Actual pronunciation/feedback quality, completion rates, 7-/30-day retention, cost per practice minute.  
**Risks:** Low consumer retention, low willingness to pay, multilingual speech latency, learner privacy and incorrect corrections.  
**Scope:** Separate product, separate roadmap/repository if selected.

## C. E-commerce delivery / return exception assistant

**Customer:** Merchants or operations teams with material delivery/returns volumes.  
**Problem:** Exceptions need staff to check carrier state, contact customer, assign owner and close out.  
**MVP:** Manual CSV/API import of authorized exceptions -> categorize -> triage queue -> owner assignment -> reviewed response draft -> status resolution and report.  
**Monetization hypothesis:** ₹5,000–₹15,000/business/month.  
**Validation:** Merchant exception volume, existing WMS/helpdesk systems, response time, cost per unresolved case, integration access.  
**Risks:** API permissions, PII, platform terms, external actions, crowded helpdesk ecosystem.

## Portfolio rule

The founder wants maximum users and growth, but **one focused product must be validated first**. Update [decision log](16_DECISION_LOG_AND_OPEN_QUESTIONS.md) before reallocating engineering time across concepts.