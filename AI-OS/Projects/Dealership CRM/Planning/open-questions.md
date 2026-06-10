# Open Questions & Action Items — Dealership CRM

*Owner: `crm-decision-scribe`. Questions stay here until resolved; resolution becomes
a decision in `decision-log.md` (note the D-ID). Each item has an owner and a status.*

| # | Question / action | Owner | Status | Resolution (D-ID) |
|---|---|---|---|---|
| Q-001 | What is the **Vehicle Selector** button supposed to do? (undefined in spec) | crm-ux-expert | Resolved | D-007 (deferred-not-shown until inventory DB exists) |
| Q-002 | What exactly should the **AI summary** be built from, and how much auto-applies vs. suggests? | crm-ai-systems-expert | Resolved | D-003 / D-004 (read-only auto summary; money/identity = suggest+confirm) |
| Q-003 | Which placeholder sidebar tiles (Inventory / Timeline / Documents / Notes) matter first, and what goes in them? | crm-project-manager | Open | — |
| Q-004 | What's the first concrete planning target the user wants to tackle? | crm-project-manager | Open | — |
| Q-005 | **Live vs. reconstructed interview** — does the salesperson capture during the conversation or write it up after? (drives paste-notes vs. live priority) | crm-project-manager / user | Open | — |
| Q-006 | **Equity ownership** — filled in real-time by the salesperson, or later by the desk manager? | crm-ai-systems-expert / user | Open | — |
| Q-007 | **Inventory DB / API availability** — is there a real inventory source to query? (unblocks Wants→Inventory and Vehicle Selector) | crm-project-manager / user | Open | — |
| Q-008 | **Book-value provider** — KBB, MMR, or Black Book for equity valuation? | crm-project-manager / user | Open | — |
| Q-009 | **ASR + call-recording consent policy** — what's permitted? (gates transcript, live transcription, objection hints) | crm-project-manager / user / legal | Open | — |
| Q-010 | **AI Discovery notes** — auto-post, or pending-by-default? (recommend pending) | crm-ai-systems-expert | Open | — |
| Q-011 | **CRM access** for enrichment / dedupe — do we have read/write access to the source CRM? | crm-project-manager / user | Open | — |
| Q-012 | **System-of-record for new identity** — is this page where new identity originates, or does it come from upstream? (affects license-scan) | crm-ux-expert / user | Open | — |

---

### Action items
- [ ] PM to frame the first substantive planning round and confirm priorities with the user.
