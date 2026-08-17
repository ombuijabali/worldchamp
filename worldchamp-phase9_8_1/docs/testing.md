# WorldChamp P9.8.1 Validation Log Hotfix

P9.8.1 does not change trading logic. It fixes historical audit visibility.

## What changed

- Keeps the existing per-session orange validation label.
- Adds a fixed `NY AUDIT` table in Validation mode containing the last 7 completed NY sessions.
- Uses the final NY bar (`time[1]`) for the 7-day window boundary check.
- The table records:
  - Context pass/block counts (`C pass/block`)
  - Retire count (`RET`)
  - 15M re-arms (`R15`)
  - 1H re-arms (`R1`)
  - Last audit anchor source
  - Geometry `L/R/V/S/A/T`
  - Final valid location bars (`FV`)

## Test

1. Load P9.8.1 on NAS100USD 5M.
2. Set Operating Mode = Validation.
3. Keep Calendar days = 7.
4. Do not change trading thresholds.
5. Look at the fixed `NY AUDIT` table at bottom-right.
6. Confirm Aug 10-14 all appear, even if an orange historical label is missing.
7. Send one screenshot showing the audit table. We should no longer need five separate screenshots just to read lifecycle counters.
