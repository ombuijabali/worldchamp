# Phase 9.1 GEX Safety Test

Use a 5-minute chart.

## Test 1 - Safe default

Set:
- Enable manual GEX context = OFF

Expected dashboard:
- `GEX: NOT CONFIGURED`
- no GEX lines
- no GEX wall target can be added to a plan

## Test 2 - Incomplete input

Set:
- Enable manual GEX context = ON
- Gamma Flip = 30500
- Call Wall = 29500
- Put Wall = 0

Expected:
- `GEX: INPUT INCOMPLETE`
- no GEX drawings
- GEX values ignored by target map

## Test 3 - Wall order

Enter all three levels but make Call Wall <= Put Wall.

Expected:
- `GEX: WALL ORDER INVALID`
- no GEX drawings

## Test 4 - Regime / flip conflict

If current price is below Gamma Flip and Gamma regime is Positive:
- expect `GEX: REGIME / FLIP CONFLICT`

If current price is above Gamma Flip and Gamma regime is Negative:
- expect the same conflict warning.

Neutral is permitted on either side of the flip because the user may be supplying a provider-specific neutral regime.

## Test 5 - Valid daily data

With a complete, internally consistent daily snapshot:
- dashboard shows `POSITIVE/NEGATIVE/NEUTRAL · volatility · ABOVE/BELOW FLIP`
- Gamma Flip / Call Wall / Put Wall are drawn
- the directional wall may be considered by the structural target map

## Production dashboard wording fix

When a valid value map exists but Auto location has no directional context/anchor yet:
- `Zone / Value` should show `n/a | WAIT · LOCATION`
- it must **not** say `NO VALUE MAP`

`NO VALUE MAP` is reserved for the actual case where VAH/VAL are unavailable.
