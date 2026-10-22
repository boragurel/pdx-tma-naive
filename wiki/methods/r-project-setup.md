# R project setup

Status: settled
Last updated: 2026-10-12
Scope: shared
Copied from: Studies/wiki/methods/r-project-setup.md (2026-10-22)

## Structure

A single `.Rproj` file lives at the study root, named for the study
(`<Study Name>.Rproj`). Opening it sets the working directory to the project
root. All script paths are relative to this root.

```
<Study Name>/
  <Study Name>.Rproj
  CLAUDE.md
  Data/
  Scripts/
  Figures/
  Sources/
  Images/
  wiki/
```

## Workspace settings

- "Save workspace to .RData on exit": **Never**
- "Restore .RData into workspace at startup": **off**

Set these in the `.Rproj` file itself (`RestoreWorkspace: No`,
`SaveWorkspace: No`), not left as `Default`. A `.Rproj` on `Default` inherits
RStudio's global options, so the rule then holds only if the global options
happen to be set that way; check the file, not the dialog.

Every session starts clean. Scripts load what they need explicitly.

## Figures

Scripts are the reproducible artefact, not exported images. Plots render in the
RStudio plots pane and are exported manually when needed for reports or
presentations, which gives control over dimensions and aspect ratio. `Figures/`
holds the exports; each gets a `wiki/figures/` page recording script, inputs,
date and status, because the export step is manual and that page is the only
link between a figure and the code that made it.

## Rationale

One project per study keeps analysis, data and documentation together.
Disabling workspace save and restore prevents `.RData` bloat, removes hidden
dependencies on lingering objects, and forces explicit data loading.

## Sources
- Related: [[git-setup]], [[derived-data-convention]], [[data-intake-convention]]

---

## Local

- Project file: `Treatment Naive PDX TMA.Rproj` at the study root.
