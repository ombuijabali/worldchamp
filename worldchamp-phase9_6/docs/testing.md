# P9.6 Developing-Anchor Validation

Use NAS100USD on the 5-minute chart and set Operating mode = Validation.

Keep all production thresholds unchanged. Leave GEX OFF unless you have real session-specific GEX inputs.

Re-check the historical NY 09:30-11:00 sessions that previously had CTX P > 0.

For each session, read the orange WC VAL audit label and record:

- CTX P / B
- ANCH direction/source/age
- PRE-BR
- SEL-BR
- NY-INV
- CHG
- GEO L / R / V / S / A / T
- RAW E / Z
- FINAL V

Primary pass condition:

- `SEL-BR` should no longer be 1 simply because the location direction activates after an old completed 1H swing.

Secondary observations:

- If `SEL-BR` improves but `GEO V` remains 0, the value-side requirement becomes the next item to review.
- If `GEO V` becomes positive and `A`/`RAW E` become positive, the stale anchor was causing the apparent value-side failure.
- Do not loosen .886 or value rules during this test.

Production regression check:

Switch to Production after the validation screenshots and confirm the chart remains clean and execution remains manual.
