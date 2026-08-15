# WorldChamp Phase 2

Phase 2 combines the Phase 1.2 higher-timeframe structure engine with a session Value / Auction Map.

## Added in Phase 2

- Configurable profile session (default 09:30-16:00 America/New_York)
- 1-minute intrabar OHLCV collection on the 5-minute chart
- Session VAH, POC, and VAL
- Developing profile during an active profile session
- Latest completed profile outside the session
- Session-to-session value migration
- Combined structure + value environment state
- Optional historical profile segments in debug mode
- Clean live map: only VAH, POC, and VAL are extended to the right

## Value migration states

- VALUE UP
- VALUE DOWN
- VALUE EXPANDING
- VALUE CONTRACTING
- OVERLAP UP
- OVERLAP DOWN
- OVERLAP
- WARMING

No location/Fibonacci logic, footprint/order-flow confirmation, or automated execution is present yet.
