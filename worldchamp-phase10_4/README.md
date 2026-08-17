# WorldChamp Phase 10.4 - Location Timing Audit

P10.4 is a diagnostics-only continuation of P10.3. Trading logic, thresholds, fib geometry, value rules, session rules, order-flow rules, setup rules, plan rules, and manual-execution behavior are unchanged.

The purpose is to explain why the first 20-session sample produced 43 final-valid location bars but zero production-valid approaches or touches.

New WCLOG fields:

- FV_DIR: direction of the first final-valid location in the NY session.
- FV_SRC: anchor source when the first final-valid location appeared.
- FV_FIRST_M: minutes after the 09:30 NY open when the first final-valid location appeared.
- FV_LAST_M: minutes after 09:30 of the last final-valid location bar.
- FV_PRET: 1 if the eventual first-valid zone had already been touched after its current endpoint formed but before it became production-valid; otherwise 0.
- FV_GAP_PCT: minimum candle-to-valid-zone gap while FV was valid, normalized as a percentage of the active impulse range. Zero means a touch.
- FV_GAP_M: minutes after 09:30 when that minimum gap occurred.
- FV_ZDRIFT_PCT: movement of the valid-zone midpoint from the first FV bar to the last FV bar, normalized by the first FV impulse range.
- FV_END_CHG: number of developing endpoint changes after the first FV bar.
- R15_FIRST_M: minute of the first in-session 15M re-arm, if any.
- R1_FIRST_M: minute of the first in-session 1H re-arm, if any.

These fields are diagnostic only and do not alter WorldChamp decisions.
