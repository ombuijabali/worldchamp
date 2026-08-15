# WorldChamp Phase 4 - Location Engine

Phase 4 adds the location layer on top of the validated Phase 3 environment stack.

## Included modules

- 4H / 1H confirmed structure
- Session VAH / POC / VAL
- Value migration + overlap quality
- Manual GEX volatility context
- **NEW: 1H -> 15M location engine**

## Phase 4 location rules

The production `Auto` mode only activates a direction when the combined environment is already bullish or bearish. Transition/mixed environments stay blocked.

For a long location:

1. Select the completed 1H upswing ending at the latest confirmed 1H swing high.
2. Optionally refine the impulse origin using confirmed 15M internal structure.
3. Calculate retracements from the impulse high: 0.705, 0.788, 0.886.
4. Require the zone to sit in the lower half of the impulse (discount).
5. Require the full location zone to be below the active VAL (outside value).
6. Require confirmed 15M internal structure when the corresponding toggle is enabled.
7. A confirmed close below 0.886 invalidates that anchor until a new impulse is selected.

The short side mirrors the same logic into premium above VAH.

## States

- `CONTEXT BLOCKED`
- `LEG WARMING`
- `ANCHOR INVALID`
- `NO VALUE MAP`
- `INSIDE VALUE · REJECT`
- `NO 15M SWING`
- `VALID · WAIT PULLBACK`
- `APPROACHING LONG / SHORT`
- `IN LONG / SHORT LOCATION`
- `INVALIDATED < .886 / > .886`

## Test override

`Location direction` contains:

- `Auto` - production logic.
- `Force Long (Test)` - visualization/logic validation only.
- `Force Short (Test)` - visualization/logic validation only.

When forced, the dashboard marks the location and state as `TEST` so it cannot be confused with an automatically approved environment.

Trade execution remains completely manual. Order-flow confirmation is still intentionally unimplemented.
