# Phase 6A Static Test

No Bar Replay is required.

## 1. Compile / load

Load `pine/worldchamp.pine` on a 5-minute chart. Keep the profile lower timeframe at 1 minute.

Expected header: `WorldChamp P6A`.

## 2. Confirm status-line cleanup

The colored `0.0 0.0 ...` values that leaked from Phase 5.1 participation plotchars should no longer appear beside the indicator title.

## 3. Confirm current-bar data row

The dashboard now includes `OF Data`.

On a symbol with lower-timeframe volume it should resemble:

`LTF TICK PROXY - 5/5 - Delta +20.4% - READY`

or

`LTF VOL PROXY - 5/5 - Delta -31.7% - READY`

Historical 5-minute bars normally have five 1-minute samples. A partially formed realtime bar can contain fewer.

## 4. Static historical NY test

Scroll to a completed 09:30-11:00 New York window.

Top-of-chart markers:

- `+` = positive proxy delta.
- `-` = negative proxy delta.
- `0` = delta within the configured neutral band.
- `X` = insufficient lower-timeframe data/volume.

At the end of the window, the script prints an order-flow summary above price, e.g.:

`OF PROXY +8 -7 03 X0 avgDelta -4.2%`

The counts should total 18 bars for a complete 90-minute 5-minute session unless data is missing.

## 5. Participation markers

The existing Phase 5 `H/N/L/W/X` markers remain below price. Their values should no longer leak into the TradingView status line.

## 6. Gate behavior

The Flow / Execution row can now report:

- `GATED - LOCATION / MANUAL`
- `GATED - SESSION / MANUAL`
- `GATED - VOLUME / MANUAL`
- `GATED - OF DATA / MANUAL`
- `ARMED - DATA READY / MANUAL`

Phase 6A stops here. `ARMED - DATA READY` means only that the future aggression module is allowed to inspect the bar. It is not an entry signal.

## Important interpretation

This build uses lower-timeframe directional feed volume as a proxy. It must not be interpreted as exact bid/ask aggressor volume. Native footprint integration is a separate Premium/Ultimate upgrade path.
