# Signals Glossary — definitions & reliability scores

Each signal has a reliability score (0-100, starts neutral at 50). The Journalist
nudges it up when trades using it win, down when they lose. The Validator uses
these scores to weight its confidence calculation, so the team's trust in each
signal is **earned from results over time.**

| Signal | Reliability | Sample | Definition / how we read it |
|---|---|---|---|
| Support test + hold | 50 🆕 | 0 | Price reaches a prior support level and stops falling (lower wicks, slowing momentum). Long trigger on the reclaim/bounce. |
| Oversold RSI (<30) | 50 🆕 | 0 | Intraday RSI in oversold territory — bounce fuel, but not a trigger alone. |
| Volume confirmation | 50 🆕 | 0 | Move accompanied by rising volume = conviction; fading volume = suspect. |
| Extreme Fear sentiment (F&G ≤ 10) | 50 🆕 | 0 | Contrarian bullish bias intraday; crowd capitulation often mean-reverts. |
| Real positive catalyst (STRONG) | 50 🆕 | 0 | Verifiable news from a credible primary source driving the move. |
| Resistance rejection | 50 🆕 | 0 | Price stalls/reverses at prior resistance — fade or avoid longs. |
| Round-number level | 50 🆕 | 0 | Psychological levels ($63k BTC, $85 SOL) act as S/R magnets. |
| ETF flow direction | 50 🆕 | 0 | Net spot ETF inflows/outflows as a multi-session demand proxy. |

## Anti-signals (red flags the Validator weeds out)
| Anti-signal | Action | Why |
|---|---|---|
| Big % move on tiny volume | REJECT | Illiquid pump — spread/slippage kill the edge; manipulation risk. |
| Parabolic + overbought + fading volume | REJECT long / WATCH fade | Exhaustion — chasing tops. |
| "News" = the price move itself | Discount | Circular; no real catalyst. |
| Stale catalyst recycled as fresh | Discount heavily | Already priced in. |
| 3+ highly correlated ideas | Keep best, REJECT rest | Hidden concentration risk. |
| No logical invalidation / R:R < 1.3 | REJECT | Can't define risk = no trade. |
