# Workflow: ingest a HALO TMA export

Status: settled
Last updated: 2026-08-05

Follow this procedure when a new HALO archive lands in `Data/incoming/` or when processing
unprocessed archives from the source folder. Do not ask the user for confirmation at each
step — execute the full procedure and report what was done.

## Identifying the marker

Read the summary CSV header. The marker name is embedded in the column names:
`{Marker} Positive Cells`, `{Marker} Avg Cytoplasm OD`, etc. Extract the marker name from
any such column. This is deterministic — every HALO single-marker IHC export follows this
convention.

If the summary CSV is missing but object data exists, read the first line of the object data
CSV instead and extract the marker from columns like `{Marker} Positive Classification` or
`{Marker} Cytoplasm OD`.

## QC checks

1. **Marker consistency.** Extract the marker name from BOTH the summary CSV and the object
   data CSV headers. If they disagree, **stop and report the mismatch**. Do not ingest.
   This catches a known HALO export failure where summary and object data come from
   different stain runs.
2. **Row count.** The TMA has 98 cores. Fewer rows means cores were excluded or failed QC.
   Record the count; do not block ingestion.
3. **Column structure.** Confirm the standard HALO TMA columns are present: TMA Block Name,
   Spot Id 1, Spot Valid, TMA Row, TMA Column, and the per-layer breakdown
   (Tumour/Stroma/Other). See [[halo-export-format]] for the full reference.
4. **Duplicate check.** If `Data/raw/{MARKER}/` already exists, this is a re-export. Note
   the version being replaced.

## Renaming and filing

Rename files to the project convention:
- Summary: `PDX_TMA_{MARKER}_Summary.csv`
- Object data (combined): `PDX_TMA_{MARKER}_object_data.csv`

The HALO TMA export contains a single combined `Total_Object_Results.csv`. Rename it to
`PDX_TMA_{MARKER}_Objects.csv` and place it inside an `ObjectData/` subfolder.

Move into `Data/raw/{MARKER}/`:
```
Data/raw/{MARKER}/
  PDX_TMA_{MARKER}_Summary.csv
  ObjectData/
    PDX_TMA_{MARKER}_Objects.csv
```

## Wiki updates

1. Create `wiki/entities/{marker-lowercase}.md` if it doesn't exist — stub with the marker
   name, status draft, row count, date ingested.
2. Update `wiki/index.md` — add the entity page if new.
3. Append to `wiki/log.md`.

## Batch processing

When multiple archives are waiting, process them in sequence. Report a summary table at the
end:

| Marker | Rows | Status | Notes |
|--------|------|--------|-------|

## Quick sanity checks (after marker consistency passes)

Run these automatically. Report results in the ingestion summary; flag failures but do not
block ingestion unless marker consistency (QC check 1) fails.

**Spot Id overlap.** Read Spot Id 1 values from the new summary CSV. Compare against the
reference set in `Data/raw/.reference/all_spot_ids.txt` (98 known Spot Ids from the TMA).
Report:
- How many of the new export's Spot Ids are in the reference set
- Any Spot Ids NOT in the reference set (unexpected cores)
- Expected: most or all Spot Ids should be in the reference set. A new export with <50%
  overlap is suspect.

**Classifier Label vocabulary.** Read the first 5000 rows of the object data CSV. Extract
unique Classifier Label values. Expected: `Tumour`, `Other`. Any additional values (e.g.
`Stroma`, `Benign`, `Necrosis`) should be flagged — they may be valid for a new classifier
but differ from all 21 existing stains.

**Row count sanity.** Summary rows should be 77–98 (77 cores are common to all existing
stains; 98 is the full TMA). Fewer than 77 is unusual. More than 98 is wrong.

## Archives with no summary CSV

Some HALO exports contain only object data (no summary). In this case:
- Identify the marker from the object data header.
- File the object data as above.
- Note the missing summary in the entity page and log.
- The summary can be regenerated from the object data in R if needed.

## Sources
- Related: [[halo-export-format]]
