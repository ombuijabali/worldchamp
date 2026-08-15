# WorldChamp Phase 2.1

Phase 2.1 keeps the Phase 1.2 structure engine and Phase 2 value-map logic, while adding explicit data diagnostics for the profile feed.

## Why this patch exists

If a profile session provides no usable lower-timeframe volume, Phase 2 could show `LAST CLOSED` while VAH/POC/VAL remained `n/a`. Phase 2.1 distinguishes:

- `WARMING`: no completed lower-timeframe sample set yet.
- `NO VOLUME DATA`: samples exist, but none have positive volume.
- `PROFILE INVALID`: positive-volume samples exist but the profile still could not be computed.
- `LAST CLOSED`: a valid completed profile exists.
- `NO VOL · PRIOR MAP`: latest attempted session had no usable volume, so the last valid map is preserved.

The Volume Source row also reports `positive_samples / total_samples`.

No entry, exit, or automated execution logic is included.
