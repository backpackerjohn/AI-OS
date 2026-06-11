# Signals Glossary — reliability scores

_Last updated: 2026-06-11 (Session 02)_

Reliability is a 0-100 score the validator uses to weight signals. We nudge it up
when a signal contributed to a win, down when it contributed to a loss. Append the
change history; never silently overwrite. Baseline for new signals = 50.

---

## support-test-hold
- Reliability: **40** (was 50, **-10**)
- Record contribution: 0W / 3L (BTC, SOL, ETH all stopped)
- Change log:
  - 2026-06-11: -10. "Price is testing support" alone is NOT predictive of a hold.
    In risk-off, support is where the knife lands. Needs confirmation (reclaim,
    rejection wick, volume) before it counts.

## extreme-fear contrarian
- Reliability: **38** (was 50, **-12**)
- Record contribution: 0W / 3L
- Change log:
  - 2026-06-11: -12. Extreme Fear is NOT a buy signal on its own — it can persist
    and deepen when macro is deteriorating (hot CPI, hawkish Fed, ETF outflows).
    Only useful paired with a stabilization/reversal trigger, not as a standalone
    contrarian long. Heaviest demotion this round.

## round-number
- Reliability: **44** (was 50, **-6**)
- Record contribution: 0W / 2L (BTC, SOL)
- Change log:
  - 2026-06-11: -6. Round numbers did not act as support in a trending tape. Weak
    standalone signal; treat as minor confluence only.

## 200wma-hold (NEW)
- Reliability: **55** (baseline 50, +5 starting confidence)
- Record contribution: pending (T-20260611-05)
- Change log:
  - 2026-06-11: Added. A structurally major level; higher prior than generic
    support. Under test via the BTC resting limit.

## discount-limit-entry (NEW)
- Reliability: **52** (baseline 50)
- Change log:
  - 2026-06-11: Added. Resting limit at a discount avoids chasing/market knife-catch.
    Under test.

## confirmed-reclaim (NEW)
- Reliability: **58** (baseline 50, +8 starting confidence)
- Change log:
  - 2026-06-11: Added. Requiring a confirmed close back above a level (on volume) is
    the corrective to this session's failures. Higher prior because it directly
    fixes the knife-catch error. Under test via SOL >$67 conditional.

## volume-confirmation (NEW)
- Reliability: **56** (baseline 50, +6)
- Change log:
  - 2026-06-11: Added. Volume on a reclaim/breakout filters fakeouts. Under test.

---

### Macro lesson (applies to all entry signals)
Technical signals must be discounted when the MACRO regime is hostile. A hot CPI
print + hawkish Fed + ETF outflows = risk-off; in that regime, every "support" /
"contrarian fear" long is a knife-catch until a reclaim is confirmed. The validator
should down-weight bullish-reversal signals when the macro calendar shows a
near-term hot inflation print or FOMC.
