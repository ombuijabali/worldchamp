# WorldChamp Phase 8 - Plan Quality + Management Watch

Phase 8 combines the two post-READY modules requested for WorldChamp:

1. **Plan Quality / Structural R filter**
   - Grades the best available structural target as POOR / MARGINAL / GOOD / STRONG.
   - Default quality bands: <1.0R POOR, 1.0-1.5R MARGINAL, 1.5-2.0R GOOD, >=2.0R STRONG.
   - A configurable minimum structural R (default 1.50R) creates a PASS/FAIL informational gate.
   - No artificial target is created to improve R.

2. **Management Watch**
   - Begins only after a SETUP READY plan map exists.
   - It is anchored to READY REF and is **not broker-position tracking** because execution remains manual.
   - Warns when the dominant side shows aggression without price result (effort failure).
   - Warns when the opposite side shows aggressive directional follow-through.
   - Keeps invalidation/target-touch status from Phase 7.

No strategy orders are sent.
