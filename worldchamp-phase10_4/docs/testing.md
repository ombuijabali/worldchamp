# P10.4 Location Timing Audit - Testing

## Goal

Use the same accessible historical sample from P10.3. We are not trying to obtain more history and we are not tuning the method yet. The goal is to diagnose why valid locations form but price never reaches them during the NY execution window.

## Trading logic status

TRADING LOGIC UNCHANGED.

Do not change .705/.788/.886, value-side rules, 15M swing requirements, participation, aggression, absorption, dominance, setup thresholds, or the 09:30-11:00 NY window during this test.

## Run

1. Load NAS100USD (OANDA), 5 minute.
2. Add WorldChamp P10.4.
3. Set Operating Mode to Validation.
4. Leave the current historical validation window and thresholds unchanged.
5. Open Pine Logs.
6. Filter/search for WCLOG.
7. Export or copy the available WCLOG rows and send them back for analysis.

P10.4 recalculates the existing accessible history, so the same roughly 20 sessions are enough for this diagnostic pass.

## New fields to inspect

- FV_FIRST_M / FV_LAST_M: when the valid location appears and how long it survives.
- FV_PRET: whether price had already touched the eventual first-valid zone before the location became valid.
- FV_GAP_PCT / FV_GAP_M: how far price actually stayed from the valid zone and when it got closest.
- FV_ZDRIFT_PCT / FV_END_CHG: whether the developing endpoint is moving the zone away after validity begins.
- R15_FIRST_M / R1_FIRST_M: whether re-arm timing is late inside the NY window.

## Decision logic after analysis

No rule changes are authorized merely because LOC_Z remains zero.

We first classify the cause:

- Late qualification: FV_FIRST_M is late and/or FV_PRET=1.
- Zone drift: FV_END_CHG and FV_ZDRIFT_PCT are large while price never closes the gap.
- Genuine shallow retracement: FV appears early, FV_PRET=0, drift is small, but FV_GAP_PCT stays materially above zero.
- Re-arm timing: R15_FIRST_M is late and closely precedes FV_FIRST_M.

Only after the data identifies one of these mechanisms should the next phase propose a trading-rule change.
