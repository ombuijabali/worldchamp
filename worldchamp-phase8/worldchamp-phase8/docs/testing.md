# Phase 8 static test

Use the same diagnostic settings that produced the Phase 7 READY LONG map.

## Plan quality
- Confirm `Plan Quality` shows the best structural R from T1/T2/T3.
- On the prior test where only the 4H swing target existed near 0.2-0.4R, expect `POOR` and `FAIL` with the default 1.50R minimum.
- Confirm the READY REF label includes quality/R if enabled.

## Management watch
Because this is static historical testing and execution is manual, the management layer watches the latest READY map rather than a broker position.
- `B?` / `S?`: dominant-side effort stall (2/3 effort-vs-result score).
- `B!` / `S!`: dominant-side effort failure (3/3).
- `ADV`: opposite-side aggressive follow-through.
- Invalidation touch must still override everything with `THESIS FAILED · INV`.

If `Only use order-flow warnings inside NY window` is ON, historical flow warnings should only appear between 09:30 and 11:00 New York. Price-map invalidation and target tracking continue regardless.
