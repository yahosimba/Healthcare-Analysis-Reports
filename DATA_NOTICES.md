# Data sources and interpretation

All source tables are real public CMS Provider Data Catalog releases downloaded without login. The exact download links, release metadata, row counts and SHA256 hashes are recorded in `sources/Source_Register.json`.

Official dataset pages:

- Hospital General Information: https://data.cms.gov/provider-data/dataset/xubh-q36u
- Timely and Effective Care: https://data.cms.gov/provider-data/dataset/yv7e-xc69
- Complications and Deaths: https://data.cms.gov/provider-data/dataset/ynj2-r877
- Hospital Readmissions Reduction Program: https://data.cms.gov/provider-data/dataset/9n3s-kdb3
- HCAHPS Patient Survey: https://data.cms.gov/provider-data/dataset/dgck-syfz

The archived CSV files are gzip compressed without modifying their contents. Dataset metadata is retained with the snapshot. Refer to the official pages for current terms and technical specifications. No separate license is asserted for CMS data by this project.

The 27 selected indicators cover hospital operations, outcomes, readmissions and experience. Nulls preserve suppressed or nonnumeric scores; they are not zero performance. CMS risk-adjusted comparisons are preserved as published. A review flag is an investigation prompt, not a new clinical quality rating. Results require contextual interpretation and cannot direct patient treatment.
