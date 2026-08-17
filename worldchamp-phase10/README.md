# WorldChamp Phase 10 - Validation Logger

P10 freezes the P9.8.1 trading logic and adds a machine-readable NY-session logger for extended validation.

## New in P10

- One export record per completed 09:30-11:00 New York session.
- 20 numeric `VAL_*` indicator series exposed in the Data Window / chart-data export without drawing extra lines on the chart.
- Default historical window is 45 calendar days (adjustable to 90), which is usually enough to capture about 30 market sessions.
- Internal session-history retention is 30 sessions; the on-chart NY AUDIT table still shows only the latest 7 for readability.
- `VAL_ANCHOR_SOURCE` encodes the last audit source: `15` = 15M REARM, `1` = 1H-derived, `0` = none.

## Trading logic

No context, location, .886, 15M re-arm, participation, aggression, absorption, dominance, setup, plan, or management thresholds changed. Execution remains manual.
