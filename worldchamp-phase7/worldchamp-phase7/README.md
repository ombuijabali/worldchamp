# WorldChamp Phase 7 - Invalidation + Target Map

Phase 7 extends the validated Phase 6E confirmation chain. It does **not** execute trades.

When WorldChamp reaches `SETUP READY`, Phase 7 snapshots an informational trade map:

- `READY REF`: the close of the setup-ready candle. This is a reference price, not an executed entry.
- `INV`: the original failed-participant extreme, with an optional tick buffer.
- `T1 / T2 / T3`: the nearest structural/context targets in the setup direction.

Target candidates can come from:

- current POC and directional value edge,
- prior POC / prior value area,
- confirmed 1H swing high/low,
- confirmed 4H swing high/low,
- directional GEX wall when manually supplied.

The script removes duplicate levels, ignores targets on the wrong side of the READY reference, sorts the remaining candidates by distance, and uses the nearest three. If the market provides fewer than three valid structural targets, the script intentionally shows fewer targets instead of inventing arbitrary profit targets.

The dashboard tracks whether the invalidation or targets have been touched, but this is not a brokerage position tracker because execution remains manual.
