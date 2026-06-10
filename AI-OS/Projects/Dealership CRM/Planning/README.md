# Dealership CRM — Planning

Planning workspace for the desktop **"Customer Detail / Adding Unsold Customer"**
page. This is where the planning team frames work, makes decisions, and evolves the
wireframe.

## What we're building

A desktop page used by a **car salesperson** to capture and work an **unsold lead**:
classify the lead source and contact method, run a structured **interview**
(Vehicle / Features / Trade / Payment), capture **trade-in + payoff** details, set
**goals**, and manage **follow-up cadence and notes** — with AI assisting via a
customer summary, discovery notes, and live auto-fill. Speed and low friction during
a live customer conversation are the north star.

### Source artifacts
| Thing | Path |
|---|---|
| Interactive wireframe | `../Browser Customer Input Wireframe and Planning/customer-detail-wireframe.html` |
| Layout spec | `../Browser Customer Input Wireframe and Planning/desktop-adding-customer-unsold-page.md` |

## The planning team (subagents)

Defined in `.claude/agents/` at the repo root. Invoke by name (e.g. "have the
**crm-ux-expert** review the interview flow").

| Agent | Role | Use it for |
|---|---|---|
| `crm-project-manager` | Project Manager | Scope, sequencing, priorities, risks, roadmap; frames and closes each planning round |
| `crm-ux-expert` | UX Expert | User flows, information architecture, journeys, friction |
| `crm-ui-expert` | UI Expert (+ builder) | Visual hierarchy, components, states, and **editing the wireframe HTML** |
| `crm-usability-advocate` | Usability / Functionality | "Is it easy to get to? Is there an easier way?" — simplify, reduce clicks, cut clutter |
| `crm-ai-systems-expert` | AI Systems Expert | AI summary, discovery notes, interview auto-fill, payoff/equity estimates, next-best-action |
| `crm-decision-scribe` | Scribe + Decision Log | Captures notes, logs decisions, tracks open questions/actions |

## How a planning round works

1. **Frame** — `crm-project-manager` states the goal, scope, and what's out.
2. **Explore** — UX, UI, Usability, and AI agents weigh in on their facets. Usability
   pressure-tests for reachability and simpler alternatives.
3. **Prototype** — `crm-ui-expert` realizes accepted changes directly in the wireframe.
4. **Decide & record** — PM lands the decisions; `crm-decision-scribe` logs them and
   updates open questions.
5. **Sequence** — PM updates `roadmap.md` with what's next.

You can run agents in parallel for independent facets, or in sequence when one's
output feeds another (UX flow → UI build → Usability check → Scribe log).

## Documents in this folder

| File | Owner | Purpose |
|---|---|---|
| `README.md` | PM | This overview |
| `roadmap.md` | `crm-project-manager` | Phases, in-progress, backlog, parked ideas |
| `decision-log.md` | `crm-decision-scribe` | Authoritative decisions (ADR-lite, newest first) |
| `open-questions.md` | `crm-decision-scribe` | Unresolved questions + action items, with owners |
| `meeting-notes/` | `crm-decision-scribe` | One note per planning session (`0000-template.md` is the template) |
