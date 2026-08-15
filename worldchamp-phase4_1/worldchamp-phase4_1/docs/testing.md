# Phase 4.1 - 7 Day Validation

Use a 5-minute chart with usable volume data. Hide any manual Fibonacci drawing while judging WorldChamp's own location zone.

## Test A - Auto context block

1. Set `Location direction = Auto`.
2. On the NAS100 example where the environment reads `TRANSITION / WAIT`, verify:
   - `Bias / Impulse = NONE`
   - `Location = CONTEXT BLOCKED`
   - no WorldChamp location box is drawn.

## Test B - Force Long

1. Set `Location direction = Force Long (Test)`.
2. Confirm the dashboard shows `LONG · TEST · DISCOUNT ✓` when the Fib midpoint is in impulse discount.
3. Confirm the selected 1H -> 15M anchor matches the intended completed upswing.
4. Confirm the chart draws only:
   - one subtle impulse anchor,
   - one 0.705-0.886 box,
   - `LOC 0.705`, `LOC 0.788`, and `LOC 0.886 · INVALID`.
5. Verify `Zone .705→.886` and `.788` numerically against a manual Fib tool, then hide the manual tool.
6. Verify `Value Check` independently reports one of:
   - `BELOW VAL ✓`
   - `OVERLAPS VALUE ✕`
   - `WRONG SIDE · ABOVE VAH ✕`
7. Verify `Swing Check` correctly reports the 15M internal swing requirement.
8. If price has already closed below 0.886, verify `Location = INVALIDATED < .886`.

## Test C - Force Short

Repeat Test B with `Force Short (Test)` and verify:

- `SHORT · TEST · PREMIUM ✓`
- the short Fib geometry is mirrored correctly,
- valid value-side placement is `ABOVE VAH ✓`,
- a stale short anchor becomes `INVALIDATED > .886` after price closes above 0.886.

## Test D - visual cleanliness

Confirm:

- the whole dashboard fits on screen,
- GEX/value/location labels are distinguishable,
- location labels sit farther right than GEX labels,
- no old Fib boxes accumulate,
- only the active impulse/location map remains visible.

## Pass criteria

Phase 4.1 passes when:

- Auto blocks transition/mixed environments.
- Impulse discount/premium and value-side validity are clearly separated.
- The selected 1H/15M anchor is correct.
- Fib values match manual calculation.
- Full-zone outside-value logic is correct.
- 0.886 invalidation is explicit and persistent.
- Long and short forced tests behave symmetrically.
- The dashboard and drawings remain clean.
