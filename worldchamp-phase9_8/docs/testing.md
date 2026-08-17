# P9.8 Validation Test

Use `Operating Mode = Validation` on the 5-minute NAS100 chart. Keep all Production thresholds unchanged.

## Primary test

Revisit the same Aug 10-14 NY windows used for P9.7.

### Expected retirement behavior

A previously retired 1H origin must remain retired after price bounces. It must not silently reactivate.

Before a fresh pivot appears, the dashboard should show approximately:

`WAIT 15M / NEW 1H · RETIRED`

### Expected 15M re-arm behavior

A 15M re-arm is allowed only when all of these are true:

1. the matching 1H origin is already retired;
2. the production directional context is active;
3. TradingView confirms a new opposite-side 15M pivot;
4. the actual pivot time is after the latest retirement event.

When this happens, the Validation label should show:

- `ANCH ... 15M REARM`
- `RE15` incremented
- `RE` incremented

The new 15M origin should then develop its endpoint from 5M price and run through the unchanged geometry/value/location tests.

### Expected 1H override

If a genuinely newer confirmed 1H origin appears, it must supersede any temporary 15M re-arm. The audit should increment `RE1H`, and the source should return to `1H DEV` or `1H→15M DEV`.

### Temporary re-arm invalidation

If a `15M REARM` impulse breaches `.886`:

- the temporary seed must be discarded;
- it must not be reused after a bounce;
- the old 1H origin must remain retired;
- the engine waits for another newer confirmed 15M pivot or a new 1H origin.

## What to send back

For each completed NY window, send a screenshot with the full orange Validation label visible. The most important fields are:

`BLK`, `ANCH`, `RET`, `RE`, `RE1H`, `RE15`, `GEO`, `RAW`, and `FINAL V`.

The key success condition is not simply more signals. We want to see that a legitimate fresh 15M re-arm can reopen the location funnel without weakening `.886` or value rules.
