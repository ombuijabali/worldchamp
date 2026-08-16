# Phase 5.1 testing without Bar Replay

1. Load the script on a 5-minute chart with `7D Test` enabled.
2. Keep `Show historical NY participation markers` enabled.
3. Scroll to any completed 09:30-11:00 New York window.
4. Read the markers at the bottom of each bar:
   - H = HIGH
   - N = NORMAL
   - L = LOW
   - W = WARMING
   - X = NO VOLUME
5. At the end of each NY window, inspect the compact summary label, e.g. `P H3 N9 L6 W0 X0`.
6. For OANDA NAS100 in Auto mode, the script should use relative volume.
7. For MNQ in Auto mode, the script should use the absolute threshold (default 20,000 contracts per 5-minute candle).
8. Confirm Phase 4.1 location drawings/states remain unchanged.

Expected early behavior: the first session(s) can show W markers while the relative baseline accumulates enough samples. Later sessions should classify H/N/L normally.
