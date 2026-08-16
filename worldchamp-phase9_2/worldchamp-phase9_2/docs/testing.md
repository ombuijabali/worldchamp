# WorldChamp Phase 9.2 Testing

## Mode safety

- Production: production rules, TEST overrides forced OFF, clean live visuals.
- Validation: production rules, TEST overrides forced OFF, historical validation visuals allowed.
- Debug: TEST overrides may affect logic and full diagnostics are available.

## Validation check

Set Operating mode = Validation.

Expected:
- LOCATION should show AUTO, never TEST.
- No SETUP DIAG / TEST state may appear from stale saved inputs.
- Historical H/N/L, aggression, absorption, dominance, retest and setup audit visuals may appear.
- The 7-day window may still be used in Validation.
- State row should identify P9.2 VALIDATION MANUAL unless a normal production state changes the descriptive text.

## Debug check

Set Operating mode = Debug.

Expected:
- TEST controls can be enabled intentionally.
- Diagnostic markers and summaries are available.

Execution remains manual in every mode.
