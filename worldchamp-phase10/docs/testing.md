# P10 - 30-session validation without screenshots

## TradingView setup

1. Load **WorldChamp P10** on NAS100USD 5M.
2. Set **Operating mode = Validation**.
3. Keep **Enable session export series = ON**.
4. Set **Calendar days = 45**. If fewer than 30 market sessions are loaded because of holidays/data gaps, increase it to 60.
5. Scroll left far enough that TradingView has loaded the full period you want to test.

## Export

Use TradingView's **Download chart data...** command and save the CSV.

Upload that one CSV to ChatGPT. No daily screenshots are needed.

## How to isolate WorldChamp session rows

The `VAL_*` columns contain values only once per completed NY 09:30-11:00 session. Filter to rows where `VAL_CTX_PASS` is not blank.

## Logger fields

- `VAL_CTX_PASS`, `VAL_CTX_BLOCK`
- `VAL_RETIRE`
- `VAL_REARM_15M`, `VAL_REARM_1H`
- `VAL_ANCHOR_SOURCE`: 15 = 15M REARM, 1 = 1H-derived, 0 = none
- `VAL_GEO_ALL`
- `VAL_LOC_VALID`
- `VAL_ZONE_TOUCH`
- `VAL_PART_PASS`
- `VAL_OF_READY`
- `VAL_AGG_BUY`, `VAL_AGG_SELL`
- `VAL_ABS_SELLER`, `VAL_ABS_BUYER`, `VAL_ABS_POTENTIAL`
- `VAL_DOM_BUYER`, `VAL_DOM_SELLER`
- `VAL_SETUP_LONG`, `VAL_SETUP_SHORT`

The CSV timestamp gives the session date. The record appears on the first 5-minute bar after the NY active window closes.

## Funnel we will analyze

CTX -> RETIRE/REARM -> GEO -> LOCATION -> TOUCH -> PARTICIPATION -> ORDER FLOW -> ABSORPTION -> DOMINANCE -> SETUP READY

The goal is to measure conversion rates at each stage before changing any thresholds.
