# Treatment Naive PDX TMA — Project Schema

## Project overview

Multi-marker IHC characterisation of a treatment-naive prostate cancer PDX
tissue microarray: 22 matched intact/castrated models plus 5 control tissues,
98 cores, single-marker IHC stains analysed in HALO (Multiplex IHC algorithm),
with genomic annotations alongside. 33 stains so far; Ines continues to send
new ones. "Treatment naive" means no experimental drug; castrated models stand
in for CRPC and are the standard baseline. Stage: all markers ingested,
model-level summary built; cross-marker analysis and thresholding next.
Current position and open items: `wiki/index.md`.

## Folder structure

```
Treatment Naive PDX TMA/
  CLAUDE.md
  Data/      raw/ (immutable) | derived/ (script output only) | incoming/ (staging)
             genomic/ (immutable: variant annotations, OncoKB calls)
  Scripts/   clauder_logs/ (ClaudeR session logs)
  Figures/
  Sources/   papers, documents (immutable)
  Images/    scanned TMA slides, .vsi + stack folders (immutable)
  wiki/      index.md | log.md | imports/ entities/ methods/ decisions/
             experiments/ figures/ workflows/ scripts/ sources/ meta/
```
`Data/raw/` holds one subfolder per marker: `PDX_TMA_{MARKER}_Summary.csv` and
`ObjectData/PDX_TMA_{MARKER}_Objects.csv`. `Data/raw/.reference/` holds the
98 reference Spot Ids. Study prefix for derived files: `pdxtma`.

## Study-wide constraints

- Control cores (placenta, tonsil, prostate, spleen) are excluded from all
  analyses -> `entities/pdx-tma.md`
- Periostin's HALO export uses `Tumor:` (American spelling) and classifier
  labels Stroma/Benign/Tumor, not Other/Tumour; any code iterating markers
  must handle it -> `entities/periostin.md`, `methods/halo-export-format.md`
- Only 8 of 22 models have PDX-level sequencing; the rest carry patient-biopsy
  genomics. Track provenance in any genomic analysis -> `entities/pdx-tma.md`
- Compartment per marker is fixed by biology, not HALO defaults ->
  `decisions/marker-compartment-assignments.md`
- HALO summary and object exports can come from different stain runs; marker
  consistency is checked before any ingest -> `workflows/tma-halo-ingest.md`
- Routine HALO TMA exports are ingested autonomously, without per-step
  confirmation; this is a deliberate local override of the general intake
  convention, recorded under Local in `decisions/data-intake-convention.md`

## Workflows (read when the situation arises, not at session start)

- New HALO TMA export -> `wiki/workflows/tma-halo-ingest.md`. Expected:
  further exports from Ines, one marker each, landing in `Data/incoming/`
- Paper or document to add -> `wiki/workflows/source-ingest.md`
- New data of any kind -> `wiki/decisions/data-intake-convention.md`

---

Shared from here to the end. Copied from: Studies/wiki/templates/CLAUDE.md
(2026-10-22). Do not edit below this line in place: fix the template, then
re-copy.

## Start of every session

Read `wiki/index.md`. Summarise its "Current position" in two or three lines
and wait for Bora to choose the next step. Read other pages only as the task
needs them. The wiki, not memory, is the authority on project state.

## Your role

You maintain the wiki in this folder. Read and write wiki pages as part of
normal work. Update the wiki as findings emerge, not as a separate task at the
end.

## Self-contained folder

This folder does not depend on anything outside it: a collaborator given a
copy, or a session with no access to the rest of the drive, has everything
needed to work. Facts from another study are copied in, with a `Copied from:`
line, not fetched live. A live link to another study's page is allowed only
where a copy would go stale (a cohort list still being assembled, say); the
page says so, and the link is never the only record. If something is missing,
say so; do not go and fetch it. The one exception is the top-level wiki
(`Studies/wiki/`), which a session may read and write for the shared-page jobs
below when it is reachable.

## Data layer rules

Nothing enters `Data/derived/` unless a script in `Scripts/` produces it and
that script is listed in `wiki/scripts/registry.md`. `Data/raw/`, `Images/` and
`Sources/` are immutable: never edit, rename, move or delete anything in them.
`Data/incoming/` is staging: new material lands there for inspection before
being filed (see `decisions/data-intake-convention.md`).

## Wiki maintenance

- Method or parameter settled -> `methods/`
- Something learned about a cohort, sample, marker, dataset or tool ->
  `entities/` or `imports/`
