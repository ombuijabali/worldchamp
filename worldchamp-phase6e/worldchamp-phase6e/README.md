# WorldChamp Phase 6E - Setup Ready Engine

Phase 6E completes the confirmation chain while keeping execution manual.

## Sequence

1. Absorption / failed effort.
2. Opposite-side dominance shift.
3. Retest toward the dominance bar.
4. Failed side retries but fails at a better extreme than the original failure.
5. Dominant side returns within the confirmation window.
6. `SETUP READY - LONG` or `SETUP READY - SHORT`.

No orders are placed by the script.

## Production behavior

- Dominance shift is inherited from Phase 6D.
- The original absorption/failure extreme is preserved.
- A retest must occur within the configured retest window.
- Long sequences require a higher failed-seller low; short sequences require a lower failed-buyer high.
- By default, the failed side must show retry aggression and the dominant side must return with aggression.
- Location invalidation remains binding in production.

## Static-test harness

Phase 6E includes TEST-only controls for free-plan historical validation. They can allow directional proxy delta to stand in for aggression and optionally bypass location/retest-touch constraints. Keep these controls OFF for production interpretation.
