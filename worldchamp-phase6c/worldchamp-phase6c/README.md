# WorldChamp Phase 6C - Absorption / Effort vs Result

Phase 6C extends the locked Phase 6B aggression engine with a conservative Free-plan-compatible absorption proxy.

## What it adds

- Aggression remains the required first step.
- Each aggressive 5-minute bar is scored on three mirrored price-result tests:
  1. poor directional body progress,
  2. close recovery away from the aggressor-side extreme,
  3. rejection wick against the aggressor.
- Score 3/3 = absorption suspected.
- Score 2/3 = potential absorption.
- Seller absorption means aggressive sellers failed to achieve proportional downside result.
- Buyer absorption means aggressive buyers failed to achieve proportional upside result.
- Historical markers and a session summary make validation possible without Bar Replay.

## Important limitation

This build still uses the lower-timeframe directional-volume proxy introduced in Phase 6A. It is not true bid/ask footprint delta and does not claim to be. Native TradingView footprint support remains the future Premium/Ultimate upgrade path.

## Still not implemented

- dominance shift,
- retest / second failure,
- setup-ready state,
- automatic trade execution.
