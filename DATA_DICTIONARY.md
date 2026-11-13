# Data Dictionary — FDA NDC + RxNorm + Pricing + Orange Book + Purple Book Data Mart

## Grain & Keys

| Table | Grain | Primary Key | Notes |
|-------|-------|-------------|-------|
| package | One row per NDC-11 package | ndc11 | FDA package-level record |
| product | One row per product | PRODUCTID | FDA product-level record |
| ndc_xwalk | One row per NDC-11 + RxCUI | ndc11, rxcui | RxNorm NDC-to-RxCUI mapping |
| concepts | One row per RxCUI | rxcui | Preferred RxNorm concept name |
| atc_dimension | One row per RxCUI + ATC code | rxcui, atc_code | WHO ATC therapeutic classification |
| dim_nadac_benchmark | One row per NDC-11 (latest) | ndc11 | Current CMS NADAC price |
| dim_nadac_historical | One row per NDC-11 + effective date | ndc11, effective_date | Full weekly NADAC history |
| ndc_package_product_nadac | One row per NDC-11 with current NADAC | ndc11 | Joined package + product + current NADAC with cost estimate |
| orangebook_products | One row per application + product number | Appl_No, Product_No | FDA Orange Book product listing |
| orangebook_patents | One row per application + product + patent | Appl_No, Product_No, Patent_No | Orange Book patent records |
| orangebook_exclusivity | One row per application + product + exclusivity | Appl_No, Product_No, Exclusivity_Code | Orange Book exclusivity records |
| purplebook | One row per biologic / biosimilar product | BLA Number, Product ID (or Proprietary Name + Proper Name) | FDA Purple Book licensed biologics and biosimilars |

## package

| Field | Description |
|-------|-------------|
| ndc11 | 11-digit National Drug Code (package level) |
| NDCPACKAGECODE | Original FDA package code |
| PACKAGEDESCRIPTION | Package size/form description |
| STARTMARKETINGDATE | Date package marketing began |
| ENDMARKETINGDATE | Date package marketing ended (blank if active) |
| labeler_id | Labeler identifier derived from NDC |
| PRODUCTID | Foreign key to product |
| load_date | Timestamp when the row was loaded |

## product

| Field | Description |
|-------|-------------|
| PRODUCTID | Primary key |
| PRODUCTNDC | Product-level NDC |
| PROPRIETARYNAME | Brand name |
| NONPROPRIETARYNAME | Generic name |
| DOSAGEFORMNAME | Dosage form (tablet, solution, etc.) |
| ROUTENAME | Route of administration |
| SUBSTANCENAME | Active substance |
| ACTIVE_NUMERATOR_STRENGTH | Strength value |
| ACTIVE_INGRED_UNIT | Strength unit |
| PHARM_CLASSES | Pharmacologic classes |
| DEASCHEDULE | DEA controlled substance schedule |
| LABELERNAME | Labeler / manufacturer name |
| MARKETINGCATEGORYNAME | Marketing category |
| STARTMARKETINGDATE | Product marketing start date |
| ENDMARKETINGDATE | Product marketing end date |
| load_date | Timestamp when the row was loaded |

## ndc_xwalk

| Field | Description |
|-------|-------------|
| ndc11 | 11-digit NDC |
| rxcui | RxNorm concept unique identifier |
| load_date | Timestamp when the row was loaded |

## concepts

| Field | Description |
|-------|-------------|
| rxcui | RxNorm concept unique identifier |
| name | Preferred concept name |
| tty | Term type code |
| term_type | Human-readable term type description |
| suppress | Suppression flag |
| load_date | Timestamp when the row was loaded |

## atc_dimension

| Field | Description |
|-------|-------------|
| rxcui | RxNorm concept unique identifier |
| atc_code | WHO ATC classification code |
| atc_name | ATC description |
| load_date | Timestamp when the row was loaded |

## dim_nadac_benchmark

| Field | Description |
|-------|-------------|
| ndc11 | 11-digit NDC |
| ndc_raw | Original NDC as provided |
| ndc_description | NADAC drug description |
| nadac_per_unit | Current NADAC price per unit |
| effective_date | Effective date of the price |
| pricing_unit | Pricing unit (EA, ML, GM) |
| pharmacy_type_indicator | Pharmacy type used in survey |
| OTC | Over-the-counter flag |
| explanation_code | How the NADAC was calculated |
| classification_for_rate_setting | Brand/Generic classification |
| corresponding_generic_nadac | Corresponding generic NADAC |
| corresponding_generic_effective_date | Effective date of corresponding generic |
| as_of_date | As-of date of the file |
| loaded_at | Timestamp when the row was loaded |

## dim_nadac_historical

