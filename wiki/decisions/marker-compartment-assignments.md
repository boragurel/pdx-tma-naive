# Marker Compartment Assignments

Status: active
Last updated: 2026-09-01

Compartment selection for each IHC marker in the [[pdx-tma]] summary dataset. Each
marker's primary compartment was chosen based on published IHC localisation data, not
HALO algorithm defaults. HALO measures nuclear OD for any DAB stain regardless of true
localisation; compartment assignment reflects where the protein actually sits and where
expression is biologically meaningful.

## Nuclear markers (14)

Primary metric: `% Positive Nuclei` + `Avg Positive Nuclei OD`

| Marker | Rationale |
|--------|-----------|
| AR NTD | Nuclear transcription factor |
| ASCL1 | Nuclear TF (bHLH, neuroendocrine lineage) |
| Ki67 | Nuclear proliferation antigen |
| MYC | Nuclear TF (oncogene) |
| p53 | Nuclear tumour suppressor (accumulates when mutant) |
| RB1 | Nuclear tumour suppressor (lost when null/mutant) |
| SOX2 | Nuclear TF (pluripotency / neuroendocrine) |
| SNAIL | Nuclear TF (EMT master regulator) |
| Lamin A/C | Nuclear lamina structural protein |
| Lamin B1 | Nuclear lamina structural protein |
| LAP1 | Inner nuclear membrane protein (TOR1AIP1) |
| BANF1 | Inner nuclear membrane / nucleoplasm (BAF) |
| RPA | Nuclear ssDNA-binding protein (replication/repair) |
| pRPA | Phospho-RPA, nuclear DNA damage response foci |

## Dual-compartment markers (5)

Both nuclear and cytoplasmic `% Positive` included as separate columns. Nuclear used as
primary for sorting/thresholding, but both compartments are biologically informative.

| Marker | Nuclear role | Cytoplasmic role |
|--------|-------------|-----------------|
| YAP1 | Active transcriptional co-activator (Hippo off) | Phosphorylated / inactive (Hippo on) |
| pERK | Translocated, acting on nuclear TFs | MAPK cascade activity |
| IRF3 | Activated (cGAS-STING-TBK1 pathway) | Baseline / inactive |
| PTEN | Genome stability functions | Canonical PI3K/AKT antagonism |
| MCL1 | Reported nuclear expression | Primary: mitochondrial, anti-apoptotic BCL2 family |

## Cytoplasmic markers (11)

Primary metric: `% Positive Cytoplasms`

| Marker | Rationale |
|--------|-----------|
| BAK | Mitochondrial outer membrane, pro-apoptotic BCL2 family |
| BIM | Mitochondria/ER membrane, pro-apoptotic BH3-only |
| Chromogranin | Neuroendocrine secretory granules |
| CK5 | Cytoplasmic intermediate filament (basal cytokeratin) |
| CK8-18 | Cytoplasmic intermediate filament (luminal cytokeratin) |
| MALT1 | Cytoplasmic paracaspase (NF-kB/CBM signalosome) |
| pMLC2 | Actomyosin contractile apparatus (Ser19 phospho) |
| PSMA | Type II transmembrane glycoprotein |
| STING | ER transmembrane / perinuclear (cGAS-STING pathway) |
| STING E9 | Same protein, different antibody clone |
| Synaptophysin | Synaptic vesicle membrane protein |

## Special cases (3)

| Marker | Primary metric | Rationale |
|--------|---------------|-----------|
| B7H3 | `% Positive Cells` | Membrane immune checkpoint; Cells captures both membrane and cytoplasmic signal |
| CD56 | `% Positive Cells` | NCAM, membrane; Cells captures both compartments |
| Periostin | `% Positive Cytoplasms` (Tumor layer) | Secreted ECM protein; HALO uses American spelling "Tumor:" not "Tumour:"; different classifier labels |

## Sources
- Data: `Data/derived/PDX_TMA_model_summary.csv`
- Related: [[stain-inventory]], [[halo-export-format]], [[model-summary-dataset]], [[marker-distributions]]
