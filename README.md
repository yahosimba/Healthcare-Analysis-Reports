# Healthcare Performance Review

A public-data hospital monitoring project designed for a health ministry or national healthcare decision maker. Uses real US Centers for Medicare & Medicaid Services (CMS) data, without patient-level records.

## Delivery status

**Draft: Power BI display verification is pending.** Data preparation checks pass and the Excel summary was calculated and visually inspected. The editable Power BI definitions are generated, but a populated PBIX has not yet been saved or verified. Do not describe this package as a tested, portfolio-ready Power BI report. The Word handbook has been authored; its final rendered layout check is pending because the installed document renderer was unavailable and Word did not expose a usable window.

## Files

- `Healthcare_Performance_Data.xlsx`: management summary, provider data, state comparison, periods, sources, definitions and audit.
- `docs/Healthcare_Performance_Process_Handbook.docx`: process, cleaning rules, model, formulas and reconstruction instructions.
- `powerbi/Healthcare_Performance.pbip`: editable project; keep both adjacent report and semantic-model folders.
- `data/`: complete prepared CSVs, measure register and validation results.
- `sources/`: losslessly compressed official CSVs, source metadata and SHA256 hashes.
- `scripts/`: reproducible acquisition, preparation and report construction. These scripts were used to build the definitions; manual reconstruction is separately documented.

## Decision questions and report pages

1. Executive overview: reporting coverage and performance signals.
2. Geographic variation: compare states with coverage in view.
3. Emergency care: ED duration and patients leaving before care.
4. Mortality outcomes: condition-specific CMS comparisons.
5. Safety and clinical practice: published safety and process indicators.
6. Readmissions: excess ratios and condition-specific results.
7. Patient experience: rating, recommendation and communication.
8. Provider structure: hospital types and ownership.
9. Provider review queue: published worse-result flags for investigation.
10. Reporting coverage: missing scores and measurement windows.
11. Sources and definitions: provenance and audit.

The report uses cards, bars, columns, donut charts, scatter charts, matrices, tables and slicers. Visual definitions still require in-app verification.

## Snapshot findings

- 5,419 hospitals; 3,174 with an overall rating (58.6% coverage).
- Median provider ED duration: 148 minutes, across 4,081 reporting hospitals.
- Mean provider patient top-rating result: 71.7%, across 3,949 reporting hospitals.
- Mean provider sepsis-bundle result: 63.8%.
- 2,295 providers have at least one published worse-than-national result in the selected review domains.
- All 14 preparation checks pass; 120 unmatched readmission rows were excluded and documented.

These are unweighted provider summaries, not patient-weighted national rates. Different measures use different historical windows, spanning 2021–2025. A release date is not a performance date. This snapshot does not establish a monthly trend, causation or a UAE national result. No bed-occupancy, staffing, financial or monthly activity indicators were invented.

## Open and reproduce

Extract the entire package. Open `powerbi/Healthcare_Performance.pbip` in Power BI Desktop and choose Home > Refresh. Prepared CSVs are embedded as gzip-compressed snapshots inside Power Query, so there are no machine-specific source paths or website logins. After verifying populated visuals and filters, Save As a PBIX for convenient sharing. **A PBIX is not included yet.**

From the repository root, Python 3 standard library is sufficient for these scripts:

```sh
python scripts/prepare_data.py
python scripts/build_powerbi.py
python scripts/convert_legacy.py
```

To retrieve the latest official releases, first run `python scripts/fetch_sources.py`. Review changed source versions, reporting periods and validation results before replacing the current snapshot. The generated Excel/Word artifacts are supplied; the above scripts rebuild prepared data and Power BI definitions, not the formatted workbook or handbook.

## Compatibility and pending acceptance

The installed September 2026 Power BI Desktop failed in its enhanced-report schema loader. The active report uses the legacy `report.json` format. The `definition/` directory retains generated enhanced definitions as construction sources; `definition.pbir` version 1.0 activates the legacy report. Embedded snapshots were compressed to keep the query package below the size limit.

Before release: refresh without errors; compare cards against `data/Validation.json`; inspect all 11 pages; verify state/type filtering across related tables; check blank/suppressed scores stay blank; clear test filters; save and reopen a populated PBIX; render and inspect every handbook page. Current Windows automation reported `accessibility window-opened handler did not become ready`, preventing completion of these acceptance steps.

## Data attribution

See [DATA_NOTICES.md](DATA_NOTICES.md) and `sources/Source_Register.json`. This is an independent analytical project, not an official CMS product or clinical recommendation.
