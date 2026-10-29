# Import: seven TMA slide scans from RDS

Status: settled
Last updated: 2026-10-22

Five slides Ines announced by email between 8 Sep and 21 Oct 2026, plus two
(ASCL4, p300) found on RDS unannounced, none previously copied into the study. Copied, not moved; RDS originals untouched. Copies
verified by total byte count of .vsi + stack folder.

Source root: `\\rds.icr.ac.uk\DATA\DCS\UDDU\MEDBONO\TIER2\Histopathology\VS200\Treatment Naive PDX_H&E_IHC\`

| Marker | Source subfolder | Local file | Size | Announced |
|---|---|---|---|---|
| ASS1 | `ASS1` | `Images/All matched PDXs TMA ASS1.vsi` | 1.04 GB | 16 Oct (no path given) |
| CBP | `CBP` | `Images/All matched PDXs TMA CBP.vsi` | 1.25 GB | 26 Sep |
| ERG | `ERG` | `Images/All matched PDXs TMA ERG.vsi` | 0.99 GB | 21 Oct |
| LC3A/B | `LC3AB` | `Images/All matched PDXs TMA LC3AB.vsi` | 1.00 GB | 8 Sep |
| SLFN11 | `SLFN11` | `Images/All matched PDXs TMA SLFN11.vsi` | 1.01 GB | 6 Oct |
| ASCL4 | `ASCL4` | `Images/All matched PDXs TMA ASCL4.vsi` | 1.02 GB | never (scanned 1 Oct); copied on Bora's decision |
| p300 | `p300` | `Images/All matched PDXs TMA p300.vsi` | 1.15 GB | never (scanned 27 Sep); copied on Bora's decision |

## Seen on RDS but not copied (pending confirmation from Ines)

- `ASCL4\All matched PDXs TMA ASCL4.vsi` (dated 2026-10-01), never announced
- `p300\All matched PDXs TMA p300.vsi` (dated 2026-09-27), never announced
- `STEAP1\All matched PDXs TMA STEAP1 1-50_ER2 20'_Opal 570.vsi` (2026-03-06); Opal 520 and 650
  versions and the raw `18_04_Image.vsi` in `Ines\STEAP1\IF\IF steap2`. The HALO export in
  `Data/raw/STEAP1/` references `18_04_Image.vsi`. Which file is canonical is unconfirmed.
- `Ines\TMAs_IF\TMA_all matched models Feb 26.vsi` (2026-02-16), unknown IF run

## Duplicate slide locations (deliberate)

The 21 slides analysed in the YAP era exist in two places: here in `Images/` and in
`E:\HALO\Studies\YAP in PCa\Images\YAP-Lamin in PDX TMA\`. They were moved here on
2026-10-22 and HALO lost its image paths, so they were copied back the same day. HALO
references the YAP location; this study's copy is for self-containment. Neither copy may be
deleted. Any new analysis of these slides should be set up from the YAP path to keep HALO on
one image record per slide. The 7 slides copied from RDS today have only the local copy.

## Slides already local, no HALO data

- pFAK: analysed 19 Aug 2026 and results sent to Ines; HALO export never filed in this study.

## Sources
- Related: [[stain-inventory]], [[data-intake-convention]]
