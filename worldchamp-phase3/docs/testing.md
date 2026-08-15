# Phase 2.2 + Phase 3 Test Plan

Use the 5-minute chart and keep the 7-day development window enabled.

## Phase 2.2 checks

1. Confirm VAH/POC/VAL still match the Phase 2.1 result for the same closed session.
2. Confirm VA Overlap is populated when two valid profiles exist.
3. Visually compare the two value areas. Low overlap should produce STRONG directional migration; large overlap should produce WEAK or BALANCED/ROTATION behavior.
4. Confirm migration direction itself is unchanged from Phase 2.1.

## Phase 3 checks

1. Leave GEX disabled first. Dashboard should show GEX Regime OFF and GEX Volatility OFF.
2. Enable GEX and choose Negative. Dashboard should show NEGATIVE / AMPLIFIED.
3. Enter a gamma flip near current price. Confirm the line and ABOVE FLIP / BELOW FLIP relation.
4. Enter call and put walls and verify only those three GEX levels appear.
5. Switch Positive / Negative / Neutral and confirm only the volatility context changes. Environment direction must not flip solely because GEX changed.
6. Disable GEX and confirm all three GEX lines and labels disappear cleanly.

No trade-entry logic is expected in this phase.
