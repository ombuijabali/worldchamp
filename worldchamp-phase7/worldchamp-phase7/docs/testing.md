# Phase 7 static test

Use the same historical NY session and TEST settings that produced a `READY L` event in Phase 6E.

## Expected on SETUP READY

1. `READY REF` line appears at the close of the READY candle.
2. `INV · FAILED SIDE` appears at the original failed-participant extreme.
3. For a long map, invalidation should be below the READY reference. For a short map, it should be above.
4. Only targets in the setup direction are accepted.
5. Targets are sorted nearest to farthest as T1, T2, T3.
6. Duplicate structural levels are collapsed.
7. If `Show target R` is enabled, each target label displays R based on READY reference to invalidation risk.
8. The dashboard `PLAN MAP` section shows direction, reference/invalidation, targets, and current map status.

## Target sources

By default the map considers value, prior value, 1H/4H structure, and a directional GEX wall when supplied. It does not invent a target if no valid structural level exists.

## Static validation

After the READY candle, scroll right and confirm:

- a target touched by price gains a check mark in the dashboard;
- invalidation touched changes Plan Status to `INV TOUCHED`;
- final available target touched completes the map;
- no orders are generated.

## Important

The READY reference is not your actual entry. It is only the deterministic reference used to visualize the map and calculate indicative R values. Manual execution remains the user's responsibility.
