# Day Trading Market Analysis — Agent Team

A team of cooperating AI subagents that spot **intraday crypto day-trading
opportunities** on assets a **US retail user can actually trade** (Coinbase
first; Kraken/Gemini fallback). The team reads charts, researches the news
driving moves, weeds out bad/false signals, produces a ranked list of paper
trades with entry/exit plans, "enters" them at the live price, and later checks
whether it was right — **tracking everything so it improves over time.**

> ⚠️ **Simulation only.** This system produces paper trades for research and
> learning. Nothing here is financial advice. Crypto day trading is high-risk;
> most retail day traders lose money.

---

## The team

| Agent | Role | Subagent file |
|---|---|---|
| **Lead Analyst** | Orchestrates the session, sets the regime read, synthesizes the final ranked list, makes the call | `.claude/agents/daytrading-lead-analyst.md` |
| **Market Scanner** | Finds liquid, US-tradable candidates (movers, volume, volatility, ranges) | `.claude/agents/daytrading-market-scanner.md` |
| **Chart Technician** | Reads structure: support/resistance, trend, RSI/MA/volume, setup type | `.claude/agents/daytrading-chart-technician.md` |
| **News Researcher** | Finds the catalyst behind each move + scheduled event risk + macro tone | `.claude/agents/daytrading-news-researcher.md` |
| **Signal Validator** | The skeptic. Scores signals 0-100, vetoes false/illiquid/exhausted/priced-in signals | `.claude/agents/daytrading-signal-validator.md` |
| **Risk Strategist** | Entry, stop, targets, R:R, position size, management rules | `.claude/agents/daytrading-risk-strategist.md` |
| **Trade Journalist** | Logs paper trades, scores outcomes, updates the learning files | `.claude/agents/daytrading-trade-journalist.md` |

---

## How to run it

In Claude Code, from the repo root, just say:

- **"Run the day trading analysis"** → Lead Analyst runs the full session runbook
  and produces a fresh ranked list of paper trades, logged to the journal.
- **"Review our open trades"** → Journalist marks open trades to current price,
  closes the ones that hit stop/target/time-stop, scores them, and updates the
  learning files.
- **"Find me day trades in {sector/coin}"** → scoped scan + analysis.

The Lead Analyst dispatches each specialist via the Agent tool in this order:

```
Regime read → Scanner → (Technician ∥ News Researcher) → Signal Validator
→ Risk Strategist → Synthesize & rank → Journalist logs paper entries
→ [later] Journalist reviews & updates learning files
```

---

## How it learns (the loop)

Every session reads the learning files first and writes back to them after:

- `data/strategies.md` — each setup's running **win-rate & expectancy**. Winning
  setups get promoted; losing ones get demoted or retired.
- `data/signals-glossary.md` — each signal's **reliability score**, nudged up/down
  by outcomes. This re-weights what the Validator trusts next time.
- `data/lessons-learned.md` — dated, specific, actionable takeaways + the next
  experiment to run.
- `data/performance-summary.md` — equity curve, win-rate, avg R, per-setup stats.

Over many sessions the team should raise hit-rate and expectancy, drop the
setups/signals that don't pay, and test new ones deliberately.

---

## Files

```
.claude/agents/                         # the 7 subagent definitions (the team)
Projects/Day Trading Market Analysis/
  README.md                             # this file
  data/
    watchlist.md                        # current candidates being tracked
    trade-journal.md                    # human-readable paper-trade ledger
    trade-log.jsonl                     # machine-readable trade records (for stats)
    strategies.md                       # setups + running win-rate/expectancy
    signals-glossary.md                 # signal types + reliability scores
    lessons-learned.md                  # dated, actionable lessons
    performance-summary.md              # equity curve & aggregate stats
  runs/
    2026-06-11-session-01.md            # full session reports (one per run)
  templates/
    run-template.md
    trade-idea-template.md
    review-template.md
```

---

## Ground rules (enforced by the agents)

1. **US-tradable only** — confirmed Coinbase USD/USDC pair first; else Kraken/Gemini.
2. **Paper only** — every entry is a simulated fill, logged with a timestamp.
3. **No invented numbers** — prices/levels come from a live tool call each session.
4. **Risk-first** — no idea without a stop, target, R:R ≥ 1.3, and a size rule.
5. **Weed out bad signals** — illiquid pumps, exhaustion chases, stale/priced-in
   news, and over-correlated ideas get rejected and *documented* so we learn.

---

## Optional: automate it

The team currently runs **on demand** inside Claude Code. To run it on a schedule
(e.g. a pre-market scan), it can be wired to an **n8n** workflow (an n8n MCP server
is available in this environment) that triggers the session and appends results to
`data/`. Ask: *"automate the day trading scan in n8n"* to set that up.
