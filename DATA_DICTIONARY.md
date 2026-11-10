# Data Dictionary — FDA NDC + RxNorm Data Mart

## Grain & Keys

| Table | Grain | Primary Key | Notes |
|-------|-------|-------------|-------|
| `package` | One row per NDC-11 package | `ndc11` | FDA package-level record |
| `product` | One row per product | `PRODUCTID` | FDA product-level record |
| `ndc_xwalk` | One row per NDC-11 + RxCUI | `ndc11`, `rxcui` | RxNorm NDC-to-RxCUI mapping |
| `concepts` | One row per RxCUI | `rxcui` | Preferred RxNorm concept name |

## package

| Field | Description |
|-------|-------------|
| `ndc11` | 11-digit National Drug Code (package level) |
| `NDCPACKAGECODE` | Original FDA package code |
| `PACKAGEDESCRIPTION` | Package size/form description |
| `STARTMARKETINGDATE` | Date package marketing began |
| `ENDMARKETINGDATE` | Date package marketing ended (blank if active) |
| `labeler_id` | Labeler identifier derived from NDC |
| `PRODUCTID` | Foreign key to `product` |
| `load_date` | Timestamp when the row was loaded |

## product

| Field | Description |
|-------|-------------|
| `PRODUCTID` | Primary key |
| `PRODUCTNDC` | Product-level NDC |
| `PROPRIETARYNAME` | Brand name |
| `NONPROPRIETARYNAME` | Generic name |
| `DOSAGEFORMNAME` | Dosage form (tablet, solution, etc.) |
| `ROUTENAME` | Route of administration |
| `SUBSTANCENAME` | Active substance |
| `ACTIVE_NUMERATOR_STRENGTH` | Strength value |
| `ACTIVE_INGRED_UNIT` | Strength unit |
| `PHARM_CLASSES` | Pharmacologic classes |
| `DEASCHEDULE` | DEA controlled substance schedule |
| `LABELERNAME` | Labeler / manufacturer name |
| `MARKETINGCATEGORYNAME` | Marketing category |
| `STARTMARKETINGDATE` | Product marketing start date |
| `ENDMARKETINGDATE` | Product marketing end date |
| `load_date` | Timestamp when the row was loaded |

## ndc_xwalk

| Field | Description |
|-------|-------------|
| `ndc11` | 11-digit NDC |
| `rxcui` | RxNorm concept unique identifier |
| `load_date` | Timestamp when the row was loaded |

## concepts

| Field | Description |
|-------|-------------|
| `rxcui` | RxNorm concept unique identifier |
| `name` | Preferred concept name |
| `tty` | Term type code |
| `term_type` | Human-readable term type description |
| `suppress` | Suppression flag |
| `load_date` | Timestamp when the row was loaded |

## TTY Lookup

| tty | term_type |
|-----|-----------|
| SCD | Semantic Clinical Drug |
| SBD | Semantic Branded Drug |
| GPCK | Generic Pack |
| BPCK | Branded Pack |
| IN | Ingredient |
| PIN | Precise Ingredient |
| BN | Brand Name |
| DF | Dose Form |
| SCDF | Semantic Clinical Drug Form |
| SBDF | Semantic Branded Drug Form |
| SCDG | Semantic Clinical Drug Group |
| SBDG | Semantic Branded Drug Group |
| MIN | Multiple Ingredients |
| TMSY | Tall Man Synonym |
| SY | Synonym |
| PSN | Prescribable Name |

## Quality Checks

The `quality_checks.py` script validates:

- NDC-11 format and length
- Null rates on key fields
- Duplicate detection on primary keys
- Referential integrity between `package` and `product`
- Row counts and basic distribution summaries
