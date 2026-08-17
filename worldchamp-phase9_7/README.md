# WorldChamp Phase 9.7 - Anchor Retirement + Fresh Re-arm

P9.7 fixes the stale-origin lifecycle exposed by P9.6 validation.

An active developing impulse that breaches `.886` retires its confirmed 1H origin. That origin cannot be reused after a bounce. The corresponding long/short location engine re-arms only after a newer confirmed 1H opposite swing origin appears.

The developing endpoint from P9.6 is retained. No `.886`, value-side, 15M swing, participation, order-flow, setup, plan-quality, or management thresholds are loosened. Trade execution remains manual.
