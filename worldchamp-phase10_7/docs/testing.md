# WorldChamp P10.7 - Clean Confirmation Audit

## Purpose

Use the same accessible 20-session NAS100USD/OANDA 5-minute Validation sample. No new history is required.

P10.7 changes diagnostics only. Trading rules, fib levels, value rules, 15M structure, session window, order flow, READY logic, plans, and management are unchanged.

## Why P10.7 exists

P10.6 reported `FV_PRECONF_Z=1` with `FV_PRECONF_RT=100` at minute 0 on Aug 6 and Aug 12. Those sessions had a 15M origin at 09:30. The audit interval included the structural-origin bar itself, which is not a post-origin pullback and can mechanically span the eventual deep retracement zone.

P10.7 therefore adds a second pre-confirmation audit that starts one 5-minute bar after the pivot origin.

## New WCLOG fields

- `FV_PRECONF_POST_Z`: eventual first-valid .705-.886 zone touched after the origin bar but before mathematical 15M pivot confirmation.
- `FV_PRECONF_POST_Z_M`: first such touch in NY minutes from 09:30.
- `FV_PRECONF_POST_RT`: deepest retrospective retracement after the origin bar but before mathematical confirmation.
- `FV_PRECONF_POST_RT_M`: time of that deepest retracement.

The old `FV_PRECONF_Z/RT` fields remain in the log for comparison, but for origins inside NY use the new `POST` fields when deciding whether a genuine post-origin pullback occurred before confirmation.

## Decision rule

1. If `FV_PRECONF_POST_Z=1`, a genuine post-origin zone touch occurred before the 15M pivot could be confirmed. Capturing it would require earlier/unconfirmed structural information, so do not change the trading rule automatically.
2. If `FV_PRECONF_POST_Z=0` and `FV_STAB_Z=0`, neither the unavoidable confirmation interval nor the optional 15-minute stability interval contained an actual .705-.886 touch. Confirmation latency is then not the reason for the zero production touches in that session.
3. Track `FV_PRECONF_POST_RT` and `FV_STAB_RT` for near-misses. A retracement below 70.5% is still not a valid zone touch.

## Run

- Symbol: OANDA:NAS100USD
- Timeframe: 5 minutes
- Mode: Validation
- Use the same accessible history/sample as P10.6.
- Open Pine Logs and export/copy all `WCLOG` records.
- Send the resulting CSV/logs for analysis.
