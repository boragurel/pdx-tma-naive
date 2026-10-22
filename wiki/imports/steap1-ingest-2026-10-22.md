# Import: STEAP1 IF exports

Status: settled
Last updated: 2026-10-22

Two HALO exports of the STEAP1 immunofluorescence stain on the [[pdx-tma]],
found in `E:\HALO\Studies\STEAP1\Data\` (never ingested; predates this
study). Copied, not moved; the source folder is untouched.

## Files

| Run | Source | Filed as | Rows | MD5 (summary / objects) |
|---|---|---|---|---|
| whole-cell | `STEAP1_Naive_PDX_TMA_{Summary,Object}_Results.csv` | `Data/raw/STEAP1/` | 98 | `27b55b04…` / `485c415b…` |
| membrane | `STEAP1_membrane_Naive_PDX_TMA_{Summary,Object}_Results.csv` | `Data/raw/STEAP1_membrane/` | 95 | `04829f8c…` / `7f1dab37…` |

Full hashes: summary `27b55b04f39f98a30ccbd443ba72add5`, objects
`485c415bcf110d84dfbcd197a8c7e056`; membrane summary
`04829f8ceff0ef792c90f306d4a9e092`, objects `7f1dab37cf7dbf0a19296bd7f6ab7ee1`.
Not copied: `STEAP1_PDX_TMA_Cytoplasm_Membrane_Merged.csv` (a derived merge,
not a raw export).

## QC ([[tma-halo-ingest]])

- Marker consistency: STEAP1 in both summary and object headers, both runs. Pass.
- Spot Id overlap: 98/98 and 95/95 in the reference set, none unexpected.
- Classifier labels (first 5000 object rows): Tumour only.
- Column structure: `Spot Id 1`, `Spot Valid`, `TMA Row`, `TMA Column` present;
  `TMA Block Name` absent; only a `Tumour:` layer. Recorded, not blocking.

## Slide

Not local. `Image Location` in the export points to RDS:
`\\rds.icr.ac.uk\data\DCS\UDDU\MEDBONO\TIER2\Histopathology\VS200\Ines\STEAP1\IF\IF steap2\18_04_Image.vsi`.
No copy has been made into `Images/`.

## Sources
- Related: [[steap1]], [[stain-inventory]], [[data-intake-convention]]
