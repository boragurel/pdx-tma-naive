# STEAP1

Status: draft
Last updated: 2026-10-22

Immunofluorescence marker on the [[pdx-tma]], the only IF stain in the set
(all others are brightfield IHC). Scanned on the VS200; the slide is not held
locally, see [[steap1-ingest-2026-10-22]]. Two HALO runs on the same scan:
whole-cell and membrane-only (`Data/raw/STEAP1_membrane/`). STEAP1 is a
membrane protein, so the membrane run is the biologically primary
measurement; the whole-cell run is kept for comparison.

## Data
- Whole-cell: `Data/raw/STEAP1/`, 98 / 98 cores
- Membrane: `Data/raw/STEAP1_membrane/`, 95 / 98 cores
- Classifier labels: Tumour only; summary has a `Tumour:` layer but no
  `Other:`/`Stroma:` columns and no `TMA Block Name` column. Scripts iterating
  all markers must tolerate this, as for [[periostin]].
- Not yet in [[model-summary-dataset]]; compartment assignment pending in
  [[marker-compartment-assignments]].

## Sources
- Data: `Data/raw/STEAP1/`, `Data/raw/STEAP1_membrane/`; copied from
  `E:\HALO\Studies\STEAP1\Data\` (also holds a merged
  cytoplasm/membrane CSV not brought in)
- Related: [[stain-inventory]], [[pdx-tma]], [[steap1-ingest-2026-10-22]]
