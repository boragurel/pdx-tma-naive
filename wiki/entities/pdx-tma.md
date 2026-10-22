# PDX TMA — Treatment Naive

Status: active
Last updated: 2026-08-05

Treatment-naive PDX tissue microarray. "Treatment naive" means no experimental drug
treatment; castrated models recapitulate CRPC and are included as the standard baseline.

## TMA structure

22 matched PDX models, each as intact and castrated (suffix "c"), 2 cores per condition.
Plus 5 control tissues (2 cores each). 98 cores total.

**Models (22):** CP50, CP89, CP129, CP142, CP190, CP229, CP253, CP261, CP267, CP284,
CP286, CP291, CP312, CP320, CP324, CP327, CP336, CP341, CP354, CP365, CP429, CP430

**Controls:** Human placenta, human prostate, human tonsil, mouse prostate, mouse spleen

## Stain inventory

See [[stain-inventory]] for the full list of markers analysed on this TMA, their ingestion
status, and row counts.

## Genomic data

Variant annotations for the PDX models are in `Data/genomic/`. Includes OncoKB-annotated
variants and a cleaned genomic summary per model.

## Cross-project references

The same TMA was stained with periostin and analysed in the Periostin project:
`E:\HALO\Studies\Periostin\Data\pdx-tma-periostin-ihc\`
See that project's [[pdx-tma]] and [[pdx-od-threshold-calibration]] pages for periostin-
specific methods and findings.

## Images

TMA slide scans (.vsi) are in `Images/`. Not all stains have scans stored locally.

## Sources
- Data: `Data/raw/` (per-marker), `Data/genomic/`
- Related: [[stain-inventory]], [[halo-export-format]], [[tma-halo-ingest]]
