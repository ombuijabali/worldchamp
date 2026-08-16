# Phase 6D.1 Static Test

Use the same NAS100USD 5-minute chart and completed 09:30-11:00 New York session.

## Recommended diagnostic settings

- TEST: dominance diagnostic mode = ON
- TEST: diagnostic seed source = Any Aggression
- TEST: diagnostic lookahead bars = 8
- TEST: diagnostic min body progress = 10%
- TEST: diagnostic min close location = 52%
- TEST: allow directional delta as opposite-side proof = ON
- TEST: ignore absorption midpoint reclaim = ON
- TEST: show dominance candidates = ON

You can leave the older potential-seed/context-bypass toggles OFF; diagnostic mode already provides its own isolated test path.

## Expected visuals

- Aqua circle below a bar: TEST buyer-dominance candidate.
- Orange circle above a bar: TEST seller-dominance candidate.
- Green square below: buyer dominance confirmed.
- Red square above: seller dominance confirmed.

At the end of the NY window, inspect a summary similar to:

`DOM DIAG Seed3 CB2 CS1 B1 S0 Exp1 TEST`

Candidate and event counts are event counters; they do not need to total 18.

## Pass conditions

1. At least one seed is created.
2. Opposite-direction candidate circles appear only after a seed and inside its lookahead window.
3. A square appears only when the relaxed diagnostic progress + close-location tests also pass.
4. If no confirmation occurs, the sequence expires rather than persisting indefinitely.
5. With diagnostic mode OFF, the script returns to Phase 6D production behavior.
6. No automated orders are created.
