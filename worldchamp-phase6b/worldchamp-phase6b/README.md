# WorldChamp Phase 6B - Aggression Engine

Phase 6B builds on the validated Phase 6A lower-timeframe proxy data layer.

## Adds

- Adaptive aggression thresholding from prior NY-session absolute delta %.
- Configurable fixed delta floor.
- Optional participation requirement.
- Buyer/seller aggression classification.
- Strong-vs-active aggression grading.
- Static historical aggression markers for Free-plan testing.
- Session aggression summary.

## Important

This Free-plan build uses lower-timeframe directional-volume proxy data. It is not true bid/ask footprint delta. Native `request.footprint()` remains a future upgrade path for plans that support it.

No absorption, dominance shift, second failure, or automated execution is implemented yet.
