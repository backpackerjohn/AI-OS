# Strategies / Setups — running win-rate & expectancy

_Last updated: 2026-06-11 (Session 02)_

Each setup tracks closed-trade record, win-rate, expectancy (avg R), and a status
(PROMOTE / TESTING / FLAGGED / DEMOTED). Append history; never delete prior records.

---

## SUPPORT-BOUNCE
- Record: **0W / 2L** (T-20260611-01 BTC, T-20260611-02 SOL)
- Win-rate: **0% (0/2)**
- Expectancy: **-1.00R**
- Status: **FLAGGED** ⚠
- Notes: Both losers were market/early entries that assumed support would hold in
  Extreme Fear. Support broke on a hot-CPI risk-off tape. Do NOT trade as a naked
  "price is near support" long. Re-spec required: only valid with (a) a CONFIRMED
  reclaim or rejection wick + volume, OR (b) a resting LIMIT at a structurally
  major level (e.g. 200-week MA) with a hard macro-event de-risk rule. The Session
  02 BTC limit (T-...-05) is the first re-spec'd test of this setup.

## MEAN-REVERSION
- Record: **0W / 1L** (T-20260611-03 ETH)
- Win-rate: **0% (0/1)**
- Expectancy: **-1.00R**
- Status: **FLAGGED** ⚠
- Notes: Failed because the tape was trending (risk-off), not ranging. Mean-reversion
  needs a confirmed range / oversold + stabilization, not a falling knife. Suspend
  until we have a regime filter (e.g. don't fade a trend day; require RSI divergence
  or a higher-low before entry).

## BREAKOUT-RECLAIM (NEW)
- Record: **0W / 0L** (T-20260611-06 SOL pending/conditional)
- Win-rate: n/a
- Expectancy: n/a
- Status: **TESTING** 🧪
- Notes: Introduced Session 02 as the disciplined alternative to knife-catching.
  Arms only on a confirmed 1h close above the level with volume. First live test is
  the SOL >$67 conditional. This is the setup we WANT to validate.

---

### Setup leaderboard (by expectancy)
1. BREAKOUT-RECLAIM — n/a (testing)
2. SUPPORT-BOUNCE — -1.00R (flagged; re-spec under test)
3. MEAN-REVERSION — -1.00R (flagged; suspended pending regime filter)
