# Import: HALO TMA exports, 29 Oct 2026

Status: active
Last updated: 2026-10-29

Two single-marker exports, both new markers, HALO v4.4.7276 (previous batch v4.3.6992;
algorithm unchanged, Multiplex IHC v4.2.2). Exported 13:17 and 13:56; HALO runs on
29 Oct did not overlap. Processed with [[tma-halo-ingest]] plus per-core reconciliation.
Both filed.

## QC (both)

Marker name agrees between summary and object headers; 98 rows, all Spot Valid;
98/98 reference Spot Ids; columns identical (marker name aside) to the 28 Oct exports;
Tumour layer only; classifier labels Tumour only across all objects, not just the first
5000; no blank-classification rows. Per-core reconciliation: total and positive cell
counts rebuilt from object data match the summary, and per-core image regions and
analysis start times agree between the two files.

## Filed

| Marker | Archive | HALO run (29 Oct) | Objects | Reconciliation | MD5 (summary, objects) |
|---|---|---|---|---|---|
| BOK | `13-17` | 10:02–10:46 | 601,387 | 98/98 cores | d9c5c1d5, 99e48830 |
| SLC7A11 | `13-56` | 10:46–11:30 | 617,688 | 98/98 cores | 71a7c810, b72abf9d |

MD5 is over the whole file (earlier import pages used sampled hashes). Moves verified by
hash before and after; incoming archive folders removed once empty.

Slides `Images/All matched PDXs TMA BOK.vsi` and `... SLC7A11.vsi` are already in
`Images/` but no imports page records their arrival.

## Shared

Summary and object data for both copied 2026-10-29 to Ines's results folder,
`V:\Cancer Biomarkers\Ines\00000_results from the greatest pathologist in the universe\0 Done\{MARKER}\`
(object data in `ObjectData\`), same layout as the 28 Oct markers. All four files verified
by full MD5.

## Sources
- Data: `Data/raw/BOK/`, `Data/raw/SLC7A11/`
- Related: [[stain-inventory]], [[tma-halo-ingest]], [[bok]], [[slc7a11]], [[halo-reexport-2026-10-28]]
