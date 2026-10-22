# Data intake convention

Status: settled
Last updated: 2026-10-12
Scope: shared
Copied from: Studies/wiki/decisions/data-intake-convention.md (2026-10-22)

All new data entering the project is first placed in `Data/incoming/`. Inspect
column headers, row structure and filenames there before anything moves to its
final location under `Data/raw/`.

## Rationale

- See the raw export format before committing to folder structure or naming.
- Catch unexpected column changes, encoding issues or naming mismatches early.
- Keep `Data/raw/` clean of unvetted files.

## Workflow

1. File lands in `Data/incoming/`. Nothing goes straight into `Data/raw/`.
2. Inspect contents; identify the platform. If a format page already exists
   for that platform's export (a HALO or Visiopharm export-format page), the
   column structure is known and need not be re-derived. Platform-specific
   checks are in the platform's ingest workflow ([[visiopharm-export-ingest]]).
3. Ask Bora for anything that cannot be inferred: cohort identity, experimental
   context, which samples belong to which condition.
4. Agree naming, structure and destination. Discuss before writing pages or
   moving files.
5. Move files to `Data/raw/<subfolder>/`.
6. Verify the copy by sampled content hash, not size alone.
7. Write the corresponding `imports/` page: what arrived, from where, when,
   what it contains, and anything the inspection turned up.
8. Update [[index]]; append one line to `log.md`. Clear `Data/incoming/` once
   confirmed.

## Sources
- Related: [[derived-data-convention]], [[source-ingest]],
  [[visiopharm-export-ingest]]

---

## Local

- Platform: HALO single-marker IHC TMA exports. Format page: [[halo-export-format]]; ingest workflow: [[tma-halo-ingest]], which identifies the marker from column headers, runs QC and files to `Data/raw/{MARKER}/`.
- Override of step 4 ("discuss before moving files"): routine HALO TMA exports are ingested autonomously, end to end, without per-step confirmation. Arrivals from Ines are frequent and the marker-consistency, Spot Id, classifier-label and row-count checks in the workflow are the gate. Anything failing QC stops and is reported. Decided 2026-10-22.
- Expected arrivals: further single-marker exports from Ines, one `Halo archive ...` folder each, landing in `Data/incoming/`.
- Pending: `imports/` pages for the 33 markers already in `Data/raw/` (ingested Aug 2026, before this convention); STEAP1 and pFAK exports held in `E:\HALO\Studies\STEAP1\Data\` and `E:\HALO\Studies\pFAK\Data\` not yet brought in.
