# WorldChamp Phase 3

This build includes both requested upgrades.

## Phase 2.2

- Calculates value-area overlap percentage between the active and reference profile.
- Grades directional migration as STRONG, MODERATE, or WEAK.
- Keeps the original migration direction states (VALUE UP, VALUE DOWN, etc.).

Overlap is measured as the overlapping width divided by the smaller of the two value-area widths. This makes 100% mean the smaller value area is fully contained in the other area.

Quality thresholds used for directional migration:

- 0-20% overlap: STRONG
- >20-50%: MODERATE
- >50%: WEAK

## Phase 3

Manual GEX context is added because the project does not assume a reliable automatic GEX feed inside Pine.

Inputs:

- Gamma regime: Positive / Negative / Neutral
- Gamma flip
- Call wall
- Put wall

Interpretation:

- Positive gamma: DAMPENED volatility context
- Negative gamma: AMPLIFIED volatility context
- Neutral: NEUTRAL volatility context

GEX never creates a long or short signal and does not overwrite structure/value direction. Trade execution remains manual.