| Field | Description |
|-------|-------------|
| year | Calendar year of the source file |
| ndc11 | 11-digit NDC |
| ndc_raw | Original NDC as provided |
| ndc_description | NADAC drug description |
| nadac_per_unit | NADAC price per unit |
| effective_date | Effective date of the price |
| pricing_unit | Pricing unit (EA, ML, GM) |
| pharmacy_type_indicator | Pharmacy type used in survey |
| OTC | Over-the-counter flag |
| explanation_code | How the NADAC was calculated |
| classification_for_rate_setting | Brand/Generic classification |
| corresponding_generic_nadac | Corresponding generic NADAC |
| corresponding_generic_effective_date | Effective date of corresponding generic |
| as_of_date | As-of date of the file |
| loaded_at | Timestamp when the row was loaded |

## ndc_package_product_nadac

| Field | Description |
|-------|-------------|
| ndc11 | 11-digit NDC |
| package_description | FDA package description |
| proprietary_name | Brand name |
| nonproprietary_name | Generic name |
| dosage_form | Dosage form |
| route | Route of administration |
| strength | Strength value |
| strength_unit | Strength unit |
| labeler_name | Labeler / manufacturer |
| nadac_per_unit | Current NADAC price per unit |
| nadac_pricing_unit | NADAC pricing unit |
| package_qty | Parsed package quantity |
| package_nadac_estimate | Estimated package cost (nadac_per_unit × package_qty) |
| reason | Quantity parsing result / review flag |
| nadac_effective_date | Effective date of the NADAC price |
| pharmacy_type_indicator | Pharmacy type |
| OTC | Over-the-counter flag |
| explanation_code | NADAC explanation code |
| classification_for_rate_setting | Brand/Generic classification |
| corresponding_generic_nadac | Corresponding generic NADAC |
| nadac_as_of_date | As-of date of the NADAC file |

## orangebook_products

| Field | Description |
|-------|-------------|
| Ingredient | Active ingredient(s) |
| DF;Route | Dosage form and route of administration |
| Trade_Name | Proprietary / trade name |
| Applicant | Short applicant name |
| Strength | Product strength |
| Appl_Type | Application type (N = NDA, A = ANDA) |
| Appl_No | Application number |
| Product_No | Product number within the application |
| TE_Code | Therapeutic equivalence code |
| Approval_Date | Product approval date |
| RLD | Reference Listed Drug flag |
| RS | Reference Standard flag |
| Type | RX, OTC, or DISCN |
| Applicant_Full_Name | Full applicant / manufacturer name |
| loaded_at | Timestamp when the row was loaded |

## orangebook_patents

| Field | Description |
|-------|-------------|
| Appl_Type | Application type (N = NDA, A = ANDA) |
| Appl_No | Application number |
| Product_No | Product number within the application |
| Patent_No | Patent number |
| Patent_Expire_Date_Text | Patent expiration date (text) |
| Drug_Substance_Flag | Drug substance patent flag |
| Drug_Product_Flag | Drug product patent flag |
| Patent_Use_Code | Patent use code |
| Delist_Flag | Patent delist request flag |
| Submission_Date | Patent submission date |
| loaded_at | Timestamp when the row was loaded |

## orangebook_exclusivity

| Field | Description |
|-------|-------------|
| Appl_Type | Application type (N = NDA, A = ANDA) |
| Appl_No | Application number |
| Product_No | Product number within the application |
| Exclusivity_Code | Exclusivity code |
| Exclusivity_Date | Exclusivity expiration date |
| loaded_at | Timestamp when the row was loaded |

## purplebook

| Field | Description |
|-------|-------------|
| Proprietary Name | Brand / proprietary name |
| Proper Name | Non-proprietary / proper name |
| BLA Number | Biologics License Application number |
| License Type | License type (e.g., 351(a), 351(k)) |
| Strength | Product strength |
| Dosage Form | Dosage form |
| Route of Administration | Route of administration |
| Product Presentation | Product presentation / packaging |
| Marketing Status | Current marketing status |
| Licensure Date | Date of licensure |
| First Licensure Date | Date of first licensure |
| Reference Product Exclusivity Expiry Date | Reference product exclusivity expiry |
| First Interchangeable Exclusivity Expiry Date | First interchangeable exclusivity expiry |
| Reference Product Proper Name | Proper name of the reference product |
| Reference Product Proprietary Name | Proprietary name of the reference product |
| Supplemental Applications | Related supplemental applications |
| loaded_at | Timestamp when the row was loaded |

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

The quality checks validate:

- NDC-11 format and length
- Null rates on key fields
- Duplicate detection on primary keys
- Referential integrity between package and product
- Row counts and basic distribution summaries
- Source vs. parquet row counts for NADAC, Orange Book, and Purple Book loads