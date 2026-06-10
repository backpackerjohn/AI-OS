# Agent Swarm — Feature Workflows

A coordinated team ("swarm") of agents whose job is to figure out **what the user
actually wants**, **learn how the user works**, and then decide **which Claude
feature (or combination of features) will bring the most value** — and build it.

The swarm answers one recurring question:

> "Given how this user works and what they're trying to achieve, what should we
> build for them — a **Skill**, a **Sub-agent**, a **Loop**, a **Goal**, a
> **Routine**, or some combination — and is it actually worth it?"

---

## The Team

| # | Agent | Role | File |
|---|-------|------|------|
| 1 | **Requirements Drill-Down Agent** | Pins down exactly what the user wants and what "done" looks like | `1-requirements-drilldown-agent.md` |
| 2 | **Insights Agent** | Learns the user from their chat history; surfaces themes, recurring prompts, and patterns | `2-insights-agent.md` |
| 3 | **Skill Insights Agent** | Expert on Claude **Skills** — decides if a skill is the right fit | `3-skill-insights-agent.md` |
| 4 | **Sub-Agent Expert** | Expert on Claude **Sub-agents** — skill vs. sub-agent vs. sub-agent-with-skills | `4-sub-agent-expert.md` |
| 5 | **Loop Agent** | Expert on the **/loop** feature — recurring in-session work | `5-loop-agent.md` |
| 6 | **Goals Agent** | Expert on the **/goal** feature — work-until-a-condition-is-met | `6-goals-agent.md` |
| 7 | **Routine Agent** | Expert on **Routines** — durable, unattended, cloud-scheduled automation | `7-routine-agent.md` |

Agent 8 (`8-swarm-orchestrator.md`) is the convener: it runs the council, holds
the debate, and writes the final recommendation.

---

## How the swarm works (the workflow)

```
                ┌─────────────────────────────┐
   user  ─────▶ │ 1. Requirements Drill-Down  │  "What do you actually want?
                │    (the drill-down skill)   │   What does the output look like?"
                └──────────────┬──────────────┘
                               │  clear goal + definition of done
                               ▼
                ┌─────────────────────────────┐
 chat history ▶ │ 2. Insights Agent           │  themes • recurring prompts •
                │    (pattern memory)         │  pain points • confirmed patterns
                └──────────────┬──────────────┘
                               │  CONFIRMED patterns + the stated goal
              ┌────────────────┼────────────────┬───────────────┬──────────────┐
              ▼                ▼                ▼               ▼              ▼
        ┌──────────┐    ┌────────────┐   ┌──────────┐    ┌──────────┐   ┌──────────┐
        │ 3 Skill  │    │ 4 Sub-Agent│   │ 5 Loop   │    │ 6 Goals  │   │ 7 Routine│
        │ Insights │    │  Expert    │   │  Agent   │    │  Agent   │   │  Agent   │
        └────┬─────┘    └─────┬──────┘   └────┬─────┘    └────┬─────┘   └────┬─────┘
             │  Each scores: "Is MY feature the best fit? Worth the effort?"  │
             └────────────────┴───────┬────────┴───────────────┴─────────────┘
                                      ▼
                      ┌──────────────────────────────────┐
                      │ 8. Swarm Orchestrator (council)  │  debate → single
                      │  best fit • combo • or "do not   │  recommendation
                      │  build"                          │  + build plan
                      └──────────────────────────────────┘
```

1. **Drill down** (Agent 1) until the goal and the definition of "done" are
   unambiguous. Nothing downstream is reliable if this step is fuzzy.
2. **Learn the user** (Agent 2). Confirmed patterns — not guesses — are the
   currency the rest of the swarm trades in. Possible-but-unconfirmed patterns
   are logged on a watchlist, not acted on.
3. **Each feature expert (3–7) independently evaluates** whether *their* feature
   is the right tool, using the shared rubric below. Crucially, each one is
   honest enough to say *"another agent's feature fits better"* — they are not
   trying to win.
4. **The council (Agent 8) debates** and produces one recommendation: a single
   feature, a combination (e.g. *a sub-agent that bundles a skill, kicked off by
   a routine*), or **"don't build this — it isn't worth it."**

---

## Shared decision rubric (every feature expert uses this)

A feature should only be recommended when it clears these bars:

1. **Real pattern** — backed by a *confirmed* pattern from the Insights Agent,
   not a one-off.
2. **Value** — it removes real work from the user's plate, speeds them up, or
   reduces error. State the value concretely ("saves ~X min, N times/week").
3. **Fit** — the feature's mechanics actually match the need (see the
   capability cheat-sheet below).
4. **Worth it** — build/maintenance cost < value delivered. Fast/cheap enough to
   justify. If it would run too slowly or break often, say no.
5. **Honest alternative check** — explicitly consider whether a *different*
   feature, or a *combination*, would serve the user better.

Each expert returns a verdict: **STRONG FIT / POSSIBLE FIT / POOR FIT / NOT
WORTH IT**, with a one-paragraph justification and the concrete value estimate.

---

## Feature capability cheat-sheet

Use this to match a need to the right tool. (Details and limits live in each
agent file.)

| Need looks like… | Best fit |
|---|---|
| Reusable knowledge, checklist, or a repeatable workflow you keep re-typing | **Skill** |
| A specialized worker with its own context, tool limits, runs and returns a summary | **Sub-agent** |
| Reusable workflow *plus* a specialized worker to run it | **Sub-agent with a Skill** |
| Poll / check back / remind, repeatedly, **within the current session** | **Loop** (`/loop`) |
| Keep working **until a verifiable condition is true** (tests pass, queue empty) | **Goal** (`/goal`) |
| Unattended work that must run **without the user's machine on** — nightly jobs, PR-triggered, on a schedule | **Routine** |

**Quick disambiguation:**
- *Loop vs. Routine* — Loop is session-scoped and stops when the session ends;
  Routine runs on Anthropic's cloud and survives restarts (min interval 1h).
- *Skill vs. Sub-agent* — Skill = reusable instructions/knowledge in your
  context; Sub-agent = isolated worker with its own context window. Combine them
  when you want both.
- *Goal vs. Loop* — Goal monitors for a completion condition and keeps going;
  Loop fires on an interval regardless of completion.

---

## Outputs the swarm produces

- A **Requirements Brief** (Agent 1)
- A **User Pattern Report** with a confirmed-patterns list and a watchlist
  (Agent 2)
- Five **Feature Fit Verdicts** (Agents 3–7)
- A single **Build Recommendation** with rationale, the chosen feature(s), a
  build plan, and a value/cost justification (Agent 8)

> Guiding principle for the whole swarm: **maximize value to the user, not the
> adoption of any one feature.** "Do nothing" is a valid, and sometimes correct,
> recommendation.
