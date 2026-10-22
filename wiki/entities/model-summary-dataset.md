# Model Summary Dataset

Status: active
Last updated: 2026-09-01

Pre-computed summary of all IHC and genomic data for the [[pdx-tma]], one row per
model-state (44 rows: 22 parent models x intact/castrated). Controls excluded.

## Location

`Data/derived/PDX_TMA_model_summary.csv` — 44 rows, 149 columns.

## Structure

**Identity columns:** `model` (e.g. CP253c), `parent` (CP253), `state` (Intact/Castrated).

**IHC columns per marker** (33 markers, variable columns per marker):
- `{Marker}_pct_nuc` — mean tumour % positive nuclei (nuclear/dual markers)
- `{Marker}_pct_cyto` — mean tumour % positive cytoplasms (cytoplasmic/dual markers)
- `{Marker}_pct_cells` — mean tumour % positive cells (all markers)
- `{Marker}_pct_mem` — mean tumour % positive membranes (B7H3, CD56 only)
- `{Marker}_od_nuc` — mean tumour avg positive nuclei OD (where available, ~22 markers)
- `{Marker}_n_cores` — number of TMA cores averaged (1 or 2)

Not all columns exist for all markers. See [[marker-compartment-assignments]] for which
compartment is primary for each marker.

**Genomic columns** (prefixed `g_`): `g_BRCA2`, `g_BRCA1`, `g_PALB2`, `g_ATM`, `g_CDK12`,
`g_TP53`, `g_PTEN`, `g_RB1`, `g_AR_amp`, `g_AR_mut`, `g_MMR`, `g_MYC_amp`,
`g_HRR_patient`, `g_no_mutation`, `g_pdx_sequenced`, `g_HRR_pdx`, `g_genomic_subtype`.

Genomic data joins on parent model (same for intact and castrated).

## Aggregation method

Each IHC value is the arithmetic mean across duplicate TMA cores for that model-state.
Source data is the tumour layer of each marker's HALO summary CSV in `Data/raw/`.

## Sources
- Script: built interactively on 2026-09-01 (see [[registry]] for future scripted version)
- Data: `Data/raw/` (33 marker folders), `Data/genomic/PDX_genomics_clean.csv`
- Related: [[marker-compartment-assignments]], [[marker-distributions]], [[stain-inventory]]
