# Phase 6B Testing

Use a 5-minute chart and keep the recent 7-day development window enabled.

## What to verify

1. The script compiles and loads as `WorldChamp P6B`.
2. Historical NY-session participation markers from Phase 5 remain intact.
3. Ordinary raw `+/-` delta markers are hidden by default.
4. Only aggressive bars show markers:
   - upward triangle below the bar = buyer aggression
   - downward triangle above the bar = seller aggression
5. A completed NY session prints an aggression summary similar to:
   `AGG PROXY B2 S4 N12 X0 thr 31.6%`
   Counts should total 18 bars for 09:30-11:00.
6. The dashboard row `OF / Aggression` shows:
   - proxy source
   - lower-timeframe sample quality
   - current proxy delta %
   - current aggression threshold
   - FIXED or ADAPT threshold mode
   - aggression state
7. Outside NY, aggression state should read `OUTSIDE NY`.
8. Phase 4 location values and Phase 5 participation output should remain unchanged.

## Expected Free-plan limitation

This build is a directional-volume proxy, not true bid/ask delta. Do not interpret the proxy values as exchange footprint data.
