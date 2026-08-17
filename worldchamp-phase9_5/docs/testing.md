# P9.5 validation test

1. Use NAS100USD 5M.
2. Set Operating Mode = Validation.
3. Keep production thresholds unchanged.
4. Capture each completed NY 09:30-11:00 session.
5. Read the session label:
   - GEO L/R/V/S/A/T
   - PRE-BR / SEL-BR / NY-INV / CHG
   - RAW E/Z and FINAL V
6. Send Aug 10-14 screenshots.

Interpretation:
- GEO L high, R high, V zero => value-side rule is bottleneck.
- GEO L/R/V high, S zero => 15M swing rule is bottleneck.
- GEO A > 0 but FINAL V = 0 with SEL-BR/PRE-BR high => invalidation/anchor lifecycle is bottleneck.
- T > 0 but A = 0 => price touched a proposed zone whose geometry was otherwise invalid.

No P9.5 diagnostic counter changes trading decisions.
