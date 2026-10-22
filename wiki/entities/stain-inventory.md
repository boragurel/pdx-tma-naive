# Stain Inventory

Status: active
Last updated: 2026-10-22

Master list of all IHC markers analysed on the [[pdx-tma]]. Updated by the
[[tma-halo-ingest]] workflow as new exports are processed.

## Ingested markers (34 stains, 35 datasets)

| Marker | Data path | Rows | Ingested | Notes |
|--------|-----------|------|----------|-------|
| AR NTD | `Data/raw/AR NTD/` | 98 | 2026-08-05 | Re-exported, clean |
| ASCL1 | `Data/raw/ASCL1/` | 98 | 2026-08-05 | Re-exported, clean |
| B7H3 | `Data/raw/B7H3/` | 96 | 2026-08-05 | |
| BAK | `Data/raw/BAK/` | 93 | 2026-08-05 | |
| BANF1 | `Data/raw/BANF1/` | 95 | 2026-08-05 | |
| BIM | `Data/raw/BIM/` | 98 | 2026-08-05 | |
| CD56 | `Data/raw/CD56/` | 93 | 2026-08-05 | Re-exported, clean |
| Chromogranin | `Data/raw/Chromogranin/` | 97 | 2026-08-05 | Re-exported, clean |
| CK5 | `Data/raw/CK5/` | 95 | 2026-08-05 | Re-exported, clean |
| CK8-18 | `Data/raw/CK8-18/` | 95 | 2026-08-05 | Re-exported, clean |
| IRF3 | `Data/raw/IRF3/` | 96 | 2026-08-05 | |
| Ki67 | `Data/raw/Ki67/` | 97 | 2026-08-05 | Re-exported, clean |
| Lamin_AC | `Data/raw/Lamin_AC/` | 91 | 2026-08-05 | |
| Lamin_B1 | `Data/raw/Lamin_B1/` | 92 | 2026-08-05 | |
| LAP1 | `Data/raw/LAP1/` | 89 | 2026-08-05 | |
| MALT1 | `Data/raw/MALT1/` | 92 | 2026-08-05 | |
| MCL1 | `Data/raw/MCL1/` | 91 | 2026-08-05 | |
| MYC | `Data/raw/MYC/` | 94 | 2026-08-05 | |
| p53 | `Data/raw/p53/` | 98 | 2026-08-05 | Re-exported, clean |
| pERK | `Data/raw/pERK/` | 93 | 2026-08-05 | |
| Periostin | `Data/raw/Periostin/` | 98 | 2026-08-05 | Copied from Periostin project |
| pMLC2 | `Data/raw/pMLC2/` | 93 | 2026-08-05 | |
| pRPA | `Data/raw/pRPA/` | 96 | 2026-08-05 | |
| PSMA | `Data/raw/PSMA/` | 96 | 2026-08-05 | |
| PTEN | `Data/raw/PTEN/` | 96 | 2026-08-05 | |
| RB1 | `Data/raw/RB1/` | 98 | 2026-08-05 | Re-exported, clean |
| RPA | `Data/raw/RPA/` | 96 | 2026-08-05 | |
| SNAIL | `Data/raw/SNAIL/` | 93 | 2026-08-05 | |
| SOX2 | `Data/raw/SOX2/` | 95 | 2026-08-05 | Re-exported, clean |
| STEAP1 | `Data/raw/STEAP1/` | 98 | 2026-10-22 | IF, whole-cell run; see [[steap1]] |
| STEAP1 (membrane) | `Data/raw/STEAP1_membrane/` | 95 | 2026-10-22 | IF, membrane run of the same scan |
| STING | `Data/raw/STING/` | 91 | 2026-08-05 | |
| STING_E9 | `Data/raw/STING_E9/` | 93 | 2026-08-05 | |
| Synaptophysin | `Data/raw/Synaptophysin/` | 97 | 2026-08-05 | Re-exported, clean |
| YAP1 | `Data/raw/YAP1/` | 93 | 2026-08-05 | |

Row count is from the summary CSV (one row per TMA core; TMA has 98 cores total). Fewer
than 98 means some cores were excluded or failed QC in HALO.

## Sources
- Related: [[pdx-tma]], [[tma-halo-ingest]], [[halo-export-format]]
