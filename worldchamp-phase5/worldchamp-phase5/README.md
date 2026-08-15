# WorldChamp Phase 5 - Participation Filter

Phase 5 extends the locked Phase 4.1 location engine with a session-aware participation gate. It does not generate entries or execute orders.

## Participation modes

- `Auto`: uses the transcript-style absolute 5-minute contract threshold only when the chart is MNQ futures; other symbols use relative volume.
- `Absolute`: compares current 5-minute volume to a configurable threshold (default 20,000).
- `Relative`: compares current 5-minute volume with a rolling baseline built only from prior confirmed 5-minute bars inside the active New York window.

## States

- `OUTSIDE NY`
- `NO VOLUME`
- `WARMING`
- `LOW`
- `NORMAL`
- `HIGH`

The future order-flow module is armed only when the location is active, the chart is inside the New York window, and participation passes. Execution remains manual.
