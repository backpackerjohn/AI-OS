# Trade Journal — Day Trading Market Analysis (Paper)

Human-readable log of every paper trade. Append-only. Newest sessions at bottom.
Starting equity: $10,000.00 | Risk per trade: $50 (0.5%).

---

## SESSION 01 — 2026-06-11 (morning)

### CLOSED

#### T-20260611-01 — BTC-USD LONG — CLOSED (STOPPED OUT) — -1R
- Opened: 2026-06-11 09:15 | Venue: Coinbase | Setup: SUPPORT-BOUNCE
- Signals: support-test-hold, extreme-fear contrarian, round-number
- Entry $63,400 | Stop $62,450 | T1 $64,400 | Size 0.0526 BTC (~$3,335) | Risk $50 | R:R 1.05 | Conviction 62
- Thesis: BTC long off support hold into round number; Extreme Fear contrarian bounce.
- Catalyst: technical
- **Exit: $62,450 — STOPPED OUT** (intraday low ~$61,456 blew through the stop). PnL **-$50 / -1.0R**.
- Notes: Knife-catch in Extreme Fear; hot CPI + risk-off tape broke support.

#### T-20260611-02 — SOL-USD LONG — CLOSED (STOPPED OUT) — -1R
- Opened: 2026-06-11 09:20 | Venue: Coinbase | Setup: SUPPORT-BOUNCE
- Signals: support-test-hold, extreme-fear contrarian, round-number
- Entry $86.00 | Stop $84.30 | T1 $88.00 | Size 29.41 SOL (~$2,529) | Risk $50 | R:R 1.18 | Conviction 60
- Thesis: SOL long off support into bounce; Extreme Fear contrarian.
- Catalyst: technical
- **Exit: $84.30 — STOPPED OUT** (SOL subsequently collapsed to ~$65.2). PnL **-$50 / -1.0R**.
- Notes: Support did not hold; SOL led the risk-off selloff.

#### T-20260611-03 — ETH-USD LONG — CLOSED (STOPPED OUT) — -1R
- Opened: 2026-06-11 09:25 | Venue: Coinbase | Setup: MEAN-REVERSION
- Signals: support-test-hold, extreme-fear contrarian
- Entry $1,685 | Stop $1,652 | T1 $1,725 | Size 1.515 ETH (~$2,553) | Risk $50 | R:R 1.21 | Conviction 58
- Thesis: ETH mean-reversion long off oversold; Extreme Fear contrarian.
- Catalyst: technical
- **Exit: $1,652 — STOPPED OUT** (current ~$1,648). PnL **-$50 / -1.0R**.
- Notes: Mean-reversion failed in a trending risk-off tape; no reclaim confirmation.

#### T-20260611-04 — NEAR-USD LONG — CANCELLED (UNFILLED) — $0 / 0R
- Opened: 2026-06-11 09:30 | Venue: Coinbase | Setup: SUPPORT-BOUNCE
- Signals: support-test-hold, extreme-fear contrarian
- Resting LIMIT BUY $2.04 | Stop $1.98 | T1 $2.16 | Size 833 NEAR (~$1,699) | Risk $50 | R:R 2.0 | Conviction 55
- Thesis: NEAR resting limit at support; bounce attempt.
- Catalyst: technical
- **CANCELLED UNFILLED** — limit @ $2.04 never hit (price stayed above ~$2.15 during the order's life). Per its own rule, cancelled. PnL **$0 / 0R**.
- Notes: Arthur Hayes dumped his stake June 7; NEAR re-pulled this session ~$2.00-2.03 (CMC $2.03). Drift lower confirms cancel was correct — would now be a knife-catch.

**Session 01 result: 3 stops (-$150), 1 cancelled. Equity $10,000 -> $9,850.**

---

## SESSION 02 — 2026-06-11 (afternoon)

### OPEN / PENDING

#### T-20260611-05 — BTC-USD LONG — PENDING (resting LIMIT BUY)
- Logged: 2026-06-11 14:40 | Venue: Coinbase | Setup: SUPPORT-BOUNCE (200-week MA hold)
- Signals: 200wma-hold, discount-limit-entry
- LIMIT BUY $61,900 | Stop $60,400 (-2.42%) | T1 $63,000 (50% scale) | T2 $66,000 (runner) | Blended R:R 1.73 | Size 0.0333 BTC (~$2,063) | Risk $50 (0.5%) | Conviction 68
- Thesis: Buy the discount at the 200-week MA support on the Iran headline dip; let confirmation come to us rather than chasing.
- Catalyst: technical (discount on Iran headline)
- Status: **PENDING** (current ~$62,800; limit rests below).
- Management: stop -> break-even after T1; FLAT / de-risked by EOD June 15 (FOMC June 16-17); 48h time-stop.
- **Scheduled review: 2026-06-12 session.**

#### T-20260611-06 — SOL-USD LONG — PENDING (CONDITIONAL)
- Logged: 2026-06-11 14:45 | Venue: Coinbase | Setup: BREAKOUT-RECLAIM
- Signals: confirmed-reclaim, volume-confirmation
- Arms ONLY on a confirmed 1h close >$67 with volume. Entry $67.20 | Stop $64.40 (-4.17%) | T1 $70.00 | T2 $74.00 | Blended R:R 1.71 | Size 17.85 SOL (~$1,200) | Risk $50 | Conviction 64
- Thesis: Require a CONFIRMED reclaim (not a knife-catch); only go long once SOL proves it can hold above $67 on volume.
- Catalyst: technical (confirmed reclaim trigger)
- Status: **PENDING / conditional** (current ~$65.2; trigger >$67 1h close not met).
- Management: Correlation cap — if BTC trade (T-...-05) is live, halve SOL risk to $25. Cancel June 15 if unfilled.
- **Scheduled review: 2026-06-12 session.**

---
