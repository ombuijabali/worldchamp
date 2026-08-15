# WorldChamp Phase 4.1 - Location Refinement

Phase 4.1 keeps the validated Phase 4 location engine and improves clarity, invalidation handling, and chart cleanliness.

## Included modules

- 4H / 1H confirmed structure
- Session VAH / POC / VAL
- Value migration + overlap quality
- Manual GEX volatility context
- 1H -> 15M location engine

## Phase 4.1 refinements

1. **Impulse discount/premium is separate from auction value.**
   - A long retracement can be in impulse discount while still being above VAH or overlapping value.
   - A short retracement can be in impulse premium while still being below VAL or overlapping value.
2. **Directional value validation uses the full zone.**
   - Long: the complete 0.705-0.886 zone must sit below VAL.
   - Short: the complete 0.705-0.886 zone must sit above VAH.
3. **Value checks are explicit.**
   - `BELOW VAL ✓`
   - `ABOVE VAH ✓`
   - `OVERLAPS VALUE ✕`
   - `WRONG SIDE · ABOVE VAH ✕`
   - `WRONG SIDE · BELOW VAL ✕`
4. **0.886 invalidation is explicit and persistent for the selected anchor**, even when test mode exposes a stale/rejected impulse.
5. **Dashboard is compacted** to keep the full location section visible.
6. **Location labels are offset farther right** and prefixed with `LOC` to separate them from GEX/value labels.

## Production logic

`Location direction = Auto` only activates a direction when the combined environment is already bullish or bearish. Transition/mixed environments remain blocked.

For a long location:

1. Select the completed 1H upswing ending at the latest confirmed 1H swing high.
2. Optionally refine the origin using confirmed 15M internal structure.
3. Calculate 0.705, 0.788, and 0.886 retracements.
4. Require the retracement to be in impulse discount.
5. Require the entire zone to be below active VAL.
6. Require 15M internal structure when enabled.
7. A close below 0.886 invalidates that anchor until a new impulse is selected.

The short side mirrors the same logic into impulse premium above VAH.

Trade execution remains completely manual. Order-flow confirmation is still intentionally unimplemented.
