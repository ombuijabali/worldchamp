# Phase 4 - 7 Day Validation

Use a 5-minute chart with usable volume data. Keep the existing 7-day development window enabled.

## Test A - production Auto mode

1. Set `Location direction = Auto`.
2. On the NAS100 example where the environment reads `TRANSITION / WAIT`, verify:
   - `Location Bias = NONE`
   - `Location = CONTEXT BLOCKED`
   - no Fib zone is drawn.

This confirms Phase 4 cannot create a setup just because a Fib exists.

## Test B - forced long visualization

1. Set `Location direction = Force Long (Test)`.
2. Confirm the dashboard displays `LONG · TEST · DISCOUNT`.
3. Confirm an impulse anchor is selected from a completed 1H upswing.
4. Confirm the chart draws only:
   - a subtle impulse anchor,
   - one shaded 0.705-0.886 box,
   - 0.705 and 0.886 boundaries,
   - dotted 0.788 midpoint.
5. Verify the numerical Fib levels against TradingView's Fib tool using the dashboard anchor prices.
6. Verify `Location Checks` reports whether the zone is outside VA and whether 15M internal structure exists.

## Test C - forced short visualization

Repeat Test B with `Force Short (Test)` and verify the zone is in premium and the short retracement is mirrored correctly.

## Test D - outside-value rejection

Find or force a case where the long zone overlaps/enters the value area or the short zone overlaps/enters value. Confirm:

- `Location Checks` reports `IN VA`.
- `Location = INSIDE VALUE · REJECT`.
- the box uses the rejected/neutral visual treatment rather than the valid location treatment.

## Test E - invalidation

For a valid long anchor, move through historical bars after a close below 0.886. The state should become `INVALIDATED < .886` and remain invalid for that anchor. The short side mirrors this above 0.886.

## Pass criteria

Phase 4 passes when:

- Auto mode blocks transition/mixed environments.
- The selected 1H impulse is correct.
- 15M refinement does not choose a pivot outside the 1H impulse.
- Fib values match manual calculation.
- Outside-value logic is correct.
- Location states transition correctly.
- The chart remains visually clean.
