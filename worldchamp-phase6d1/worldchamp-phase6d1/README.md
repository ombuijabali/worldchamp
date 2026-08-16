# WorldChamp Phase 6D.1 - Dominance Diagnostic Harness

Phase 6D.1 keeps the Phase 6D production dominance logic intact and adds a TEST-only diagnostic harness so the dominance-confirmation branch can be exercised on static historical charts without Bar Replay.

## Production behavior

When **TEST: dominance diagnostic mode** is OFF, the script uses the same Phase 6D production rules:

- qualified absorption seed,
- opposite-side aggression,
- production progress/close-location thresholds,
- optional absorption-midpoint reclaim,
- production lookahead,
- location invalidation remains binding.

## Diagnostic behavior

When diagnostic mode is ON, TEST-only controls can:

- seed from potential absorption or any aggression event,
- use directional proxy delta instead of full aggression for the opposite-side proof,
- extend the lookahead window,
- relax body-progress and close-location thresholds,
- ignore midpoint reclaim,
- bypass location invalidation,
- show candidate circles before a confirmed dominance square.

These relaxations never apply with diagnostic mode OFF.

Trade execution remains manual. Retest/second-failure logic is still not implemented.
