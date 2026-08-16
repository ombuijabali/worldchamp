# Phase 6D Static Testing

Use NAS100USD 5M and the same 7-day window. No Bar Replay is required.

## Production test
Keep both dominance TEST toggles OFF. A full absorption must occur with valid upstream context before dominance can arm. Zero shifts is valid.

## Free-plan state-machine test
If the sample has no full absorption, enable `TEST: allow potential absorption seed`. If the location gate prevents that historical event from arming, also enable `TEST: bypass location context for seed`. The dashboard State must clearly show TEST.

Check that:
- a seed always precedes a shift; same-bar confirmation never happens;
- seller absorption can only lead to a buyer shift;
- buyer absorption can only lead to a seller shift;
- the shift happens within the configured lookahead or the seed expires;
- buyer shift has buyer aggression + bullish progress; seller shift has seller aggression + bearish progress;
- midpoint reclaim is respected when enabled;
- `DOM PROXY Seed# B# S# Exp#` is an event summary, so it does not need to total 18;
- execution remains manual.

Send a screenshot of a completed NY session with absorption marker(s), any dominance square(s), the DOM PROXY label, and the dashboard Dominance row. A seed followed by expiry is also a valid test case.
