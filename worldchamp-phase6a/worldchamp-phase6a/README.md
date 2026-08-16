# WorldChamp Phase 6A - Order-Flow Data Acquisition

Phase 6A adds the first order-flow layer while preserving every validated module from Phases 0-5.

## Free-plan implementation

TradingView native `request.footprint()` data is not used in this build because native footprint requests require a Premium or Ultimate TradingView plan. The main WorldChamp build therefore stays compatible with the user's current Free plan.

Instead, Phase 6A reuses the existing lower-timeframe arrays (default 1-minute data inside each 5-minute bar) and builds a transparent directional-volume proxy:

- 1M close > open: volume assigned to the buy proxy bucket.
- 1M close < open: volume assigned to the sell proxy bucket.
- 1M doji: close-to-close direction is used when available; otherwise volume is neutral.
- Proxy delta = buy proxy volume - sell proxy volume.
- Proxy delta % = proxy delta / total proxy feed volume.

This is deliberately labelled `PROXY` in the dashboard. It is not true exchange bid/ask footprint delta.

## Phase 6A adds

- Lower-timeframe sample-quality diagnostics.
- Buy/sell/neutral proxy-volume buckets.
- Delta and delta-percent calculation.
- Historical `+`, `-`, `0`, `X` markers during the NY active window.
- NY-session order-flow proxy summary labels for testing without Bar Replay.
- A new `OF Data` dashboard row.
- Flow gate state `ARMED - DATA READY` when location, session, participation, and data quality all pass.
- Status-line cleanup for the Phase 5 historical participation markers.

## Not included yet

- Aggression thresholding (Phase 6B).
- Absorption / effort-vs-result detection (Phase 6C).
- Dominance shift (Phase 6D).
- Second failure / setup-ready state (Phase 6E).
- Automated execution.
