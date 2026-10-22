# Log

Append-only. One line per operation, newest at the bottom.

## [2026-08-05] setup | Project created at E:\HALO\Studies\Treatment Naive PDX TMA
Separated from YAP in PCa. Folder tree created: Data/{raw,derived,incoming,genomic},
Scripts, Figures, Sources, wiki/8 page types. Images/ pre-existed with 12 TMA slide scans.

## [2026-08-05] setup | CLAUDE.md written
Schema, data layer rules, wiki maintenance rules, R Studio workflow rules. 152 lines.

## [2026-08-05] setup | Wiki seed pages written
Created: wiki/index.md, wiki/log.md, entities/pdx-tma.md, entities/stain-inventory.md,
methods/halo-export-format.md, scripts/registry.md, workflows/tma-halo-ingest.md.

## [2026-08-05] ingest | 21 marker datasets migrated from YAP in PCa
Copied from E:\HALO\Studies\YAP in PCa\Data\YAP-Lamin in PDX TMA\. Per-marker folders
with renamed summary CSVs and ObjectData subfolders. Source left intact.

## [2026-08-05] ingest | Genomic data copied
11 files from Genomic data/ to Data/genomic/. Includes variant annotations, OncoKB calls.

## [2026-08-05] ingest | 8 new markers from today's HALO archives
AR NTD, ASCL1, CK5, CK8-18, Ki67, p53, SOX2, Synaptophysin. Identified from column headers,
renamed per convention, filed into Data/raw/. AR NTD required summary from second archive.
YAP1 archive (2026-04-07) skipped — already in raw/ from named folder migration.

## [2026-08-05] update | stain-inventory.md populated
29 markers with summary and object data. All rows, paths, dates recorded.

## [2026-08-05] delete | 8 ingested markers removed — HALO export mismatch
AR NTD, ASCL1, CK5, CK8-18, Ki67, p53, SOX2, Synaptophysin deleted from Data/raw/ and
from Ines's network folder. Three archives had summary/object data from different stains
(p53/Chromogranin, CK8-18/CD56, AR NTD/RB1). All 11 new markers to be re-exported from
HALO. Stain inventory reverted to 21 markers.

## [2026-08-05] fix | tma-halo-ingest.md updated
Fixed object data naming convention to _Objects.csv (not _object_data.csv), matching the 21
existing folders. Added marker consistency check as QC step 1: extract marker from both
summary and object data headers, stop if they disagree.

## [2026-08-05] update | Sanity checks added to tma-halo-ingest.md
Three quick checks: Spot Id overlap against reference set (77 common, 98 total),
Classifier Label vocabulary (expect Tumour + Other only), row count range (77-98).
Reference Spot Id files saved to Data/raw/.reference/.

- 2026-08-05: Ingested 11 re-exported HALO markers (AR NTD, ASCL1, CD56, Chromogranin, CK5, CK8-18, Ki67, p53, RB1, SOX2, Synaptophysin). All QC passed. Duplicate AR NTD archive (10-23) skipped — byte-identical to 10-20. Created 11 entity stubs. Updated stain-inventory (now 32 markers) and index. Incoming archives still in Data/incoming/ pending cleanup.
- 2026-08-05: Added marker extraction note to halo-export-format.md (prefix stripping for column parsing).
- 2026-08-05: Copied Periostin data from Periostin project into Data/raw/Periostin/. 98 rows, full Spot Id overlap. Created entity page. Stain inventory now 33 markers.

- 2026-09-01: Created `Data/derived/PDX_TMA_model_summary.csv` — 44 model-states, 96 IHC + 17 genomic columns
- 2026-09-01: Created `Data/derived/PDX_TMA_marker_distributions.csv` — distribution stats for 33 markers
- 2026-09-01: Created `decisions/marker-compartment-assignments.md` — compartment selection per marker
- 2026-09-01: Created `entities/model-summary-dataset.md` — summary dataset documentation
- 2026-09-01: Created `entities/marker-distributions.md` — distribution characterisation and thresholding guidance
- 2026-09-01: Updated `index.md` — added new entities, decisions, updated current position
