# Dealership CRM — CLI Goals

*A plain-language statement of **what** this CLI should do — its purpose, who drives it, and the jobs it must handle. This is intentionally **not** about backend design, storage, syntax, or implementation. It's the "what good looks like" we'll measure the build against.*

---

## 1. Purpose in one sentence

A command-line interface to the dealership CRM that an **AI agent operates** — so a person can prompt the agent with intent ("follow up with every unsold walk-in from last week") and the agent carries it out by running CLI commands against the CRM.

---

## 2. Who uses it

- **Primary operator: an AI agent** (a Claude sub-agent). The CLI is the agent's *hands* — the surface it acts through. Every design choice favors "easy and safe for an agent to drive."
- **Indirect user: the human** (salesperson / manager). They never type CLI commands themselves; they prompt the agent in natural language, and the agent does the typing.
- **Phasing:** First goal is simply **get the CLI working and reliable**. *Then* we wrap it as a Claude sub-agent we can prompt with different criteria.

---

## 3. Relationship to the existing (browser) CRM

The CRM already has a **browser interface** (see the customer-detail wireframe — humans clicking through customer pages). The CLI is a **second front door to the same CRM and the same data.**

| | Browser UI | CLI |
|---|---|---|
| Who drives it | A human, point-and-click | The AI agent, typed commands |
| Best at | Reading, judgment, manual edits | Repetitive, bulk, scripted, "do X for all matching Y" |
| Source of truth | **Same underlying CRM data** | **Same underlying CRM data** |

**Goal — parity:** anything the agent does through the CLI shows up in the browser, and anything a human does in the browser is visible to the CLI. They are two ways to operate one system, never two separate systems that drift apart.

---

## 4. Core jobs

The three job areas you picked, made concrete against this CRM's actual domain (customers, vehicles, trades, payment goals, lead sources, follow-ups, notes, interviews).

### Job A — Contact & record management *(create and maintain records)*

The agent can fully manage a customer's record through its whole lifecycle:

- **Create** a new customer record.
- **Open / read** a single customer's full profile.
- **Update** any part of the record:
  - Customer Info (name, DOB, phone, email, address, driver's license).
  - Status (e.g. Unsold → Sold), Lead Source (Walk-In / CRM / Referral / Social + sub-source), Contact method.
  - Insurance, New Vehicle of interest, Trade-in details, Payment Goals.
  - Customer Wants (desired vehicle type + features).
- **Notes** — add a note, tagged by origin (AI Discovery vs Manual Entry) with a timestamp.
- **Follow-ups** — add / edit / complete custom follow-ups (date + reason) and relationship cadence (last contacted, next due).
- **Lifecycle** — archive / restore a customer; ideally find and merge duplicates.

**Done looks like:** the agent can take a customer from "new lead" to "sold or closed" without anyone touching the browser.

### Job B — Querying & reporting *(read and answer questions)*

The agent can find records and answer questions about the pipeline:

- **Find customers by criteria** — status, lead source, salesperson, date ranges, vehicle interest, cadence due/overdue, has-trade, paying-cash, etc. (filters should combine).
- **Worklists** — "who needs follow-up today," "who's overdue," "new leads with no first contact yet."
- **Single-record pull** — the complete profile for one customer.
- **Aggregate reports** — counts and breakdowns: by status, by lead source, leads over a time window, pipeline snapshot, simple conversion view.
- **Output that's useful two ways** — structured enough for the agent to act on the results, and readable enough for a human to glance at.

**Done looks like:** the agent can answer "what's my pipeline look like and who do I owe a call?" and immediately act on the list it gets back.

### Job C — Workflow automation *(act in sequences, across many records)*

The agent can carry out multi-step and bulk work, not just one edit at a time:

- **Cadence / follow-up automation** — surface everyone due, mark them contacted, advance the cadence to the next step.
- **Bulk actions** — apply the same change (note, status, follow-up, tag) across a filtered set, e.g. "all unsold walk-ins from last week."
- **Intake play** — run an interview-style intake that fills Customer Wants, Trade, and Payment Goals in one guided sequence.
- **New-lead routine** — on a new lead, set lead source, assign owner, schedule the first follow-up.
- **Drafting outreach** — compose a follow-up text/email *draft* tied to a customer for a human to review/send (decide later whether the CLI ever sends directly).

**Done looks like:** you prompt the agent with a criteria, and it runs an entire play end-to-end across all matching customers.

---

## 5. Qualities the CLI must have (still "what," not "how")

Because an **AI agent** is the operator, these matter as much as the features:

- **Predictable & composable** — same input → same result; commands can be chained so the agent can build sequences.
- **Legible output** — consistent, structured responses the agent can reliably parse and chain.
- **Safe by default** — bulk and destructive actions support a preview / dry-run and/or confirmation, so a bad prompt can't quietly wreck many records.
- **Idempotent where possible** — re-running a command shouldn't create duplicates or double-apply.
- **Auditable** — every change the agent makes is attributable and logged (who/what/when), so we can trust and review the AI's actions.
- **Self-describing** — the agent can ask the CLI what commands and options exist, so it can discover capabilities instead of guessing.

---

## 6. Explicit non-goals (for now)

- Not the human's primary interface — that's the browser CRM.
- Not a redesign of the backend, database, or storage.
- Not natural-language understanding *inside* the CLI — Claude does the interpreting; the CLI takes clear commands.
- Not (yet) a decision on the CLI sending live texts/emails on its own.

---

## 7. Success criteria

> You can prompt Claude with a set of criteria, and it can run the full customer lifecycle — create, find, update, report, and automate follow-ups — entirely through the CLI, with results that match what a human would see in the browser, and a log of everything it did.

---

## 8. Open decisions (flag these before/while building)

- **Send vs. draft:** does the CLI ever send outreach directly, or only prepare drafts for a human?
- **Bulk safety:** confirmation step, dry-run preview, or both — and above what size?
- **Multiple users/owners:** does the CLI need a notion of "which salesperson" for assignment and reporting from day one?
- **Merge/dedupe:** in the first version, or later?
- **Report scope:** which few reports are worth having on day one vs. nice-to-have later?
