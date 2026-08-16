# WorldChamp Phase 9.1 - Production + GEX Safety

Phase 9.1 keeps the validated Phase 9 trading logic unchanged and hardens the manual GEX module.

## GEX safety changes

- Default remains **GEX OFF**, **Neutral**, and all levels at **0**.
- Input labels now make `0 = unset` explicit.
- When GEX is enabled, Gamma Flip, Call Wall, and Put Wall must all be non-zero.
- Call Wall must be above Put Wall.
- Positive gamma below the entered Gamma Flip is flagged as a regime/flip conflict.
- Negative gamma above the entered Gamma Flip is flagged as a regime/flip conflict.
- Neutral regime is allowed on either side of the flip.
- Incomplete/conflicting GEX is not drawn and is excluded from target selection.
- Dashboard reports `NOT CONFIGURED`, `INPUT INCOMPLETE`, `WALL ORDER INVALID`, or `REGIME / FLIP CONFLICT` instead of silently using bad levels.

Manual execution remains unchanged.
