# Phase 1 - Environment Engine Test Plan

## Purpose

Validate the higher-timeframe environment engine before adding value profile, GEX, location, or order-flow logic.

Phase 1 intentionally uses confirmed swing structure as a proxy for auction/value direction. Phase 2 will add actual value-area and POC migration.

## Operating chart

- Use a 5-minute chart.
- Keep the development window at 7 calendar days.
- Historical testing is valid while markets are closed.

## Default structure rules

For each higher timeframe:

- UP: latest confirmed swing high > previous confirmed swing high AND latest confirmed swing low > previous confirmed swing low.
- DOWN: latest confirmed swing high < previous confirmed swing high AND latest confirmed swing low < previous confirmed swing low.
- BALANCED: the two swing comparisons disagree.
- WARMING: insufficient confirmed pivots exist.

## HTF environment rules

- 4H UP + 1H UP -> ALIGNED UP.
- 4H DOWN + 1H DOWN -> ALIGNED DOWN.
- 4H UP + 1H DOWN -> 4H UP / 1H PULLBACK.
- 4H DOWN + 1H UP -> 4H DOWN / 1H PULLBACK.
- Other combinations -> BALANCED or MIXED.

## Seven-day visual validation

For each visible structural transition:

1. Open the 4H chart and identify the most recent confirmed swing high and swing low.
2. Compare those levels with the dashboard's 4H Swing H / Swing L.
3. Repeat on the 1H chart.
4. Confirm that UP requires both HH and HL.
5. Confirm that DOWN requires both LH and LL.
6. Confirm mixed progression reports BALANCED rather than forcing a trend.
7. Confirm the four structural lines are the latest levels only; old lines must not accumulate.
8. Enable Debug mode and verify the confirmed HTF close plots remain stable between HTF closes.

## Pass criteria

Phase 1 passes when:

- The displayed swing levels match manually identified confirmed pivots.
- Structure classifications change only after confirmed HTF information becomes available.
- The environment state correctly describes 4H/1H agreement or pullback/mixed conditions.
- No buy/sell signal is produced.
- The chart stays visually clean.

## Important limitation

Do not interpret Phase 1's structure state as the final 'value up/value down' model. The transcript's environment framework also uses value creation/migration. That component belongs to Phase 2.
