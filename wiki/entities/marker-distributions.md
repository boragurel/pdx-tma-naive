# Marker Distribution Characterisation

Status: active
Last updated: 2026-09-01

Distribution shape analysis for each IHC marker across the 44 model-states in the
[[pdx-tma]]. Used to guide thresholding strategy per marker.

## Location

`Data/derived/PDX_TMA_marker_distributions.csv`

## Method

For each marker's primary compartment metric (see [[marker-compartment-assignments]]):
mean, median, SD, skewness, excess kurtosis, and bimodality coefficient (BC). BC uses
Sarle's formula: (skew^2 + 1) / (kurtosis_excess + correction). BC > 0.555 suggests
bimodality.

## Distribution shapes

### Bimodal / switch-like (BC > 0.8)

Strong on/off behaviour. Threshold sits in the valley between modes.

CK5 (BC 0.95), CD56 (0.95), ASCL1 (0.93), SOX2 (0.91), Synaptophysin (0.91),
SNAIL (0.90), PTEN (0.87), STING (0.85), pERK (0.84), STING_E9 (0.84),
PSMA (0.84), BAK (0.81), pRPA (0.80).

Neuroendocrine markers (ASCL1, SOX2, Synaptophysin, CD56) cluster here as expected.
PTEN shows clear bimodality consistent with loss-of-function in a subset of models.

### Moderately bimodal (BC 0.55 -- 0.8)

Some bimodal tendency but less clean separation.

BANF1 (0.77), AR NTD (0.76), p53 (0.73), YAP1 (0.71), MALT1 (0.70), B7H3 (0.69),
RPA (0.68), Periostin (0.68), CK8-18 (0.68), Lamin_B1 (0.67), BIM (0.67),
LAP1 (0.62), RB1 (0.60), MCL1 (0.56), Lamin_AC (0.55).

p53 bimodality is expected (TP53 mutant vs wild-type). AR NTD bimodality likely reflects
CRPC/lineage heterogeneity.

### Continuous / spread (BC < 0.55)

No clear bimodal split. Median or tertile thresholds are the pragmatic options.

IRF3 (0.53), pMLC2 (0.43), MYC (0.42), Ki67 (0.38).

### Near-floor markers

Chromogranin (mean 0.9%, SD 2.6) — near-zero across almost all models.
Lamin_B1 (mean 99.1%, SD 1.1) — near-ceiling, essentially ubiquitous.

## Thresholding implications

- **Bimodal markers**: use the valley or a fixed low cutoff (e.g. 5--10%) to separate
  positive from negative populations. The data often defines the threshold.
- **Continuous markers**: median split or tertiles for exploratory dichotomisation;
  document as arbitrary.
- **Floor/ceiling markers**: binary present/absent may be more appropriate than
  continuous scoring.

## Sources
- Data: `Data/derived/PDX_TMA_marker_distributions.csv`, [[model-summary-dataset]]
- Related: [[marker-compartment-assignments]], [[stain-inventory]]
