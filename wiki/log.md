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

## [2026-10-22] setup | Git initialised, pushed to boragurel/pdx-tma-naive (private)
Canonical .gitignore adopted; clauder_logs/ moved to Scripts/clauder_logs/.

## [2026-10-22] create | decisions/git-setup (shared copy)

## [2026-10-22] update | CLAUDE.md rebuilt from Studies/wiki/templates/CLAUDE.md (shared half copied 2026-10-22)

## [2026-10-22] create | decisions/data-intake-convention (shared copy)
## [2026-10-22] create | decisions/derived-data-convention (shared copy)
## [2026-10-22] create | methods/r-project-setup (shared copy)
## [2026-10-22] create | methods/reading-files (shared copy)
## [2026-10-22] create | workflows/source-ingest (shared copy)
## [2026-10-22] setup | wiki/imports/ and wiki/figures/ folders created

## [2026-10-22] move | 21 TMA slide scans moved from YAP in PCa/Images/YAP-Lamin in PDX TMA/ to Images/; Periostin slide copied from Periostin study. 34 slides local
## [2026-10-22] ingest | STEAP1 IF, whole-cell and membrane runs, from E:/HALO/Studies/STEAP1/Data/ into Data/raw/STEAP1/ and STEAP1_membrane/
## [2026-10-22] create | entities/steap1, imports/steap1-ingest-2026-10-22
## [2026-10-22] update | stain-inventory (34 stains), index
## [2026-10-22] import | 5 TMA slides copied from RDS (ASS1, CBP, ERG, LC3AB, SLFN11) into Images/; 39 slides local
## [2026-10-22] create | entities/ass1, cbp, erg, lc3ab, slfn11; imports/tma-slides-2026-10-22
## [2026-10-22] update | stain-inventory (unanalysed-slides table), index current position
## [2026-10-22] import | ASCL4 and p300 TMA slides copied from RDS into Images/ (unannounced scans, Bora's decision); 41 slides local
## [2026-10-22] create | entities/ascl4, p300; update imports/tma-slides-2026-10-22, stain-inventory, index
## [2026-10-22] fix | 21 YAP-era slides copied back to YAP in PCa/Images/YAP-Lamin in PDX TMA/ (HALO references those paths); both copies kept, noted in imports/tma-slides-2026-10-22
## [2026-10-28] ingest | HALO exports ASS1, ASCL4 (summary + objects), LC3AB (objects only) into Data/raw/
## [2026-10-28] hold | HALO exports CBP, ERG, SLFN11, p300 left in Data/incoming/ (summary/object marker mismatch)
## [2026-10-28] create | imports/halo-ingest-2026-10-28; update entities ass1, ascl4, lc3ab, cbp, erg, p300, slfn11, stain-inventory, index
## [2026-10-28] verify | ASS1, ASCL4 summary vs object data reconciled per core; recorded in imports/halo-ingest-2026-10-28
## [2026-10-28] withdraw | 28 Oct HALO exports (7 markers) removed from Data/raw/ and incoming to Data/incoming/_to_delete/ for re-export one at a time
## [2026-10-28] update | imports/halo-ingest-2026-10-28 (superseded), entities ass1, ascl4, lc3ab, cbp, erg, p300, slfn11, stain-inventory, index
## [2026-10-28] clear | 12 Aug 2026 HALO archives (byte-identical to Data/raw/) moved from Data/incoming/ to _to_delete/ for deletion
## [2026-10-28] ingest | re-exports ASS1, ASCL4, CBP, LC3AB, SLFN11 into Data/raw/ (per-core reconciled)
## [2026-10-28] hold | re-exports p300, ERG in Data/incoming/ (control-core placeholder row), pending decision
## [2026-10-28] create | imports/halo-reexport-2026-10-28; update entities, stain-inventory, index
## [2026-10-28] ingest | re-exports p300, ERG into Data/raw/ (control-core placeholder row noted), Bora's decision
## [2026-10-28] update | imports/halo-reexport-2026-10-28, entities p300, erg, stain-inventory, index
## [2026-10-28] share | 7 summary CSVs (ASS1, ASCL4, CBP, ERG, LC3AB, p300, SLFN11) copied to Ines results folder on V:, noted in imports/halo-reexport-2026-10-28
## [2026-10-28] share | 7 object-data CSVs copied to Ines results folder on V: (ObjectData subfolders), noted in imports/halo-reexport-2026-10-28
## [2026-10-29] ingest | BOK, SLC7A11 into Data/raw/ (per-core reconciled)
## [2026-10-29] create | imports/halo-ingest-2026-10-29, entities bok, slc7a11; update stain-inventory, index
## [2026-10-29] share | BOK, SLC7A11 summary and object-data CSVs copied to Ines results folder on V:, noted in imports/halo-ingest-2026-10-29
