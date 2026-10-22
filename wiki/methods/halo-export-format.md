# HALO TMA Export Format

Status: settled
Last updated: 2026-08-05

Reference for the HALO TMA export structure used in this project. All stains on this TMA
use single-marker IHC analysed with HALO's Multiplex IHC algorithm.

## Archive structure

HALO exports a folder named `Halo archive YYYY-MM-DD HH-MM - vX.X.XXXX` containing:

```
Halo archive .../
  Total_Summary_Results.csv       <- one row per TMA core
  ObjectData/
    Total_Object_Results.csv      <- all cores combined, one row per cell
```

Some exports contain per-core object data CSVs instead of (or alongside) the combined file.

## Summary CSV

One row per TMA core. Key columns:

**TMA metadata:** TMA Block Name, Image Stain, Spot Valid, TMA Row, TMA Column,
Left/Top/Width/Height (pixels), Spot Id 1, Spot Id 2.

**Combined columns:** Total Cells, {Marker} Positive Cells, % {Marker} Positive Cells,
{Marker} Avg Cytoplasm OD, {Marker} Avg Nucleus OD, morphometry, Tissue Area.

**Per-layer columns:** Same block repeated with prefixes `Tumour:`, `Stroma:`, `Other:`.

The marker name is embedded in column names and varies per stain.

**Marker extraction:** The marker name appears in columns with varying prefixes: bare
(`{Marker} Positive Cells`), percentage (`% {Marker} Positive Cells`), and per-layer
(`Tumour: {Marker} Positive Cells`, `Tumour: % {Marker} Positive Cells`). Strip layer
and `%` prefixes before matching.

## Object data CSV

One row per detected cell. Key columns: Object Id, XMin/XMax/YMin/YMax (pixel coordinates
relative to TMA spot), {Marker} Positive Classification (0/1), {Marker} Cytoplasm OD,
{Marker} Nucleus OD, Cell Area, Classifier Label (Tumour/Stroma/Other).

## Spot Id format

`{model} - {passage} {block_id}_{core}` e.g. `CP50 - P18 373700_1`.
Castrated models have "c" suffix: `CP50c - P20 300893_1`.

## File naming convention

HALO's generic names are renamed on intake:
- `Total_Summary_Results.csv` -> `PDX_TMA_{MARKER}_Summary.csv`
- `Total_Object_Results.csv` -> `PDX_TMA_{MARKER}_object_data.csv`

See [[tma-halo-ingest]] for the full intake procedure.

## Sources
- Related: [[tma-halo-ingest]], [[pdx-tma]]