- Analysis or run completed -> `experiments/`: what was done, found, produced,
  naming the derived files used with their provenance `created` stamp
- Choice made (threshold, exclusion, compartment rule) -> `decisions/` with
  rationale; not yet made -> `Status: open` with the options recorded
- Script created or modified -> `wiki/scripts/registry.md`
- Figure produced -> `figures/` page recording script, inputs, date, status.
  Figures are saved from the plot pane, so this page is the only link between a
  figure and the code that made it.
- New export ingested -> `imports/` page via the platform's ingest workflow in
  `wiki/workflows/`
- Paper or document ingested -> `sources/`, one page per source,
  `first-author-year`
- An explanation in chat worth keeping -> file it as a page

If a page doesn't exist, create it; if it does, update it in place. Check
`index.md` first.

At the end of each working session, propose a commit message summarising
changes to `wiki/` and `Scripts/` (see `decisions/git-setup.md`); Bora runs it.
Never commit.

Pages are Markdown with `[[wikilinks]]` on first mention of anything that has
its own page. Concise, current-state, not session history. Prefer tables and
lists over prose. If something changed, say what it is now and note what it was
before in one line.

### Shared pages

Pages marked `Scope: shared` are copies of canonical pages in the top-level
wiki (`Studies/wiki/`), with `Copied from: <path> (<date>)` under
`Last updated`. Do not improve a copy in place: if it is wrong or incomplete,
say so, fix the canonical page, then re-copy (procedure:
`Studies/wiki/workflows/copy-shared-page.md`). If the canonical page cannot be
reached, record the correction under the copy's `## Local` heading, marked
"pending canonical fix", and carry on. Study-specific additions go under
`## Local` and survive re-copying; within this study, `## Local` wins over the
shared text above it. A page that looks general enough to share is marked
`Scope: shared-candidate` for the next top-level review. Pages copied from
another study rather than the top-level wiki carry `Copied from:` only and may
be adapted freely.

### Page format

```markdown
# Page Title

Status: draft | active | settled | superseded | open
Last updated: YYYY-MM-DD          (then optional Scope: / Copied from: lines)

[content]

## Sources
- Scripts: [paths]
- Data: [paths]
- Related: [[wikilinks]]
```

draft = preliminary; active = in use, may change; settled = decided, change
only with a recorded reason; superseded = replaced, link to replacement;
open = decision not yet made, options recorded.
Scope: shared = copy of a canonical page; shared-candidate = proposed for
sharing; absent = this study's own page.

After any page change update `index.md`; after any wiki operation append one
line to `log.md` in the form `## [YYYY-MM-DD] <operation> | <subject>` — no
other format.

### Reading the wiki

On any query about this project read `wiki/index.md` first, then only the
relevant pages. Name the pages you used. If the answer isn't in the wiki, say
so; don't fabricate.

### Anti-patterns

- No session diary. Wiki pages are the memory.
- No project state in CLAUDE.md. Keep this file under 150 lines.
- No deferred wiki updates. No scripts that exist only in chat. No free-form
  `log.md` entries.
- No re-teaching what the wiki already knows. Read the page first.
- No improving a shared copy in place.

### Lint

Pages in `index.md` that don't exist; pages not in `index.md`; dead
`[[wikilinks]]`; `draft` pages older than two weeks; `decisions/` without
rationale; `Data/derived/` files with no registered script; `Figures/` without
a `figures/` page; `log.md` lines not matching the entry format; a constant
appearing in more than one script with different values; shared copies whose
canonical page is newer (checked when the top-level wiki is reachable).

## Working rules

- Skills: r-style for any R written; r-session for the RStudio console and
  file access on this machine; prose-for-publication for any text leaving the
  chat. Load them when the occasion arises; they are not repeated here. They
  are personal to Bora's setup; the folder works without them.
- Name the content, never the code. When a row ID, label or filename is
  mentioned, say what it is in words.
- Teaching pace: Bora is learning shell, Python tooling and HPC. Teach those one
  step at a time with short examples and wait for him to try each.
- Narrate tool work: say what is about to happen and roughly how long; a line
  every few calls; never go silent for minutes. Stop before writing files
  outside `wiki/`, starting runs longer than a few minutes, or choosing between
  approaches.
- Undiscussed methods: never add methods, filters, thresholds or corrections
  that have not been discussed. If one is unavoidable, state it first.
- Conciseness: short responses; no restating what has been agreed.
