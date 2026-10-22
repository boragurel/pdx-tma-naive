# Skill Preparation Notes

Running log of generic vs project-specific choices made while building this wiki.
Written contemporaneously during the setup session for use by a future skill-creation session.

## Observations

- [generic] Folder tree: Data/{raw,derived,incoming,genomic}, Scripts, Figures, Sources, wiki/{entities,methods,experiments,decisions,scripts,sources,workflows}, clauder_logs. Identical to Periostin except: added Data/genomic (project-specific — variant annotations exist), no Images/ creation (already existed). B-cell uses Data/raw only (no derived yet) and Sources/inherited-notes + inherited-derived (project-specific migration layer).
- [generic] wiki/meta/ added for this file — not in Periostin or B-cell. Could become standard for skill-prep or other meta content.
- [parameterise] Project name used in: folder path, CLAUDE.md title, .Rproj filename, git remote name. All derivable from one input.
- [generic] CLAUDE.md structure: project overview, folder structure, data layer rules, wiki maintenance (when/how/format/reading/anti-patterns/lint), workflows section, file reading note, R Studio workflow rules. Identical section ordering across all three projects.
- [generic] Anti-patterns list: identical across all three projects, verbatim.
- [generic] R Studio workflow rules: identical across all three projects, verbatim. Could be a shared reference file rather than repeated.
- [generic] Page format (status/date/content/sources): identical, verbatim.
- [generic] Wiki maintenance triggers (method->methods/, finding->entities/, etc.): identical pattern, verbatim.
- [parameterise] Project overview paragraph: unique per project. User provides study description.
- [parameterise] Folder structure diagram: mostly identical; Data/ subfolders vary (genomic/ is project-specific here; Periostin has no genomic/; B-cell has no derived/ yet).
- [parameterise] Data layer rules: the "nothing enters derived without a script" rule is generic. The immutability rule for raw/ is generic. The specific folders (genomic/, incoming/) are parameterised.
- [parameterise] Workflows section: pointer lines to workflow pages are project-specific. The pattern of "read the page before acting" is generic.
- [changed] CLAUDE.md line limit: Periostin uses 100, B-cell uses 200, this project uses 150. Should settle on one value for the skill.
- [omitted] B-cell has "figures are copied from the plot pane" rationale — included because the figures/ page type needed motivation. Generic concern but not all projects need it in CLAUDE.md.
- [omitted] B-cell has "Data/derived script-output-only" with backstory about the lost density script. The rule is generic; the backstory is project-specific.
- [generic] index.md structure: Current position paragraph, then tables by category (Entities, Methods, Workflows, Experiments, Decisions, Scripts, Sources). Identical layout across all three projects.
- [generic] log.md format: append-only, `## [YYYY-MM-DD] operation | subject` with 1-2 line description. Identical across all three.
- [generic] Page format, status values, wikilink convention: identical across all three. Fully generic.
- [generic] .Rproj: RestoreWorkspace No, SaveWorkspace Never. Identical across all three.
- [generic] .gitignore: /Data/, /Images/, /Sources/, .RData, .Rhistory, .Rproj.user/, clauder_logs/. Near-identical; Periostin anchors with / to avoid case-insensitive wiki/sources/ collision on Windows. B-cell tracks Sources/ (exception: verification targets). The anchor pattern should be default.
- [generic] Script registry: identical stub format across all three.
- [new] tma-halo-ingest.md: project-specific workflow, but the pattern (autonomous ingest procedure with marker identification, QC, rename, file, update wiki) could be generalised for any HALO export type. The Periostin project's data-intake-convention.md and B-cell's export-ingest.md serve the same role but for different platforms (HALO vs Visiopharm).
- [new] stain-inventory.md: new page type not in Periostin or B-cell. Needed because this project has ~30 markers on one TMA. Other projects don't have this many parallel stains. This is project-specific rather than a generic category.
- [new] halo-export-format.md: carried from Periostin but trimmed to TMA-specific content (Periostin version covers both per-slide and TMA). A generic skill would need to handle both variants or let the user specify.
- [parameterise] Cross-project references: the pdx-tma.md entity page links to the Periostin project by absolute path. This pattern (pointer to another project's data) is reusable but the specific paths are project-specific.
- [generic] Data migration pattern: copy from source, don't move. Leave source intact. This is a one-time operation during project creation, not part of the ongoing workflow.
- [generic] The ingest workflow (marker identification from column headers, QC row count, rename, file, wiki update) worked correctly first try on all 12 archives. The deterministic marker-from-header extraction is reliable.
- [observation] The ingest found duplicates (same marker in two archives — one with summary, one without). The workflow handles this by skipping if the folder exists, but the AR NTD case showed that the first-ingested version can be incomplete (obj only, no summary). A refinement: when a folder exists, check whether the new archive has files the existing one lacks, and supplement rather than skip.
- [generic] Stain inventory page: useful when a project has many parallel analyses on the same tissue. Not needed for single-marker projects. The skill could offer this as an optional page type triggered by "TMA" or "multi-marker" in the project description.

## Summary for skill creation session

The following are fully generic and can be templated verbatim:
1. Page format (status/date/content/sources with wikilinks)
2. Anti-patterns list
3. R Studio workflow rules
4. Wiki maintenance triggers and timing
5. index.md and log.md structure and format
6. .Rproj settings
7. .gitignore base patterns
8. Script registry stub
9. CLAUDE.md section ordering

The following need user input to parameterise:
1. Project name (drives folder, .Rproj, CLAUDE.md title, git remote)
2. Project overview paragraph (1-3 sentences)
3. Data folder structure (which subfolders under Data/)
4. Workflow pages (what ingest procedures apply)
5. Seed entity pages (what entities exist at project creation)
6. Category set (most projects use all 7 categories; some may not need all)
7. CLAUDE.md line limit (settle on one value)
8. Cross-project references (optional)

The following emerged as project-specific and should NOT be in the generic skill:
1. Genomic data subfolder (specific to PDX TMA)
2. Stain inventory page (specific to multi-marker TMA projects)
3. Specific ingest workflow content (HALO TMA vs HALO per-slide vs Visiopharm)
4. old data/ handling (one-time migration concern)

## Project instructions (Claude Desktop system prompt)

Each project has a short block of text set as the project instructions in Claude Desktop.
This is read before any conversation starts and tells the session how to bootstrap.

Generic structure (identical across all three projects):
1. Check for MCP access (python-interpreter or r-studio tools)
2. When confirmed: use python-interpreter:run_python_code with standard file I/O; do NOT use read_file, list_directory, or bash for local access
3. Read CLAUDE.md and wiki/index.md before the first response
4. Follow CLAUDE.md for the rest of the session
5. When MCP not available: say so and proceed without file access

Parameterised:
- The two file paths (CLAUDE.md and index.md) — derived from the project root
- An optional project-specific directive between steps 3 and 5:
  - B-cell: "Do not re-derive data structure from raw exports; the wiki documents columns, phenotype labels, factor values and export versions"
  - PDX TMA: "When a new HALO export arrives, read wiki/workflows/tma-halo-ingest.md and follow the procedure without asking"
  - Periostin: none (no project-specific directive needed at the time of writing)

The skill could generate these instructions automatically from the project root path, with an optional slot for a project-specific directive the user provides.
- [workflow refinement] The tma-halo-ingest workflow identified markers from the summary CSV header only. This missed a real failure mode: HALO can produce archives where the summary CSV and object data CSV are from different stains (same mismatch problem as Visiopharm's two-metadata-block issue in the B-cell project). The workflow should be updated to check BOTH summary and object data headers and flag if they disagree, rather than trusting the summary alone. This is a cross-platform gotcha worth documenting in any HALO ingest workflow.
