# Import: HALO TMA re-exports, 28 Oct 2026

Status: active
Last updated: 2026-10-28

Re-export, one marker at a time, of the seven markers whose parallel export earlier
the same morning was withdrawn ([[halo-ingest-2026-10-28]]). Seven archives,
HALO v4.3.6992, exported 09:53–10:29; each finished before the next began.
Processed with [[tma-halo-ingest]] plus per-core reconciliation. All seven filed.

## QC (all seven)

Marker name agrees between summary and object headers; 98 rows; 98/98 reference
Spot Ids; standard columns present; Tumour layer only; classifier labels Tumour
only (first 5000 objects). Per-core reconciliation: total and positive cell counts
rebuilt from object data compared with the summary, and per-core image regions and
analysis start times compared between the two files.

## Filed

| Marker | Archive | HALO run (27 Oct) | Reconciliation | Sampled MD5 (summary, objects) |
|---|---|---|---|---|
| ASS1 | `09-54` | 17:13–17:57 | 98/98 cores | d2df58c7, f708a548 |
| SLFN11 | `09-56` | 17:57–18:39 | 98/98 cores | 47bee414, 0c4ca6fb |
| CBP | `10-28` | 18:39–19:20 | 98/98 cores | e3295617, a472259a |
| LC3A/B | `09-56-50` | 19:21–20:00 | 98/98 cores | cb6c9ebe, 13000dfe |
| ASCL4 | `09-57` | 20:01–20:41 | 98/98 cores | efea8bcc, f7867aae |

ASS1 and ASCL4 (both files) and LC3A/B (object data) are byte-identical to the
withdrawn morning exports.

## Filed with a note

| Marker | Archive | HALO run (27 Oct) | Reconciliation | Sampled MD5 (summary, objects) |
|---|---|---|---|---|
| p300 | `09-53` | 16:28–17:13 | 97/98 cores | 8be8f93d, 30f1b905 |
| ERG | `10-26` | 20:41–21:22 | 97/98 cores | f8e94b70, 4397b113 |

In both, the exception is control core Mouse prostate - 1: summary 0 cells, object
data one row with blank classification (HALO placeholder for a core with no detected
cells). Image regions and start times match for all 98 cores, this one included.
Not a run mismatch; filed on Bora's decision. Any code counting objects per core
should drop rows with blank classification.

## Shared

Summary CSVs of all seven copied 2026-10-28 to Ines's results folder,
`V:\Cancer Biomarkers\Ines\00000_results from the greatest pathologist in the universe\0 Done\{MARKER}\`,
matching the existing per-marker layout there; summaries verified by MD5. Object data
added the same day in `{MARKER}\ObjectData\` (2.4 GB), verified by size and sampled hash.
These are the only markers in that folder with object data.

## Sources
- Data: `Data/raw/p300/`, `Data/raw/ERG/`, `Data/raw/ASS1/`, `Data/raw/SLFN11/`, `Data/raw/CBP/`, `Data/raw/LC3AB/`, `Data/raw/ASCL4/`
- Related: [[halo-ingest-2026-10-28]], [[stain-inventory]], [[tma-halo-ingest]], [[ass1]], [[slfn11]], [[cbp]], [[lc3ab]], [[ascl4]], [[p300]], [[erg]]
