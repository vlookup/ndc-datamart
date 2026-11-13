# NDC-DataMart

A dimensional data mart built from the FDA NDC Directory and public pharmacy pricing sources to support pharmacy reference data, coverage analysis, and benchmark pricing. Designed as an extensible foundation for incorporating additional public pharmacy and drug data sources over time.

## Purpose

Establish a clean, queryable model of FDA NDC product and package information across active, compounded, and excluded categories, enriched with public benchmark pricing. The structure is intended to support ongoing expansion with other public pharmacy datasets.

## Vision

Build a lightweight, open pharmacy reference data mart that makes it easier to analyze drug coverage, pricing, and utilization questions using publicly available sources. The long-term goal is a single, well-documented model that can support research, portfolio work, and practical analysis without requiring proprietary data licenses.

## Roadmap

### Current (v1.0.8)
- FDA NDC Directory product and package files (active, unfinished, excluded, and compound)
- Clean dimensional model with consistent keys and standardized NDC11
- DuckDB-based queries and Jupyter notebooks for exploration
- RxNorm crosswalks and concept relationships
- WHO ATC hierarchy for therapeutic classification
- CMS NADAC (National Average Drug Acquisition Cost) current benchmark pricing dimension
- Historical NADAC dimension (yearly datasets)
- Package + Product + NADAC join with package-level cost estimation
- FDA Orange Book products, patents, and exclusivity tables
- Therapeutic equivalence view for generic substitution analysis
- FDA Purple Book biologic and biosimilar patent and exclusivity data
- Basic quality checks and data profiling notebooks
- Improved documentation of grain, keys, and load process

### Longer-term
Nothing planned at this time. Recommendations for additional datasets or analysis ideas are welcome in the comments or via issues.

## Data Sources

- [FDA NDC Directory](https://www.fda.gov/drugs/drug-approvals-and-databases/national-drug-code-directory)
- [RxNorm / RxNav (NLM)](https://lhncbc.nlm.nih.gov/RxNav/)
- [CMS NADAC (National Average Drug Acquisition Cost)](https://data.medicaid.gov/dataset/fbb83258-11c7-47f5-8b18-5f8e79f7e704)
- [FDA Orange Book](https://www.fda.gov/drugs/drug-approvals-and-databases/approved-drug-products-therapeutic-equivalence-evaluations-orange-book)
- [FDA Purple Book](https://purplebooksearch.fda.gov/)
- Additional public pharmacy and drug reference sources (planned)

## Status

In progress. Current focus is on the FDA NDC source files, the dimensional model, NADAC pricing dimensions, Orange Book patent/exclusivity data, and Purple Book biologic/biosimilar data.

## Tools

- Python
- DuckDB
- Jupyter / VS Code

## Disclaimer

This is a personal learning and portfolio project. It is not an official FDA or CMS product, is not intended for clinical or production use, and may contain gaps or inaccuracies. Data is pulled from public sources and transformed for educational and exploratory purposes.

## Contributing

Contributions, ideas, and feedback are welcome. If you see something that can be improved, have a useful public data source to add, or want to extend the model, feel free to open an issue or submit a pull request.

## Notes

This is a living document and will be updated as the project evolves.