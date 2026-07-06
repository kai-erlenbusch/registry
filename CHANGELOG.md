# Datapond Changelog

## 2026-07-06 — Full refresh + data-quality audit

All five Nason-maintained databases were rebuilt from their latest sources,
then independently audited from a researcher's perspective (every finding
SQL-verified), repaired, and republished. Per-database details live in each
repo's CHANGELOG.md and on the HuggingFace dataset pages.

| Database | Rows (old → new) | Data now through | Headline changes |
|----------|------------------|------------------|------------------|
| eoir | 164.6M → 169.2M | 2026 | Values normalized: charge-lookup joins 77% → 100% coverage |
| ice | 17.8M → 22.0M | 2026-03-10 | New `encounters` table; 2026 FOIA release; views rewritten (were producing negative durations); cross-release double counting removed |
| fec | 339.5M → 347.2M | 2026 cycle | Standalone-table dates fixed (were 100% NULL); IE amendments deduplicated; views rebuilt with conduit/refund-correct money math |
| clinicaltrials | 56.4M → 58.0M | June 2026 | ACTUAL/ESTIMATED date-type columns restored; docs corrected |
| cms-medicare | 121.7M → 132.9M | CY2024 | CY2024 added; corrupted geography HCPCS codes and NPI/ZIP typing repaired; suppression undercount documented |

Also released: **datapond 0.1.2** on PyPI — fixes `connect()`/CLI for
hyphenated database IDs (`cms-medicare`, `ipeds-db`).

Every database README now carries a researcher-caveats section covering the
semantics traps the audit surfaced (suppression undercounts, granularity,
coverage windows, upstream dirty dates, how to sum FEC money correctly).

ipeds-db is maintained upstream by paulgp85 and was health-checked but not
rebuilt.
