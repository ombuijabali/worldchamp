# Phase 9 - Seven-Day Integrated Validation

Use a 5-minute chart with a volume-capable symbol. MNQ/NQ is preferred for the final order-flow/participation validation; NAS100 CFD is acceptable for validating the free-plan proxy behavior.

## Test settings

1. Set Operating mode = Validation.
2. Keep Limit drawings to recent window = ON.
3. Keep Calendar days = 7.
4. Set Location direction = Auto.
5. Turn OFF every TEST dominance/setup override.
6. Use real/manual GEX values only if you have them. Otherwise leave GEX OFF.
7. Keep execution manual.

## What Validation mode should show

- Historical participation markers.
- Aggression markers.
- Absorption markers.
- Dominance shifts.
- Retest/second-failure markers.
- SETUP READY events.
- One consolidated session label at the end of each NY active window.

It should NOT show the raw delta markers or the old stack of separate module summary labels unless Operating mode = Debug.

## Session review checklist

For each completed NY 09:30-11:00 window, verify in order:

1. HTF environment is sensible.
2. Value migration and quality are sensible.
3. Location uses Auto and never uses forced-test direction.
4. Valid location is on the correct side of value.
5. Participation classification is sensible for the feed.
6. Aggression appears only on materially one-sided proxy-delta bars.
7. Absorption is conservative and requires aggression first.
8. Dominance follows a qualified failure and opposite-side response.
9. Retest occurs after dominance.
10. Second failure is on the correct side of the original failed-participant extreme.
11. SETUP READY appears only after the full sequence.
12. Invalidation is beyond the failed side.
13. Structural targets are ordered in the setup direction and no fake targets are created.
14. Plan quality reflects the best available structural R.
15. Management warnings do not resurrect a thesis after invalidation.

## Production-mode check

After the seven-day validation looks correct:

1. Set Operating mode = Production.
2. Confirm the dashboard says P9 - PRODUCTION.
3. Confirm forced location and all diagnostic TEST settings have no effect.
4. Confirm historical H/N/L, aggression, absorption, dominance, and retest markers disappear.
5. Confirm the latest plan map remains clean.
6. Confirm execution remains manual.
