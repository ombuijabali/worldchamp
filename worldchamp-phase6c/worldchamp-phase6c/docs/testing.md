# Phase 6C Static Testing

Use NAS100USD 5-minute or another symbol with usable volume.

## Default thresholds

- Aggression floor: 25%
- Absorption max directional progress: 35%
- Absorption min counter-recovery: 45%
- Absorption min rejection wick: 20%

## Historical markers

- Green diamond below bar: seller absorption suspected (3/3)
- Red diamond above bar: buyer absorption suspected (3/3)
- Faded green circle below bar: potential seller absorption (2/3)
- Faded red circle above bar: potential buyer absorption (2/3)

## Session summary

At the end of the 09:30-11:00 NY window, the label format is:

`ABS PROXY SA# BA# P# N# X#`

For a complete 90-minute session, SA + BA + P + N + X should total 18 five-minute bars.

## What to verify

1. Absorption appears only on bars that already meet Phase 6B aggression.
2. Seller absorption should visually correspond to aggressive selling with poor downside result/rejection.
3. Buyer absorption should visually correspond to aggressive buying with poor upside result/rejection.
4. Potential markers should be more common than full 3/3 absorption markers.
5. No setup-ready or trade-entry signal should exist yet.
