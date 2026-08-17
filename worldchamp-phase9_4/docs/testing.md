# WorldChamp P9.4 - Location Anchor Audit Testing

Use Operating Mode = Validation on the 5-minute NAS100 chart.

P9.4 does not change production trading rules. It only expands the completed NY-session audit label.

For each 09:30-11:00 NY session, record:
- CTX P/B
- LOC V/Z/A
- BLK counts
- ANCH direction/source/age/changes
- PRE-BR Y/N
- NY-INV count
- RAW E/Z
- FINAL V
- NY open
- .705 / .788 / .886
- participation, aggression, absorption, dominance, setup counts

Interpretation:
- PRE-BR=Y + NY-INV=0 + RAW E>0 suggests a stale already-invalid anchor may be blocking the session.
- PRE-BR=N + NY-INV>0 suggests the selected impulse genuinely invalidated during NY.
- RAW E=0 means invalidation is not the only blocker; other location geometry requirements also fail.
- RAW Z>0 with FINAL V=0 and PRE-BR=Y is especially useful evidence for an anchor-refresh problem.

Do not change any thresholds yet. Send screenshots of the same Aug 10-14 sessions after P9.4 loads.
