# Performance Summary — Day Trading Market Analysis (Paper)

_Last updated: 2026-06-11 (Session 02 review)_

## Equity
- Starting equity: **$10,000.00**
- Realized PnL to date: **-$150.00**
- Current equity: **$9,850.00**
- Equity curve: $10,000.00 -> $9,850.00 (Session 01 closed out)

## Aggregate stats (CLOSED trades only; cancelled excluded)
- Trades closed: **3**
- Wins: **0** | Losses: **3** | Scratches: **0**
- Win-rate: **0.0%** (0/3)
- Avg win: n/a (no wins yet)
- Avg loss: **-$50.00 (-1.0R)**
- Expectancy (avg R): **-1.00R** per trade
- Best trade: none positive (best = -1.0R)
- Worst trade: -1.0R (three-way tie: BTC, SOL, ETH)
- Cancelled/unfilled (no PnL): 1 (T-20260611-04 NEAR)

## Per-setup breakdown
| Setup | Closed | W | L | Win-rate | Avg R | Status |
|---|---|---|---|---|---|---|
| SUPPORT-BOUNCE | 2 | 0 | 2 | 0% | -1.00R | FLAGGED — failed in Extreme Fear / risk-off |
| MEAN-REVERSION | 1 | 0 | 1 | 0% | -1.00R | FLAGGED — failed without reclaim confirmation |
| BREAKOUT-RECLAIM | 0 | 0 | 0 | n/a | n/a | NEW — under test (T-...-06) |

## Open / pending exposure
| ID | Pair | Dir | Status | Risk | Notes |
|---|---|---|---|---|---|
| T-20260611-05 | BTC-USD | LONG | PENDING (limit $61,900) | $50 | de-risk by June 15 (FOMC) |
| T-20260611-06 | SOL-USD | LONG | PENDING (conditional >$67) | $50 | halve to $25 if BTC live |

- Open risk if both fill: up to $100 (capped to $75 via SOL correlation rule).

## Notes
- Three straight stop-outs from going long majors in Extreme Fear assuming support would hold. Hot CPI + risk-off tape broke every support level.
- Session 02 corrected: resting limits + confirmed-reclaim triggers instead of market knife-catches; macro calendar now checked before entry.
