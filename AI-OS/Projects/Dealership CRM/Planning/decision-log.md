# Decision Log — Dealership CRM

*Owner: `crm-decision-scribe`. ADR-lite. Newest entries at the top. A decision is
never deleted — when superseded or reversed, its **Status** is updated and the new
entry references it.*

---

### D-007 — One spine: collapse the two competing primary actions
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** The page currently offers two competing starts — "Start Interview"
  and an undefined "Vehicle Selector" — leaving no single clear path through the job.
- **Decision:** Collapse to one spine. "Vehicle Selector" is **deferred-not-shown**
  until an inventory DB exists, rather than shipping an undefined button. The interview
  is the single primary action.
- **Options considered:**
  - **One spine, defer Vehicle Selector (chosen)** — removes ambiguity now; honest
    about the missing inventory dependency.
  - Ship Vehicle Selector as a stub — rejected; an undefined button erodes trust and
    teaches a dead end.
  - Keep both starts — rejected; two primary actions = no primary action.
- **Consequences / trade-offs:** Clearer first move for the salesperson; the
  Wants→Inventory flow waits on a real inventory source (see Q-007).
- **Owner / driver:** crm-ux-expert / crm-ui-expert.
- **Affects:** `customer-detail-wireframe.html` (action row, primary CTA).
- **Resolves:** Q-001.

### D-006 — Model tiers for AI features
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** AI features span heavy structured reasoning (flagship extraction) and
  lightweight generation (summary, simple extraction); one model for all is wasteful
  or under-powered.
- **Decision:** Tier the models — **`claude-opus-4-8`** for flagship extraction /
  reasoning; **`claude-haiku-4-5` / `claude-sonnet-4-6`** for the AI Summary and simple
  extraction. Confirm exact model ids and limits against the **claude-api skill**
  before build.
- **Options considered:**
  - **Tiered by task weight (chosen)** — cost/latency fit to each call.
  - Single flagship model everywhere — rejected; overpays for summaries.
  - Single cheap model everywhere — rejected; under-powers structured extraction.
- **Consequences / trade-offs:** Better cost/latency profile; two integration paths to
  maintain. Model ids must be re-verified against the claude-api skill at build time.
- **Owner / driver:** crm-ai-systems-expert.
- **Affects:** whole page (all AI calls).

### D-005 — Money is deterministic, not AI
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** Trade equity, payoff, and per-diem math are money-critical. A model
  recalling "book values" from memory is both wrong and untrustworthy.
- **Decision:** Money is computed deterministically. **Book value** comes from an
  **external API** (never model memory); **equity = book_value − payoff** (subtraction);
  **per-diem / 20-day** figures are arithmetic. AI may only present a clearly badged
  **"Est."** valuation suggestion — never a committed number.
- **Options considered:**
  - **Deterministic math + external book-value API (chosen)** — auditable, correct.
  - Let the model estimate values — rejected; non-reproducible, legally risky.
- **Consequences / trade-offs:** Trustworthy money; introduces a book-value provider
  dependency (see Q-008) and gates equity on integration (Phase 2).
- **Owner / driver:** crm-ai-systems-expert.
- **Affects:** Trade payoff/equity block.

### D-004 — Flagship: one structured-output extraction call
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** The flagship value is talk → structured fields. Building separate
  extractors per input source would fragment the work.
- **Decision:** One structured-output extraction call returns
  `{value, confidence, source_span}` per field into the **existing data-sync keys**.
  Build the call once; feed it from progressively richer sources — **paste-notes
  (ship first)**, then **post-call transcript**, then **live transcription**.
- **Options considered:**
  - **Single extraction call, multiple input sources (chosen)** — build once, reuse.
  - Per-source bespoke extractors — rejected; triples the work and drifts.
- **Consequences / trade-offs:** One well-tested path; requires confidence + source
  span plumbed into the field-state UI (depends on D-002).
- **Owner / driver:** crm-ai-systems-expert.
- **Affects:** interview extraction, data-sync keys, AI-suggested field state.
- **Resolves:** Q-002 (with D-003).

### D-003 — Core AI policy: nothing money/identity commits silently
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** AI that silently writes money or identity fields is untrustworthy and
  unsafe in a sales context.
- **Decision:** **Money/identity fields are suggest + tag + one-tap-confirm, never
  silent.** The **AI Summary** is the only auto-generated (read-only) artifact. The
  **lender payoff/banking block, record merges, and outbound actions are NEVER
  auto-written.**
- **Options considered:**
  - **Suggest/confirm for money & identity; auto only for read-only summary (chosen)**
    — keeps a human on every consequential write.
  - Auto-apply high-confidence extractions — rejected; confidence ≠ consent.
  - Manual entry only, no AI writes — rejected; throws away the flagship value.
- **Consequences / trade-offs:** Trustworthy by construction; adds a confirm tap on
  suggested writes (cheap given one-tap accept/reject from D-002).
- **Owner / driver:** crm-ai-systems-expert.
- **Affects:** whole page.
- **Resolves:** Q-002 (with D-004).

### D-002 — Three field-states + primitives as Phase-0 pre-work
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** Today editable and read-only fields are visually indistinguishable, so a
  suggest/confirm trust model can't be expressed on screen. This gates all AI writes.
- **Decision:** Adopt three field-states — **read-only / editable / AI-suggested** —
  plus new primitives (`.skeleton`, `.field.is-error`, `.empty`, one-tap
  accept/reject). Ships as **Phase-0 foundational pre-work, BEFORE any AI write.**
- **Options considered:**
  - **Build field-states + primitives first (chosen)** — makes the suggest/confirm
    model enforceable and visible.
  - Add AI writes onto the current undifferentiated fields — rejected; users can't tell
    what's theirs, what's the system's, or what's a suggestion.
- **Consequences / trade-offs:** A short pre-work phase before any AI ships, in exchange
  for a coherent, enforceable trust model across every later feature.
- **Owner / driver:** crm-ui-expert.
- **Affects:** `customer-detail-wireframe.html`.

### D-001 — Stand up a planning agent team + planning docs
- **Date:** 2026-06-10
- **Status:** Accepted
- **Context:** We need structured help to plan functionality for the Unsold Customer
  page and to grow the wireframe deliberately rather than ad hoc.
- **Decision:** Create six specialized planning subagents (Project Manager, UX Expert,
  UI Expert, Usability Advocate, AI Systems Expert, Scribe/Decision-Log) in
  `.claude/agents/`, plus a `Planning/` documentation scaffold (README, roadmap,
  decision log, open questions, meeting notes).
- **Options considered:**
  - **Six agents + combined Scribe (chosen)** — full role coverage; note-taker and
    decision-log merged into one Scribe since they share source material and format.
  - Separate note-taker and decision-log agents — rejected as redundant overlap.
  - No dedicated agents, plan inline — rejected; loses reusable, role-specific lenses.
- **Consequences / trade-offs:** Reusable, named lenses for every planning question
  and a durable paper trail; small upkeep cost to keep agent prompts and docs current.
- **Owner / driver:** User request, set up by the team.
- **Affects:** `.claude/agents/crm-*.md`, `AI-OS/Projects/Dealership CRM/Planning/*`
