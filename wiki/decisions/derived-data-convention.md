# Derived data convention

Status: settled
Last updated: 2026-10-12
Scope: shared
Copied from: Studies/wiki/decisions/derived-data-convention.md (2026-10-22)

Split project data by provenance: **raw** (imported, immutable exports and
manifests) and **derived** (anything a script computes). Two reasons: never
recompute an expensive analysis, and keep an audit trail from every derived
file back to the script that made it.

```
Data/
  raw/          immutable; see [[data-intake-convention]]
  derived/      script output only
  incoming/     staging for anything new before filing
```

## Rule

Nothing enters `Data/derived/` unless a script in `Scripts/` produces it and
that script is listed in [[registry]]. `Data/raw/` is immutable: never edit,
rename, move or delete anything in it. The reason this rule is strict: an
earlier project lost the script behind its central dataset, and four analyses
became unreproducible.

## Format

- **RDS by default** for R-native objects (data.tables, lists): lossless types,
  strong compression, instant reload.
- **CSV additionally** for small, portable tables meant to be opened outside R.
- **Parquet for large per-cell tables**, one file per sample, written with
  `arrow`, provenance as JSON in the file metadata; adopted in MMR (2026-09-29)
  and PathStage (2026-10-07), with DuckDB as a reader over the files. Small
  objects stay RDS. A study using Parquet records its metadata key under Local.
- The filename is a stable identity; the mutable method version lives in the
  provenance, not the name, so files never need renaming when a pipeline
  evolves.

## Provenance

Every derived file carries an embedded provenance record (RDS: an attribute,
read with `attr(readRDS(f), "provenance")`; Parquet: file metadata). The file
is then self-describing even if separated from the wiki. Fields:

- `dataset`, `description`, `pipeline` (script path), `params`, `created`
- `script_md5`: hash of the script as it ran
- `script_uncommitted`: whether the script had uncommitted changes when it ran
- `git_commit`: the commit at the time of the run (which precedes the edit if
  `script_uncommitted` is true)
- `source_raw` and `source_md5`: every immediate input, raw or derived, with
  its hash

A hash identifies a version; it does not store it. Git stores it, but only if
committed. So: **a result an `experiments/` page relies on comes from a
committed script.** If the provenance says the script was uncommitted when it
ran, commit before writing the page. The page names the derived files it used
with their `created` stamp, so a later replacement of the file under the same
name is detectable. Old derived outputs are not archived; keeping one is a
judgment call for results that would be impractical to recreate.

## Naming

`<study-prefix>_<dataset>.<ext>`, hyphenated slug after the prefix.
Descriptive, no method or version tag in the name (`mmr_cell-density.rds`,
not `cell_density_v2_final.rds`). The prefix is short and fixed per study
(`ace`, `mmr`, `psmsi`).

## Sources
- Related: [[data-intake-convention]], [[registry]]. Provenance fields as
  implemented in MMR `Scripts/mmr_unscramble.R`

---

## Local

- Study prefix: `pdxtma`.
- Parquet not in use; per-cell object data stays as the raw HALO CSVs.
- Existing derived files predate this convention and do not conform: `Data/derived/PDX_TMA_model_summary.csv` and `PDX_TMA_marker_distributions.csv` (created 2026-09-01) have no producing script in `Scripts/`, no registry entry and no provenance record. To be rebuilt by a registered script as `pdxtma_model-summary` and `pdxtma_marker-distributions` (RDS with provenance, plus CSV). Until then, treat them as provisional. See [[model-summary-dataset]], [[marker-distributions]].
