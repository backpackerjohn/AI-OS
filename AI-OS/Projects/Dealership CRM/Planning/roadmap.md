# Roadmap — Dealership CRM (Unsold Customer page)

*Owner: `crm-project-manager`. Living document. Priorities are value-to-salesperson
vs. effort. Decisions that change this roadmap are recorded in `decision-log.md`.*

*Last refreshed: 2026-06-10 by the PM, after the "Make AI do the heavy lifting"
review. Phased so that LLM-only quick wins ship early and integration-dependent work
is honestly fenced off behind its dependencies.*

---

## Phase 0 — Foundation (gates everything)
_Must ship before any AI write. Makes the suggest/confirm trust model visible and
enforceable._

| Item | Owner agent(s) | Status | Notes |
|---|---|---|---|
| Three field-states (read-only / editable / AI-suggested) + primitives (`.skeleton`, `.field.is-error`, `.empty`, one-tap accept/reject) | UI | ⏭️ Next | `D-002`. Gates all AI writes. **Smallest next action.** |
| Button system + states; anchor the action row | UI | ⏭️ Next | Supports the single-spine collapse (`D-007`). |

## Phase 1 — LLM-only quick wins (parallel, after Phase 0)
_No external integration required — pure LLM + existing data-sync keys._

| Item | Owner agent(s) | Status | Notes |
|---|---|---|---|
| One spine — collapse the two competing primary actions | UX → UI | ⏭️ Next | `D-007`. Defer Vehicle Selector (not shown). |
| AI Summary (auto, read-only) | AI | ⏭️ Next | `D-003`. Only auto-generated artifact. |
| **FLAGSHIP v1** — paste-notes → interview extraction | AI | ⏭️ Next | `D-004`. One structured-output call; paste-notes source first. |
| AI Discovery notes | AI | ⏭️ Next | Pending-by-default recommended (see Q-010). |
| Next-best-action into the interview exit | UX → AI | ⏭️ Next | AI-proposed "set next step" at interview exit. |
| Trade form split (live discovery vs. back-office) + lien default closed | UI → UX | ⏭️ Next | Separates discovery from payoff/banking. |

## Phase 2 — Needs integration (fenced on dependencies)
_Each blocked on an external system; do not start until its dependency lands._

| Item | Owner agent(s) | Status | Blocked on |
|---|---|---|---|
| Wants → Inventory / Vehicle Selector | UX / UI / AI | 💤 Parked | Inventory DB (Q-007) |
| Trade payoff / equity | AI | 💤 Parked | Book-value API (Q-008); equity = book_value − payoff per `D-005` |
| License-scan → identity | UX / AI | 💤 Parked | Scan path; system-of-record question (Q-012) |
| Lead enrichment / dedupe | AI | 💤 Parked | CRM access (Q-011) |

## Phase 3 — Later bets
- Post-call transcript (feeds the same flagship extraction call, `D-004`).
- Live transcription.
- Objection hints.

## Out of scope (this round)
- Live transcription & objection hints — need ASR + consent policy (Q-009).
- Auto-writing the lender payoff/banking block — forbidden by `D-003`.
- Silent record merge — forbidden by `D-003`.
- Full inventory search UX — gated on a real inventory DB (Q-007).
- Model-memory book values — forbidden by `D-005` (use external API).

---

### Smallest next action
**UI builds the Phase 0 field-states + primitives in the wireframe** —
everything else is gated on it.

### Legend
✅ Done · 🟡 In progress · ⏭️ Next · 💤 Parked
