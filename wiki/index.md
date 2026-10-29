# Wiki Index

Catalogue of all wiki pages in this project. Read this first on any query.

## Current position

34 markers (33 IHC + STEAP1 IF, two runs) ingested into Data/raw/ by 22 Oct and summarised into a single model-level dataset
(`Data/derived/PDX_TMA_model_summary.csv`): 44 rows (22 models x 2 states), 96 IHC
measurements + 17 genomic columns. Marker compartment assignments and distribution
characterisation complete. Ready for cross-marker analysis and thresholding.

ASS1, ASCL4, CBP, ERG, LC3A/B, p300 and SLFN11 re-exported and ingested 28 Oct (per-core
reconciled; see [[halo-reexport-2026-10-28]]); BOK and SLC7A11 (new) ingested 29 Oct, per-core reconciled
([[halo-ingest-2026-10-29]]); none of these nine yet in the summary dataset. All nine shared with Ines on V:. ASS1 is the most urgent
(results requested 15–16 Oct). pFAK export not filed. STEAP1 IF scans remain on RDS awaiting
confirmation from Ines of which file is final. Derived files from 1 Sep have no producing script and
must be rebuilt (see [[derived-data-convention]] Local).

## Entities

| Page | Summary |
|------|---------|
| [[pdx-tma]] | entities/pdx-tma.md — 22 matched intact/castrated models, 5 controls, 98 cores, TMA structure, genomic data, cross-project periostin reference |
| [[stain-inventory]] | entities/stain-inventory.md — Master list of all markers on the TMA (43 ingested), ingestion status, row counts |
| [[ar-ntd]] | entities/ar-ntd.md — AR NTD IHC marker |
| [[ascl1]] | entities/ascl1.md — ASCL1 IHC marker |
| [[cd56]] | entities/cd56.md — CD56 IHC marker |
| [[chromogranin]] | entities/chromogranin.md — Chromogranin IHC marker |
| [[ck5]] | entities/ck5.md — CK5 IHC marker |
| [[ck8-18]] | entities/ck8-18.md — CK8-18 IHC marker |
| [[ki67]] | entities/ki67.md — Ki67 IHC marker |
| [[p53]] | entities/p53.md — p53 IHC marker |
| [[periostin]] | entities/periostin.md — Periostin IHC marker (copied from Periostin project) |
| [[rb1]] | entities/rb1.md — RB1 IHC marker |
| [[sox2]] | entities/sox2.md — SOX2 IHC marker |
| [[synaptophysin]] | entities/synaptophysin.md — Synaptophysin IHC marker |
| [[steap1]] | entities/steap1.md — STEAP1 IF marker, whole-cell and membrane runs; slide on RDS only |
| [[ass1]] | entities/ass1.md — ASS1 IHC, ingested 28 Oct (98 cores); results requested Oct 2026 |
| [[cbp]] | entities/cbp.md — CBP IHC, ingested 28 Oct (98 cores) |
| [[erg]] | entities/erg.md — ERG IHC, ingested 28 Oct (98 cores) |
| [[lc3ab]] | entities/lc3ab.md — LC3A/B IHC, ingested 28 Oct (98 cores) |
| [[slfn11]] | entities/slfn11.md — SLFN11 IHC, ingested 28 Oct (98 cores) |
| [[ascl4]] | entities/ascl4.md — ASCL4 IHC (unannounced slide), ingested 28 Oct (98 cores) |
| [[p300]] | entities/p300.md — p300 IHC (unannounced slide), ingested 28 Oct (98 cores) |
| [[bok]] | entities/bok.md — BOK IHC, ingested 29 Oct (98 cores) |
| [[slc7a11]] | entities/slc7a11.md — SLC7A11 (xCT) IHC, ingested 29 Oct (98 cores) |
| [[model-summary-dataset]] | entities/model-summary-dataset.md — Pre-computed summary dataset: 44 model-states, all IHC + genomic columns |
| [[marker-distributions]] | entities/marker-distributions.md — Distribution shape analysis per marker (bimodality, skewness, thresholding guidance) |

## Methods

| Page | Summary |
|------|---------|
| [[halo-export-format]] | methods/halo-export-format.md — HALO TMA export structure: summary CSV, object data, Spot Id format, file naming convention |
| [[r-project-setup]] | methods/r-project-setup.md — One .Rproj per study, workspace never saved (shared copy) |
| [[reading-files]] | methods/reading-files.md — Python tool file-reading mechanics (shared copy) |

## Workflows

| Page | Summary |
|------|---------|
| [[tma-halo-ingest]] | workflows/tma-halo-ingest.md — Autonomous procedure for ingesting a new HALO TMA export: marker identification, QC, renaming, filing, wiki updates. Batch-capable |
| [[source-ingest]] | workflows/source-ingest.md — Procedure for adding a paper or document (shared copy) |

## Imports

| Page | Summary |
|------|---------|
| [[steap1-ingest-2026-10-22]] | imports/steap1-ingest-2026-10-22.md — Two STEAP1 IF exports copied from the STEAP1 study folder, QC, hashes, slide location |
| [[tma-slides-2026-10-22]] | imports/tma-slides-2026-10-22.md — Seven TMA slides (ASS1, CBP, ERG, LC3A/B, SLFN11, ASCL4, p300) copied from RDS; STEAP1 IF still on RDS; pFAK gap |
| [[halo-ingest-2026-10-28]] | imports/halo-ingest-2026-10-28.md — Seven HALO exports withdrawn for one-at-a-time re-export (superseded) |
| [[halo-reexport-2026-10-28]] | imports/halo-reexport-2026-10-28.md — Re-exports of seven markers, all filed |
| [[halo-ingest-2026-10-29]] | imports/halo-ingest-2026-10-29.md — BOK and SLC7A11 exports, QC, full MD5, shared with Ines |

The 33 markers ingested in Aug 2026 predate this page type; see [[stain-inventory]].

## Figures

*None yet.*

## Experiments

*None yet.*

## Decisions

| Page | Summary |
|------|---------|
| [[marker-compartment-assignments]] | decisions/marker-compartment-assignments.md — Biologically motivated compartment selection per marker for summary dataset |
| [[git-setup]] | decisions/git-setup.md — Git repository conventions (shared copy); Local: repo path, remote, first commit |
| [[data-intake-convention]] | decisions/data-intake-convention.md — Intake via Data/incoming (shared copy); Local: autonomous HALO ingest override, expected arrivals, pending imports pages |
| [[derived-data-convention]] | decisions/derived-data-convention.md — Derived data rules and provenance (shared copy); Local: prefix pdxtma, non-conforming legacy files |

## Scripts

| Page | Summary |
|------|---------|
| [[registry]] | scripts/registry.md — Master list of R scripts (empty) |

## Sources

*None yet.*
