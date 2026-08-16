# WorldChamp P9.3 - Full-Funnel Validation Test

P9.3 does not change any production trading threshold or gate. It only expands the historical Validation-mode session summary so each completed 09:30-11:00 New York session shows where the production funnel stopped.

## Mode safety

- Production: production rules, no TEST overrides, minimal live visuals.
- Validation: the same production rules, no TEST overrides, historical audit visuals and the P9.3 full-funnel summary.
- Debug: TEST controls may affect logic.

## P9.3 summary fields

`WC VAL · 18B` is the number of completed 5-minute bars in the NY window.

`CTX P / B`
- P: bars where the production environment resolved to a directional long or short context.
- B: bars where environment/context was non-directional and location was therefore blocked.

`LOC V / Z / A`
- V: bars where the complete production location geometry was valid and not invalidated.
- Z: valid-location bars whose candle touched the 0.705-0.886 zone.
- A: valid-location bars approaching the zone.

`BLK`
- LEG: missing/invalid production impulse leg or anchor.
- INV: selected location impulse had already crossed its .886 invalidation.
- MAP: no usable value map.
- RNG: wrong side of the selected impulse range.
- VAL: location zone was not outside auction value on the required side.
- SW: required 15-minute internal swing was missing.

The BLK reasons are exclusive and are counted only after CTX passes.

`PART P`
- Number of NY bars that passed the production participation filter.
- H/N/L remain the existing participation classifications.

`OF ready/total`
- Bars with usable lower-timeframe proxy data.

The existing AGG, ABS, DOM and SET counters are unchanged.

## Expected test

1. Use NAS100USD on 5 minutes.
2. Set Operating mode = Validation.
3. Leave all TEST settings in any saved state; they must not affect Validation.
4. Inspect completed 09:30-11:00 NY sessions.
5. Confirm `CTX P + CTX B = 18` on a complete session.
6. Confirm the new multiline `WC VAL` label contains CTX, LOC, BLK, PART, OF, AGG, ABS, DOM and SET.
7. Send screenshots of the five available weekday sessions. We will use the new counters to decide whether no-setup results come from context/location gating or from later order-flow confirmation.
