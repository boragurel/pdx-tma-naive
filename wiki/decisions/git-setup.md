# Git setup

Status: settled
Last updated: 2026-10-12
Scope: shared
Copied from: Studies/wiki/decisions/git-setup.md (2026-10-22)

Every study folder is its own git repository, initialised at the study root,
with a private remote on GitHub (`boragurel/<repo-name>`) for off-site backup.
Private because the wiki holds unpublished results and sample identifiers.

## Tooling

- Windows git (Git for Windows) only, used from Git Bash or the RStudio Git
  pane. Both drive the same `.git` folder.
- **Never run WSL/Ubuntu git on a study repository** (via `/mnt/e/...`): Linux
  and Windows git disagree on file modes and line endings and report phantom
  changes.
- Global config: `core.autocrlf true`, `init.defaultBranch main`. Commits as
  Bora Gurel <bora.gurel@icr.ac.uk>. Auth is HTTPS via Git Credential Manager;
  no SSH key.

## Tracked

`Scripts/`, `wiki/`, `Figures/`, `CLAUDE.md`, `<Study Name>.Rproj`,
`.gitignore`. Compiled artefacts a pipeline actually ran (a `.dll` Visiopharm
called, say) are tracked so history records the build.

## .gitignore

```
/Data/
/Images/
/Sources/
.RData
.Rhistory
.Ruserdata
.Rproj.user/
__pycache__/
*.o
wiki/.obsidian/workspace*.json
/Scripts/clauder_logs/*
!/Scripts/clauder_logs/placeholder.R
```

- Root-anchored `/` patterns avoid case-insensitive collisions with
  `wiki/sources/` on Windows (`Sources/` would otherwise match it).
- `workspace*.json` is Obsidian window state, rewritten on every session; the
  other `.obsidian/` files are tracked.
- `Scripts/clauder_logs/` holds ClaudeR session logs: contents ignored,
  `placeholder.R` tracked so the folder exists in clones (the ClaudeR log-path
  field needs a file path, not a directory).
- A study with gated model weights, embeddings or credentials adds their
  extensions (`*.h5`, `*.pth`, `*.bin`, `*.safetensors`, `.env`) and any
  vendored external repo (`/external/`).

## Workflow

Commits are manual and deliberate: one per settled piece of work, typically
once or twice per session. At the end of each working session Claude proposes a
commit message summarising what changed in `wiki/` and `Scripts/`; Bora reviews
and runs it (`git commit -am` for tracked files; `git add` first for new files),
then `git push`. Claude never commits.

## Sources
- Related: [[r-project-setup]], [[derived-data-convention]]

---

## Local

- Repository: `E:\HALO\Studies\Treatment Naive PDX TMA`
- Remote: `https://github.com/boragurel/pdx-tma-naive.git` (private)
- Initialised and first pushed 2026-10-22; first commit `6ba70d7` ("Initial commit: wiki, CLAUDE.md, Rproj as of 2026-10-22")
- `.gitignore` is the canonical one, no additions. `wiki/meta/` (skill-prep notes) is tracked; the pre-git ignore file had excluded it.
- `Scripts/clauder_logs/` moved from the study root on 2026-10-22; ClaudeR log path updated accordingly.
