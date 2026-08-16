# Phase 6E Static Testing

Use a 5-minute chart and a completed 09:30-11:00 New York session.

## First pass: diagnostic sequence

To exercise the branch on the same historical sample used for Phase 6D.1:

- Keep the Phase 6D.1 dominance diagnostic settings that produced confirmed dominance squares.
- Set `TEST: setup diagnostic mode` = ON.
- Set `TEST: directional delta can prove retry/return` = ON.
- If no retest appears, temporarily set `TEST: ignore retest-reference touch` = ON.
- Keep `TEST: bypass location context after dominance` = ON for the diagnostic pass.

## Visual sequence

- dominance square = Phase 6D shift,
- yellow circle = retest detected,
- aqua/orange diamond = second failure confirmed,
- `READY L` / `READY S` = final setup-ready state.

## Session summary

At NY-session end, expect a label like:

`SETUP DIAG Arm3 Ret2 SF1 L1 S0 Exp1 TEST`

These are event counts and do not need to total 18.

## What to verify

1. A retest never occurs before its dominance shift.
2. For a long, the retest low remains above the original seller-failure low.
3. For a short, the retest high remains below the original buyer-failure high.
4. READY occurs only after a retest and a later dominant-side return bar.
5. No automatic order is placed.
6. With setup diagnostic mode OFF, production rules remain strict.
