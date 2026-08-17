# WorldChamp P9.7 - Anchor Retirement + Fresh Re-arm Validation

P9.7 changes only the location-anchor lifecycle identified by the P9.6 audit. Execution remains manual.

## What changed

- Keep the P9.6 developing endpoint.
- When the active developing impulse breaches `.886`, retire its confirmed 1H origin.
- A retired 1H origin cannot reactivate because price later bounces back above/below `.886`.
- Long and short origins are retired independently.
- Re-arm only when a genuinely newer confirmed 1H opposite swing origin appears.
- `.705/.788/.886`, value-side, 15M swing, participation, order-flow, setup, plan, and management thresholds are unchanged.

## Validation settings

1. Use NAS100USD 5-minute chart for the same Aug 10-14 static audit.
2. Set Operating mode = Validation.
3. Keep Location direction = Auto.
4. Leave all TEST overrides irrelevant/off (Validation hard-disables them).
5. Leave GEX OFF unless you have session-correct values.

## New expected audit fields

The session label now includes:

- `BLK RETx` - bars blocked because the current confirmed 1H origin is retired.
- `RETx` - retirement events during the NY validation window.
- `REx` - fresh-origin re-arm events during the NY validation window.

Existing `PRE-BR`, `SEL-BR`, `NY-INV`, `GEO`, `RAW`, and `FINAL` counters remain.

## Required checks

### A. Previously stale origin

On a session that previously showed `SEL-BR1` / persistent `INV`:

- Expect one invalidation/retirement event at most for that origin.
- Following bars should show `BLK RET` rather than repeatedly carrying the invalid anchor.
- The dashboard Location state should read `WAIT NEW 1H IMPULSE · RETIRED` while that origin remains the latest confirmed origin.

### B. No resurrection

After retirement, if price returns back through the old `.886` level:

- The old anchor must remain retired.
- Location must not become valid from the retired origin.
- Old fib/zone drawings must not be treated as an actionable active location.

### C. Fresh re-arm

When a newer confirmed 1H opposite swing origin appears:

- `RE` should increment if the confirmation occurs inside the audited NY window.
- The retired state should clear for that side.
- The developing endpoint should restart from the newer 1H origin.
- Normal strict geometry/value/swing checks should resume.

## Pass criteria

P9.7 passes if stale origins no longer persist indefinitely, no retired origin resurrects, and a new confirmed 1H origin can re-arm location without changing any other production threshold.
