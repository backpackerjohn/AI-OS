# Decision Log — Dealership CRM

*Owner: `crm-decision-scribe`. ADR-lite. Newest entries at the top. A decision is
never deleted — when superseded or reversed, its **Status** is updated and the new
entry references it.*

---

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
