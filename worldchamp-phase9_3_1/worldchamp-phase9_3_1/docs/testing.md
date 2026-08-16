# WorldChamp P9.3.1 - 5M Guard Fix

## Fix
P9.3 could falsely raise the 5-minute runtime guard on bar 0 even while TradingView was on a 5-minute chart.

The guard now uses TradingView's direct chart-timeframe built-ins:

- `timeframe.isminutes`
- `timeframe.multiplier == 5`

The profile lower-timeframe check now uses `timeframe.in_seconds()` for the chart and `timeframe.in_seconds(profileLtf)` for the configured lower timeframe.

## Trading logic
No environment, location, participation, aggression, absorption, dominance, retest, setup, plan-quality, target, or management threshold was changed.

## Test
1. Put the chart on 5m.
2. Load P9.3.1 with `Require 5-minute chart = ON`.
3. It should load normally.
4. Switch to 15m temporarily; the guard should intentionally raise the 5-minute error.
5. Return to 5m and use Validation mode for the full-funnel audit.
