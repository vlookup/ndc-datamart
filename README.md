# NDC-DataMart

A dimensional data mart built from the FDA NDC Directory to support pharmacy reference data and coverage analysis. Designed as an extensible foundation for incorporating additional public pharmacy and drug data sources over time.

## Purpose

Establish a clean, queryable model of FDA NDC product and package information across active, compounded, and excluded categories. The structure is intended to support ongoing expansion with other public pharmacy datasets.

## Vision

Build a lightweight, open pharmacy reference data mart that makes it easier to analyze drug coverage, pricing, and utilization questions using publicly available sources. The long-term goal is a single, well-documented model that can support research, portfolio work, and practical analysis without requiring proprietary data licenses.

## Roadmap

### Current (v1.0)
- FDA NDC Directory product and package files (active, unfinished, excluded, and compound)
- Clean dimensional model with consistent keys and standardized NDC11
- DuckDB-based queries and Jupyter notebooks for exploration

### Near-term
- RxNorm crosswalks and concept relationships
- WHO ATC hierarchy for therapeutic classification
- Basic quality checks and data profiling notebooks
- Improved documentation of grain, keys, and load process

### Longer-term
- FDA Orange Book patent and exclusivity data
- NCPDP or other public benchmark pricing sources
- Historical and current-state pricing snapshots
- Simple coverage and utilization analysis examples
- Additional public pharmacy and drug reference sources as they become available

## Data Sources

- [FDA NDC Directory](https://www.fda.gov/drugs/drug-approvals-and-databases/national-drug-code-directory)
- Additional public pharmacy and drug reference sources (planned)

## Status

In progress. Current focus is on the FDA NDC source files and the initial dimensional model.

## Tools

- Python
- DuckDB
- Jupyter / VS Code

## Disclaimer

This is a personal learning and portfolio project. It is not an official FDA product, is not intended for clinical or production use, and may contain gaps or inaccuracies. Data is pulled from public sources and transformed for educational and exploratory purposes.

## Contributing

Contributions, ideas, and feedback are welcome. If you see something that can be improved, have a useful public data source to add, or want to extend the model, feel free to open an issue or submit a pull request.

## Notes

This is a living document and will be updated as the project evolves.