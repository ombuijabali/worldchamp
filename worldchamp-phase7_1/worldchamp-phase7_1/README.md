# WorldChamp Phase 7.1

Compiler fix for Phase 7 target sorting.

Pine Script v6 does not expose `array.swap()`. Phase 7.1 replaces the two unsupported calls with synchronized `array.get()` / `array.set()` swaps so target prices and their labels remain paired while sorting.

No trading logic, target-selection logic, or Phase 6E setup logic was changed.
