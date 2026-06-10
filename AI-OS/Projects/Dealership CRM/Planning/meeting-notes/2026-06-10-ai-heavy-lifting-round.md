# Planning Note — 2026-06-10 — Make AI do the heavy lifting (review round)

- **Attendees:** User + UX, UI, Usability, AI Systems experts + PM (synthesis) + Scribe
- **Goal of session:** Review the wireframe through all four expert lenses, decide how
  much real work AI should do on the Unsold Customer page, and have the PM synthesize a
  phased plan that ships LLM-only wins first and fences off integration work.

## Agenda
- Each expert reviews `customer-detail-wireframe.html` independently.
- Find points of convergence across lenses.
- Lock decisions on the AI trust model and the flagship feature.
- PM synthesizes a phased roadmap; Scribe records.

## Discussion
Strong, independent convergence across all/most experts:
- **Three-state field styling** (read-only / editable / AI-suggested) is gating pre-work
  — today editable vs. read-only are visually indistinguishable. (UI, UX, Usability)
- **Nothing AI touches commits silently** — money/identity must be suggest + tag +
  one-tap-confirm. (AI Systems, Usability)
- **One spine** — kill the two competing starts (Start Interview vs. the undefined
  Vehicle Selector). (UX, UI)
- **"Set next step"** belongs in the interview exit, AI-proposed. (UX, AI Systems)
- **Flagship = talk → structured extraction** into the existing data-sync keys, with a
  ship order of paste-notes → post-call transcript → live. (AI Systems)
- **Trade form conflates** live discovery with back-office payoff/banking; lien block
  should default closed. (UX, UI)
- **AI summary + notes need** skeleton / loading / empty / error states. (UI, Usability)

Key trade-offs raised:
- Money must be deterministic, not model-recalled — book value via external API, equity
  by subtraction, per-diem by arithmetic; AI only badges an "Est." suggestion (`D-005`).
- Build the extraction call **once** and feed it richer sources over time, rather than
  per-source extractors (`D-004`).
- Tier models to task weight — Opus for flagship reasoning, Haiku/Sonnet for summary and
  simple extraction; re-verify ids against the claude-api skill at build (`D-006`).

## Decisions
- **D-002** — Three field-states + primitives as Phase-0 pre-work — ships before any AI
  write (logged in `decision-log.md`).
- **D-003** — Core AI policy: money/identity suggest+confirm, AI Summary the only auto
  read-only artifact, lender block / merges / outbound never auto-written.
- **D-004** — Flagship: one structured-output extraction call → existing data-sync keys;
  paste-notes first, then transcript, then live.
- **D-005** — Money is deterministic — external book-value API, equity = book_value −
  payoff, arithmetic per-diem; AI only badges an "Est." suggestion.
- **D-006** — Model tiers — Opus for flagship; Haiku/Sonnet for summary + simple
  extraction (confirm vs. claude-api skill).
- **D-007** — One spine — collapse competing primary actions; Vehicle Selector
  deferred-not-shown until an inventory DB exists.

## Action items
- [ ] Build Phase 0 field-states + primitives in the wireframe — owner: UI — next step:
  add read-only/editable/AI-suggested states + `.skeleton` / `.field.is-error` /
  `.empty` / one-tap accept-reject. **(Smallest next action — gates everything.)**
- [ ] Collapse to one spine + anchor the action row — owner: UX → UI — next step:
  remove the undefined Vehicle Selector start.
- [ ] Stand up the single extraction call (paste-notes source) — owner: AI Systems —
  next step: confirm models against claude-api skill, then build.

## Open questions
- Q-005 — Live vs. reconstructed interview (drives paste-notes vs. live) — owner: PM/user
- Q-006 — Equity ownership: salesperson real-time vs. desk manager later — owner: AI/user
- Q-007 — Inventory DB / API availability (unblocks Wants→Inventory) — owner: PM/user
- Q-008 — Book-value provider (KBB / MMR / Black Book) — owner: PM/user
- Q-009 — ASR + call-recording consent policy (gates transcript/live/objection hints) —
  owner: PM/user/legal
- Q-010 — AI Discovery notes auto-post vs. pending-by-default (recommend pending) —
  owner: AI
- Q-011 — CRM access for enrichment / dedupe — owner: PM/user
- Q-012 — Is this page system-of-record for new identity (affects license-scan) —
  owner: UX/user
- Q-001 (Vehicle Selector) — **resolved** by D-007; Q-002 (AI summary scope) —
  **resolved** by D-003 / D-004.
  (all mirrored in `open-questions.md`)
