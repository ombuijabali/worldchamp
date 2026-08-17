# WorldChamp Phase 9.5 - Location Geometry Breakdown

Validation-only diagnostics built on P9.4. Production trading logic is unchanged.

Adds independent location-geometry counters:
- LEG: usable directional anchor leg
- RNG: correct side of impulse range
- VAL: zone outside the relevant value boundary
- SW: 15M internal-swing requirement
- ALL: all four geometry requirements together
- TOUCH: candle touched the proposed zone regardless of persistent invalidation
- SEL-BR: a newly selected anchor was already beyond .886 when selected

Existing PRE-BR, NY-INV, anchor-change, raw eligibility, and final-valid counters remain.

Execution remains manual.
