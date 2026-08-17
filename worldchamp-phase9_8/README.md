# WorldChamp Phase 9.8 - 15M Fresh Re-arm under 1H Context

P9.8 builds on the validated P9.7 retirement lifecycle.

## What changed

- The confirmed 1H opposite swing remains the primary location origin.
- If that impulse breaches `.886`, the 1H origin remains retired and cannot resurrect on a bounce.
- While the same directional context is active, a **new confirmed 15M opposite-side pivot whose pivot time is after the latest retirement** may temporarily re-arm the location engine.
- The temporary 15M origin develops its endpoint from actual 5-minute highs/lows.
- A genuinely newer confirmed 1H origin always overrides the temporary 15M re-arm.
- If a temporary 15M re-arm itself breaches `.886`, that 15M seed is discarded and the engine waits for another newer 15M pivot or a new 1H origin.

## Rules intentionally unchanged

- `.705 / .788 / .886` calculations
- `.886` invalidation
- value-side requirement
- range-side requirement
- higher-timeframe environment logic
- participation/order-flow/aggression/absorption/dominance logic
- retest and second-failure logic
- SETUP READY logic
- plan quality and management watch
- manual execution only

## Validation fields

The existing `ANCH` source will show either `1H DEV`, `1H→15M DEV`, or `15M REARM`.

The audit line now includes:

- `RE` - total re-arm events
- `RE1H` - re-arms caused by a newer confirmed 1H origin
- `RE15` - temporary re-arms caused by a fresh confirmed 15M pivot

