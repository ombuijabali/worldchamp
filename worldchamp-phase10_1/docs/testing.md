# P10.1 Validation Logger Test

1. Load WorldChamp P10.1 on NAS100USD 5-minute chart.
2. Set Operating Mode = Validation.
3. Confirm there is no RE10140 plot-limit error.
4. Keep validation window around 45 calendar days for roughly 30 sessions.
5. Export chart data to CSV after history is loaded.

## Packed fields

P10.1 uses base-1000 packing to stay below TradingView's plot-count limit.
For any packed value `X`:
- first value = floor(X / 1000)
- second value = X % 1000

Fields:
- `VAL_CTX_PACK` = CTX_PASS * 1000 + CTX_BLOCK
- `VAL_REARM_PACK` = REARM_15M * 1000 + REARM_1H
- `VAL_AGG_PACK` = AGG_BUY * 1000 + AGG_SELL
- `VAL_ABS_PACK` = ABS_SELLER * 1000 + ABS_BUYER
- `VAL_DOM_PACK` = DOM_BUYER * 1000 + DOM_SELLER
- `VAL_SETUP_PACK` = SETUP_LONG * 1000 + SETUP_SHORT

Unpacked export fields remain:
- VAL_RETIRE
- VAL_ANCHOR_SOURCE
- VAL_GEO_ALL
- VAL_LOC_VALID
- VAL_ZONE_TOUCH
- VAL_PART_PASS
- VAL_OF_READY
- VAL_ABS_POTENTIAL

Only completed NY-session rows have values; other bars should be blank/na.
