# P10.6 Testing — 15M Confirmation Delay Audit

Use the same setup as the existing WorldChamp validation:

- Symbol: `OANDA:NAS100USD`
- Timeframe: 5 minutes
- Mode: Validation
- Same accessible historical sample (approximately Jul 20–Aug 14, 2026)
- Do not change thresholds.

## New WCLOG fields

- `FV_CONF_READY_M` — minute relative to 09:30 NY when the selected 15M pivot is mathematically confirmable. With strength 2, this is origin + 30 minutes.
- `FV_STAB_DELAY_M` — minutes between mathematical confirmation and the first production-valid location. Current architecture is expected to show about 15 minutes.
- `FV_PRECONF_Z` — whether the eventual first-valid .705–.886 zone was touched during the NY window **before** the pivot was confirmable. A hit here cannot be recovered without using an unconfirmed/predictive pivot.
- `FV_PRECONF_RT` / `_M` — deepest retrospective retracement and its NY-minute during that pre-confirmation interval.
- `FV_STAB_Z` — whether the eventual first-valid zone was touched during the NY window **after** the pivot was mathematically confirmed but **before** the extra stability bar released it. This is the decisive field for whether the extra `[1]` stability offset is costing valid opportunities.
- `FV_STAB_Z_M` — first such touch minute.
- `FV_STAB_RT` / `_M` — deepest retracement during the extra stability interval.

## Decision rule

1. If `FV_STAB_Z=1` on one or more valid-location sessions, the next controlled experiment should remove only the extra 15M stability offset for the **temporary 15M re-arm**, while keeping the pivot fully confirmed (strength 2).
2. If `FV_STAB_Z=0` but `FV_PRECONF_Z=1`, reducing the extra stability offset would not have captured the touch; doing so would require predictive/unconfirmed structure, which we should not adopt without much stronger evidence.
3. If both are 0, the missed touch occurred outside the execution window or reflects genuinely shallow retracement / other timing geometry.

Send/export the Pine Logs CSV after loading P10.6.
