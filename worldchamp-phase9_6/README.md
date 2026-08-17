# WorldChamp Phase 9.6 - Developing 1H Impulse Anchor

P9.6 fixes the stale-anchor behavior identified by the P9.5 validation audit.

## Evidence from P9.5

On every audited session where directional context passed, the selected location anchor was already beyond its .886 boundary (`SEL-BR1`). At the same time, the location geometry breakdown showed the value-side gate at zero while leg/range/15M-swing geometry was otherwise available.

## Fix

The location engine no longer waits for a fully completed 1H low->high or high->low swing pair to define the impulse endpoint.

- Long origin: latest confirmed 1H swing low.
- Long endpoint: highest 5M high observed since that confirmed low.
- Short origin: latest confirmed 1H swing high.
- Short endpoint: lowest 5M low observed since that confirmed high.
- 15M origin refinement remains enabled exactly as before.
- The endpoint only moves when the impulse genuinely extends.
- Historical scanning is backward-only; no future bars are used.

## Unchanged

The .886 invalidation rule, value-side rule, impulse discount/premium rule, 15M swing requirement, participation, order flow, absorption, dominance, setup-ready, plan quality, and manual execution are unchanged.

## Validation objective

Re-run the same context-pass NY sessions in Validation mode. We want `SEL-BR` to fall from 1 toward 0. Only after that do we judge whether the value-side gate still needs adjustment.
