# WorldChamp Phase 10.5 — Re-arm Timing Audit

P10.5 is a **diagnostic/logger-only** build derived from P10.4.

**Trading logic is unchanged. Manual execution remains unchanged.**

The purpose is to distinguish three different reasons why a valid `.705–.886` location may never be touched:

1. the 15M re-arm becomes available only after a meaningful confirmation delay;
2. price already visited the eventual zone between the structural pivot origin and the moment the location became valid;
3. the NY pullback is genuinely too shallow even after the location is valid.

New `WCLOG` fields:

- `FV_ORIGIN_M` — actual selected anchor-origin minute relative to the 09:30 NY start. Negative values mean the origin formed before 09:30.
- `FV_ORIGIN_AGE_M` — minutes from the actual selected origin to the first production-valid location bar.
- `FV_PRE_ORIGIN_TOUCH` — `1` if the first-valid `.705–.886` zone was touched after the selected origin formed but before the first valid-location bar.
- `FV_MAX_RT` — deepest wick retracement, as a percent of the active impulse, while the location was production-valid.
- `FV_MAX_RT_M` — NY minute offset when `FV_MAX_RT` occurred.

Existing P10.4 fields remain, including `FV_FIRST_M`, `R15_FIRST_M`, `FV_GAP_PCT`, zone drift, endpoint changes, and the complete production funnel counters.
