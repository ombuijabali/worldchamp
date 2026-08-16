# WorldChamp Phase 9 - Production Cleanup

Phase 9 does not add new trading logic. It packages the validated Phase 8 engine into a cleaner operating workflow for real chart use and the planned seven-day integrated validation.

## Operating modes

- Production: forces location direction to Auto, disables every TEST override, hides historical validation markers/summaries, disables the development-window restriction, and leaves only live/relevant decision support plus the latest plan map.
- Validation: enables the configured recent-window filter, keeps the static historical validation markers, and replaces the many module summaries with one compact WorldChamp session summary.
- Debug: keeps Validation behavior and additionally enables raw diagnostic visuals and individual module summaries when their toggles are enabled.

## Final dashboard

The dashboard is reduced from 34 rows to 21 rows. It groups the system into:

1. Chart/session
2. HTF structure
3. Value and GEX context
4. Environment
5. Location
6. Participation and order flow
7. Plan map, quality, status, and management

## Production chart behavior

Production mode keeps historical validation clutter off. SETUP READY and management markers are live-only in Production, while the latest READY plan map remains available as the main reference.

Trade execution remains manual. No strategy orders are generated.
