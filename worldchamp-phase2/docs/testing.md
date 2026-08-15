# Phase 2 - 7-day validation

## Basic compile/run

1. Use a standard 5-minute candle chart.
2. Leave Profile session at 09:30-16:00 New York for the first test.
3. Leave Profile lower timeframe at 1 minute.
4. Leave Profile rows at 40 and Value area at 70%.
5. Confirm there are no compiler/runtime errors.

## Visual checks

1. The chart should show only three current/latest profile lines in normal mode:
   - VAH: aqua solid
   - POC: yellow dotted
   - VAL: aqua solid
2. The dashboard should show `LAST CLOSED` while the market/profile session is inactive.
3. VAH must be above POC, and POC must be above VAL.
4. Turn Debug mode ON and `Show closed-session VAH/POC/VAL segments` ON. Confirm each completed 09:30-16:00 session gets its own three short profile segments.
5. Compare two consecutive sessions manually. Check whether the Value Migration label matches the movement of their value areas.

## Structure checks

Confirm the Phase 1.2 mappings still work:
- HH + HL => TREND UP
- LH + LL => TREND DOWN
- LH + HL => CONTRACTING
- HH + LL => EXPANDING

## Instrument note

On spot/forex symbols such as XAUUSD, the available volume is broker/data-feed or tick-volume-like data rather than centralized futures exchange volume. Use XAUUSD to validate mechanics and drawings. Later, validate the production auction map on the futures instrument used for execution/context (for example MNQ/NQ) before trusting volume-derived decisions.

## Send back

Send a screenshot with:
- WorldChamp Phase 2 only
- 5-minute chart
- dashboard visible
- debug historical profiles ON for one screenshot if possible

If Pine reports an error, send the exact compiler line/message before changing anything else.
