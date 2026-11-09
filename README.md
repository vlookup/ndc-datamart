# NDC-DataMart

A dimensional data mart built from the FDA NDC Directory to support pharmacy reference data and coverage analysis. Designed as an extensible foundation for incorporating additional public pharmacy and drug data sources over time.

## Purpose

Establish a clean, queryable model of FDA NDC product and package information across active, compounded, and excluded categories. The structure is intended to support ongoing expansion with other public pharmacy datasets.

## Data Sources

- [FDA NDC Directory](https://www.fda.gov/drugs/drug-approvals-and-databases/national-drug-code-directory)
- Additional public pharmacy and drug reference sources (planned)

## Status

In progress. Current focus is on the FDA NDC source files and the initial dimensional model.

## Tools

- Python
- DuckDB
- Jupyter / VS Code

## Notes

This is a living document and will be updated as the project evolves.
=======
# ndc-datamart
Dimensional model of FDA NDC Directory data (active, compounded, and excluded products and packages), designed to incorporate additional public pharmacy and drug reference sources for coverage analysis and healthcare data modeling with Python and DuckDB.
