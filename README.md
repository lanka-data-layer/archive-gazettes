# archive-gazettes

An open, verifiable archive of Sri Lanka's **extraordinary gazettes**, as published by the Department of Government Printing at [documents.gov.lk](https://documents.gov.lk/web/extra_gazettes). It covers every listed issue since 2010, in Sinhala, Tamil and English.

It is maintained by the [Lanka Data Layer](https://github.com/prabhavalabs/lanka-data-layer) harvester (`lanka docs harvest`) and published here by `lanka docs mirror`. This README's statistics are rewritten on every mirror run.

## Layout

| Path | What |
|---|---|
| `metadata/documents/<year>.jsonl` | One line per gazette: number, date, titles, upstream id, first and last seen, withdrawn date, and its files (language, SHA-256, bytes, pages, status, source URL). Sorted by `doc_id`, so changes diff cleanly. |
| `metadata/revisions/<year>.jsonl` | Every change the publisher made to a gazette's listing, when it was seen, and the record as it then stood |
| `months/<YYYY-MM>.json` | The manifest of a month's release: each PDF's name in the tarball, its SHA-256 and size, and the checksums of the release assets |
| Release `YYYY-MM` | `gazettes-YYYY-MM.tar` (the PDFs, named `<doc_id>_<lang>.pdf`), `text-YYYY-MM.tar.gz` (UTF-8 text, pages separated by form feeds) and `manifest-YYYY-MM.jsonl` |

## Verifying a file

```bash
gh release download 2026-11 -R lanka-data-layer/archive-gazettes -p 'gazettes-2026-11.tar'
tar -xf gazettes-2026-11.tar
shasum -a 256 gze-2515-01_en.pdf   # compare with metadata/documents/2026.jsonl
```

A month is published only when every file of that month has been fetched (or found missing upstream). Each file's checksum is re-checked against the archive before packing, and each asset's size and checksum are checked against GitHub after upload.

## Licence

See [NOTICE.md](NOTICE.md). In short: the gazettes are official texts and not under copyright, and the metadata is CC BY 4.0.

<!-- stats:start -->
Last mirrored: 2026-11-24 12:14 UTC (2026-11).

| Year | Documents | Files ok | Missing | Corrupt | Pending | Months published |
|---:|---:|---:|---:|---:|---:|---:|
| 2010 | 760 | 0 | 0 | 0 | 1440 | 0 |
| 2011 | 1195 | 0 | 0 | 0 | 2243 | 0 |
| 2012 | 1228 | 0 | 0 | 0 | 2422 | 0 |
| 2013 | 2033 | 0 | 0 | 0 | 4766 | 0 |
| 2014 | 2341 | 0 | 0 | 0 | 6546 | 0 |
| 2015 | 2342 | 0 | 0 | 0 | 6598 | 0 |
| 2016 | 2498 | 0 | 0 | 0 | 6937 | 0 |
| 2017 | 2512 | 0 | 0 | 0 | 7035 | 0 |
| 2018 | 2708 | 0 | 0 | 0 | 7715 | 0 |
| 2019 | 2923 | 0 | 0 | 0 | 8406 | 0 |
| 2020 | 1940 | 0 | 0 | 0 | 5594 | 0 |
| 2021 | 2676 | 0 | 0 | 0 | 7805 | 0 |
| 2022 | 3108 | 0 | 0 | 0 | 8894 | 0 |
| 2023 | 3011 | 0 | 0 | 0 | 8618 | 0 |
| 2024 | 2551 | 0 | 0 | 0 | 7289 | 0 |
| 2025 | 2973 | 0 | 0 | 0 | 8397 | 0 |
| 2026 | 2679 | 3530 | 0 | 0 | 3523 | 1 |
| **Total** | **39478** | **3530** | **0** | **0** | **104228** | **1** |

Archive total: 39478 documents, 3530 archived files, 2.4 GiB of PDFs.
<!-- stats:end -->
