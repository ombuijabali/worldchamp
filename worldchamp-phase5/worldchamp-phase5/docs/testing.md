# Phase 5 test plan

Use a 5-minute chart.

## Test A - NAS100 CFD / relative mode
1. Leave Participation Mode on `Auto`.
2. Confirm the dashboard reports `AUTO · RELATIVE`.
3. Outside 09:30-11:00 New York, Participation must read `OUTSIDE NY` and Flow / Execution must remain gated.
4. Use Bar Replay inside 09:30-11:00. The baseline warms from prior confirmed NY-window bars, then participation should classify as `LOW`, `NORMAL`, or `HIGH` from the relative-volume ratio.
5. Default relative pass threshold is 0.80x; default HIGH threshold is 1.25x.

## Test B - MNQ futures / absolute mode
1. Open MNQ on 5 minutes.
2. Leave Participation Mode on `Auto`.
3. Confirm the dashboard reports `AUTO · MNQ ABS` and threshold defaults to 20.0K.
4. Inside the NY window, bars below 20K should read `LOW`; bars from 20K up to the default HIGH threshold should read `NORMAL`; bars at/above 25K (default 1.25x) should read `HIGH`.

## Integration gate
Even with valid participation, Flow / Execution remains `GATED · LOCATION` until price is actually inside a valid Phase 4 location. Once both location and participation pass, it should show `ARMED · NOT BUILT / MANUAL`.

## Pass conditions
- Phase 4.1 location output is unchanged.
- Outside NY always blocks the participation gate.
- Auto mode selects absolute mode only for MNQ and relative mode for the NAS100 CFD test.
- Participation does not create buy/sell signals or automated execution.
