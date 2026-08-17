# WorldChamp P10.5 — Re-arm Timing Audit

## Goal

Re-run the same accessible ~20-session NAS100USD/OANDA 5-minute Validation sample. Do not change thresholds.

P10.5 does **not** change the trading engine. It only adds diagnostics to determine whether the zero-touch result comes from 15M confirmation timing or from genuinely shallow retracements.

## TradingView

- Symbol: NAS100USD (OANDA), same source used in prior validation
- Timeframe: 5 minutes
- Mode: Validation
- Keep the current validation window/settings
- Keep `.705/.788/.886`, value, 15M swing, participation, aggression, absorption, dominance and setup settings unchanged

## Export

Open **Pine Logs**, filter/search `WCLOG`, export/copy the same accessible session set, and send the CSV/logs back.

## Fields to inspect

For sessions where `FV > 0`:

- `FV_FIRST_M`
- `R15_FIRST_M`
- `FV_ORIGIN_M`
- `FV_ORIGIN_AGE_M`
- `FV_PRE_ORIGIN_TOUCH`
- `FV_MAX_RT`
- `FV_MAX_RT_M`
- `FV_GAP_PCT`
- `FV_ZDRIFT_PCT`
- `FV_END_CHG`
- `LOC_A`
- `LOC_Z`

## Interpretation

- `FV_PRE_ORIGIN_TOUCH=1`: the eventual production zone was visited after the structural origin existed but before confirmation made it usable. This supports a confirmation-lag diagnosis.
- Large `FV_ORIGIN_AGE_M`: the confirmed-pivot path is materially delaying location availability.
- `FV_PRE_ORIGIN_TOUCH=0` with low `FV_MAX_RT`: price genuinely did not retrace deeply enough.
- `FV_MAX_RT` around 60–70% but below 70.5%: a near miss to the current `.705` boundary. Do not loosen the boundary from this diagnostic alone.
- High zone drift / many endpoint changes: developing endpoint movement may be contributing.

Do not tune any production threshold until this audit is reviewed.
