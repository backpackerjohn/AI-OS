# Lessons Learned — Day Trading Market Analysis (Paper)

Dated, specific, actionable takeaways. Append-only; newest at bottom.
Format: "YYYY-MM-DD: [what we observed] -> [stop doing X / keep doing Y]."

---

## 2026-06-11 (Session 01 outcomes reviewed in Session 02)

- **2026-06-11: Caught three falling knives.** Session 01 went long majors (BTC,
  SOL, ETH) in Extreme Fear assuming support would hold. A hot CPI + risk-off tape
  blew through every support level. All 3 stopped at -1R (-$150 total, equity
  $10,000 -> $9,850). LESSON: In Extreme Fear WITH deteriorating macro (hot CPI,
  hawkish Fed, ETF outflows), a "support bounce" long WITHOUT a CONFIRMED reclaim
  is a knife-catch. STOP entering naked "price is near support" longs in risk-off.

- **2026-06-11: Extreme Fear is not a buy signal by itself.** It can persist and
  deepen when macro is hostile. KEEP using it only as confluence paired with a
  stabilization/reversal trigger (reclaim, rejection wick + volume, higher-low),
  never as a standalone contrarian long. Demoted extreme-fear contrarian 50->38.

- **2026-06-11: Mean-reversion failed because the tape was trending, not ranging.**
  Fading a trend day is a losing trade. STOP fading without a regime filter; require
  a confirmed range / RSI divergence / higher-low before any mean-reversion entry.

- **2026-06-11: We missed the June 10 CPI on the calendar.** Entered the morning of
  a hot inflation print with no macro awareness. KEEP a macro-calendar check
  (CPI / FOMC / major prints) as a PRE-TRADE gate from now on; size down or stand
  aside into known catalysts, and set a hard de-risk-by date around FOMC.

- **2026-06-11: Round numbers did not act as support in a trending tape.** Treat
  round-number levels as minor confluence only, never a primary thesis. Demoted
  round-number 50->44.

- **2026-06-11 (what worked — KEEP):** The NEAR resting LIMIT @ $2.04 never filled
  and was cancelled per its own rule; price later drifted to ~$2.00-2.03 (Hayes
  dumped his stake June 7). A resting limit + a cancel rule SAVED us from a 4th
  knife-catch. KEEP using resting limits with hard cancel rules instead of chasing.

- **2026-06-11 (corrective applied in Session 02):** Re-spec'd entries to require
  CONFIRMED reclaims (SOL $67 1h-close-on-volume trigger) and resting limits at
  STRUCTURAL levels (BTC 200-week MA $61,900) instead of market knife-catches, each
  with a FOMC de-risk date (June 15). This is the discipline we are now testing.

---

## Next experiment queued (for Session 03)

1. **PRIMARY — Validate BREAKOUT-RECLAIM vs SUPPORT-BOUNCE head-to-head.** The SOL
   $67-reclaim conditional (T-20260611-06) is the disciplined alternative to the
   knife-catch. Compare its outcome against the BTC structural-limit re-spec
   (T-20260611-05). Hypothesis: confirmed-reclaim entries out-perform naked
   support-touch entries in a risk-off regime. Need >=3 closed reclaim trades before
   promoting the setup.

2. **SECONDARY — Macro-gate rule test.** Formalize a pre-trade checklist gate:
   no fresh longs in the 24h before a CPI/FOMC print unless it's a resting limit at
   a structural level with a defined de-risk date. Measure whether trades that
   PASSED the gate out-perform any that would have been skipped.

3. **STRETCH — Regime filter for MEAN-REVERSION.** Keep it suspended until we add a
   trend/range classifier (e.g. ADX or higher-low structure). Only re-arm
   mean-reversion when the classifier flags "range," then paper-test 1 small entry.
