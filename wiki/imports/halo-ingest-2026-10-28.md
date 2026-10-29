# Import: HALO TMA exports, 28 Oct 2026 (withdrawn)

Status: superseded
Superseded by: [[halo-reexport-2026-10-28]]
Last updated: 2026-10-28

Seven HALO v4.3.6992 archives exported 09:33–09:36 on 2026-10-28 (ASS1, ASCL4,
LC3A/B, CBP, ERG, SLFN11, p300). Withdrawn the same morning; Bora is re-exporting
each marker one at a time. Nothing from this batch remains in `Data/raw/`.

## What went wrong

The exports were run in parallel. Two archives held a summary CSV for a different
marker from their object data (CBP summary beside p300 objects; ERG summary beside
SLFN11 objects), written about two minutes after the object data. Three archives
had no summary. Likely cause: later exports wrote their summary into earlier
archive folders, overwriting the p300 and SLFN11 summaries.

ASS1 and ASCL4 had passed full per-core reconciliation (cell and positive-cell
counts, image regions and analysis start times all matched) and were briefly filed
in `Data/raw/`; withdrawn with the rest at Bora's choice.

## Disposal

All files moved to `Data/incoming/_to_delete/2026-10-28 exports/` for Bora to
delete. One empty archive folder (`Halo archive 2026-10-28 09-34-56`) was locked
by another program and left in `Data/incoming/`.

## Sources
- Related: [[stain-inventory]], [[tma-halo-ingest]], [[ass1]], [[ascl4]], [[lc3ab]], [[cbp]], [[erg]], [[p300]], [[slfn11]]
