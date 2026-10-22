# Reading files (interpreter, library, encoding per filetype)

Status: settled
Last updated: 2026-10-12
Scope: shared
Copied from: Studies/wiki/methods/reading-files.md (2026-10-22)

Mechanics for reading files off the local filesystem with the Python tool. This
page covers extraction only. Filing data after reading follows
[[data-intake-convention]]; the paper ingest procedure is [[source-ingest]].

All filesystem access uses `python-interpreter:run_python_code` with standard
Python I/O (`open()`, `os.walk()`), never `read_file` or `list_directory`
(path-restricted). Open text files with `encoding="utf-8", errors="replace"`.
Each call must return within about a minute: exclude `Images/`, `Data/raw/` and
`incoming/` from any `os.walk()`, since walking them hangs the tool.

## Interpreter environments

`run_python_code` defaults to the `system` environment (the uv-cached Python),
which does **not** have PDF or spreadsheet libraries installed. Libraries live in
the `default` environment:
`C:\Users\bgurel\AppData\Local\Programs\Python\Python313\python.exe`.

For any read that needs a third-party library (PDF, xlsx, qptiff), call with
`environment="default"` and `execution_mode="subprocess"`. Plain text and CSV via
`open()` work in either environment.

## PDF (source papers)

- Preferred: `pymupdf4llm` (installed in `default`). Outputs Markdown with
  correct multi-column reading order, table detection and header identification.
  Save the extracted text alongside the PDF as `<filename>_text.md` for reuse.

```python
import pymupdf4llm

md = pymupdf4llm.to_markdown("path/to/paper.pdf")
with open("path/to/paper_text.md", "w", encoding="utf-8") as f:
    f.write(md)
```

- Tables render as approximate Markdown tables; verify key numbers against the
  PDF when precision matters.
- Figure content appears in `<!-- Start of picture text -->` blocks containing
  OCR of text within figure images. Useful for plot annotations, not structured
  data.
- `pymupdf4llm` pulls in `pymupdf` (PyMuPDF), so raw `fitz` access is available
  if needed (embedded images, scanned PDFs).
- Fallback: `pypdf` (also installed) for simple text-only extraction.

## CSV / TSV (HALO and Visiopharm exports, processed data)

- Both HALO and Visiopharm exports carry a UTF-8 byte-order mark: read with
  `encoding="utf-8-sig"` or the first column name picks up a stray BOM artefact.
- In R, `data.table::fread` handles these directly.

## xlsx

- Library: `openpyxl` or `pandas.read_excel` (install into `default` if absent).
- Call with `environment="default"`, `execution_mode="subprocess"`.

## XML (HALO .annotations)

- Structure: `<Annotations>` → `<Annotation Name=...>` →
  `<Region NegativeROA="0|1">` → `<Vertices>` → `<V X= Y=>`. Regions with
  `NegativeROA="1"` are holes and must be subtracted.
- Exploratory inspection in Python: `xml.etree.ElementTree` streaming with
  `iterparse`, clearing elements as you go, so cost stays flat with file size.
  Mouse allograft files run to ~140 MB and 3.7 million vertices; a full DOM load
  chokes.
- **Do not** use R `xml2::read_xml` on large files: it builds the whole DOM in
  memory and `//` xpaths walk it repeatedly, which hangs the R tool. R/xml2 is
  fine for small human-cohort files (a few MB).
- Bounding-box X/Y ranges are a poor proxy for spatial arrangement: diagonally
  placed tissue pieces have overlapping boxes but are cleanly separated.
- A fast regex-based R parser for whole annotation layers (no DOM, about 90x
  faster) exists in the Periostin study (`tumour_island_fragmentation.R`,
  `parse_layer_fast`). Copy it in if a study needs it.

## qptiff (Akoya/CODEX scans)

- Library: `tifffile` (in `default`). Call with `environment="default"`,
  `execution_mode="subprocess"`, `timeout` 300–600. Reading headers only is fast
  even on a 20 GB file; never read pixel data through the tool.
- Channel order = page order of `tf.series[0].pages`. Each page's
  `ImageDescription` tag is XML: `<Biomarker>` is the reliable channel name,
  `<Name>` holds the fluorophore (DAPI, ATTO 550, Cy5, AF 750). Visiopharm's
  `OriginalBandName` is `"<Biomarker> (<Name>)"`.

```python
import tifffile, re
with tifffile.TiffFile(path) as tf:
    for i, page in enumerate(tf.series[0].pages):
        d = page.tags['ImageDescription'].value
        bm = re.search(r'<Biomarker>(.*?)</Biomarker>', d)
        fl = re.search(r'<Name>(.*?)</Name>', d)
        print(i, bm.group(1), fl.group(1))
```

## Sources
- Related: [[data-intake-convention]], [[source-ingest]]

---

## Local

