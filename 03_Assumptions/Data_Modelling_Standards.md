# Data Modelling Standards
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Data Modelling Standards |
| Document Version | 1.0 |
| Document Status | Proposed Standards |
| Modelling Tool | ERwin Data Modeler |
| Target Database | PostgreSQL |

---

## 1. Purpose

This document defines the data modelling standards, naming conventions, design principles and documentation guidelines to be followed during the development of the Insurance Enterprise Data Warehouse.

The standards aim to ensure:

- Consistency across all data models.
- Standardised entity and attribute naming.
- Appropriate primary and foreign key design.
- Clear relationship definitions.
- Data integrity and referential consistency.
- Reusability of common enterprise data structures.
- Maintainability of logical and physical models.
- Consistency between ERwin models and PostgreSQL implementation.

These standards will apply to the Conceptual Data Model (CDM), Logical Data Model (LDM), Physical Data Model (PDM) and Dimensional Data Model.

## 2. Data Modelling Principles

The project will follow these core principles.

| Principle | Standard |
|---|---|
| Business Alignment | Models must represent documented business requirements and rules. |
| Standardisation | Consistent naming conventions must be followed. |
| Reusability | Common business entities should be reusable across domains. |
| Normalisation | The enterprise logical model should generally follow 3NF principles. |
| Data Integrity | Appropriate keys and relationship constraints must be defined. |
| Traceability | Source identifiers and lineage information must be retained where required. |
| Scalability | The model should accommodate reasonable future business extensions. |
| Documentation | Entities, attributes, relationships and design decisions must be documented. |
| Historical Tracking | History requirements must be evaluated for applicable entities and attributes. |
| Technology Alignment | Physical design must be compatible with PostgreSQL. |

## 3. Naming Conventions

### 3.1 General Naming Standards

- Use uppercase letters for database object names.
- Use underscores to separate words.
- Avoid spaces and special characters.
- Use meaningful and business-readable names.
- Avoid unnecessary abbreviations.
- Use singular names for entity and table names.
- Use consistent terminology across all models.
- Avoid reserved SQL keywords.
- Use the same logical name in CDM, LDM and PDM unless a documented physical constraint requires a different name.

### 3.2 Entity Naming Convention

Entity names must represent business objects or concepts.

**Format:** `BUSINESS_ENTITY_NAME`

Examples:

| Recommended Name | Avoid |
|---|---|
| CUSTOMER | CUSTOMERS |
| INSURANCE_PRODUCT | PRODUCT_TABLE |
| POLICY | POLICY_DATA |
| PREMIUM_INVOICE | PREM_INV |
| PAYMENT_TRANSACTION | PAYMENT_TBL |
| CLAIM | CLAIM_INFO |
| AGENT | AGT |

### 3.3 Attribute Naming Convention

Attribute names must clearly identify the information being stored.

Examples:

| Recommended Attribute | Meaning |
|---|---|
| CUSTOMER_ID | Customer identifier |
| CUSTOMER_NAME | Customer name |
| POLICY_NUMBER | Policy business number |
| POLICY_START_DATE | Policy effective start date |
| POLICY_END_DATE | Policy expiry or end date |
| PREMIUM_AMOUNT | Premium amount |
| PAYMENT_DATE | Payment transaction date |
| CLAIM_STATUS_CODE | Claim status code |
| CREATED_TIMESTAMP | Record creation timestamp |
| UPDATED_TIMESTAMP | Last update timestamp |

Avoid vague names such as `VALUE`, `TYPE`, `STATUS` or `DATE` when a more descriptive name is possible.

### 3.4 Primary Key Naming Convention

Primary key attributes should follow:

`ENTITY_NAME_ID`

Examples:

- CUSTOMER_ID
- POLICY_ID
- INSURANCE_PRODUCT_ID
- PREMIUM_INVOICE_ID
- PAYMENT_TRANSACTION_ID
- CLAIM_ID
- AGENT_ID

Primary key attributes must be unique and non-null.

### 3.5 Foreign Key Naming Convention

Foreign key attributes should normally use the same name as the referenced primary key.

Examples:

- CUSTOMER_ID in POLICY_HOLDER.
- POLICY_ID in POLICY_COVERAGE.
- INSURANCE_PRODUCT_ID in POLICY.
- PREMIUM_INVOICE_ID in PAYMENT_ALLOCATION.
- PAYMENT_TRANSACTION_ID in PAYMENT_ALLOCATION.
- CLAIM_ID in CLAIM_SETTLEMENT.

Where multiple relationships reference the same entity in different roles, use role-specific names such as `SELLING_AGENT_ID` and `SERVICING_AGENT_ID`.

### 3.6 Constraint Naming Convention

| Database Object | Naming Pattern | Example |
|---|---|---|
| Primary Key | PK_TABLE_NAME | PK_CUSTOMER |
| Foreign Key | FK_CHILD_PARENT | FK_POLICY_CUSTOMER |
| Unique Constraint | UK_TABLE_ATTRIBUTE | UK_CUSTOMER_EMAIL |
| Check Constraint | CK_TABLE_RULE | CK_POLICY_DATE |
| Index | IX_TABLE_ATTRIBUTE | IX_POLICY_STATUS |
| Sequence | SEQ_TABLE_NAME | SEQ_CUSTOMER |

Actual constraint names will be finalised during physical modelling.

## 4. Conceptual Data Model Standards

The CDM must represent the business view of the organisation without database implementation details.

### 4.1 Entity Identification

- Identify entities based on business requirements.
- Use meaningful business terminology.
- Avoid implementation-specific table names.
- Identify major business objects and reference concepts.
- Avoid introducing entities without a business justification.

### 4.2 Relationship Definition

- Define relationships between relevant business entities.
- Identify relationship cardinality.
- Identify mandatory and optional participation.
- Use business-readable relationship descriptions.
- Resolve ambiguous business relationships through documented assumptions.

### 4.3 CDM Example

Example conceptual entities:

- Customer
- Insurance Product
- Policy
- Coverage
- Premium Invoice
- Payment
- Claim
- Agent
- Branch

The CDM should focus on business relationships rather than physical attributes, indexes or database-specific constraints.

## 5. Logical Data Model Standards

The LDM must provide a detailed, technology-independent representation of the enterprise data structure.

### 5.1 Entity Standards

Each logical entity must:

- Represent a clearly defined business concept.
- Have a unique entity name.
- Include an entity definition.
- Have appropriately defined attributes.
- Have an identified primary key.
- Include relevant relationships.
- Follow normalisation principles where appropriate.

### 5.2 Attribute Standards

Each attribute must have:

- Attribute name.
- Business definition.
- Logical data type.
- Mandatory or optional indicator.
- Key classification, where applicable.
- Applicable business rule or validation requirement.

### 5.3 Key Standards

**Primary Keys**
- Every entity must have an appropriate primary key.
- Primary key values must be unique.
- Primary key attributes must not contain null values.

**Foreign Keys**
- Foreign keys must reference valid parent entity keys.
- Relationship definitions must reflect business rules.
- Referential integrity must be considered.

**Business Keys**
- Natural or business identifiers must be identified separately from technical primary keys.
- Business key uniqueness must be defined within the appropriate scope.
- Source system identifiers must be retained where required.

**Alternate Keys**
- Additional candidate keys must be documented where applicable.
- Unique business combinations must be identified.

### 5.4 Normalisation Standards

The enterprise logical model will generally follow Third Normal Form (3NF).

| Normal Form | Design Principle |
|---|---|
| First Normal Form (1NF) | Attributes must contain atomic values and repeating groups must be avoided. |
| Second Normal Form (2NF) | Non-key attributes must depend on the complete candidate key. |
| Third Normal Form (3NF) | Non-key attributes must not depend transitively on a candidate key. |

Normalisation should support data consistency and reduce unnecessary redundancy.

Denormalisation may be considered in the dimensional model or other reporting structures when justified by analytical requirements.

### 5.5 Associative Entity Standards

Many-to-many relationships must be resolved using associative entities where appropriate.

Examples:

| Business Relationship | Associative Entity |
|---|---|
| Customer and Policy | POLICY_HOLDER |
| Product and Coverage | PRODUCT_COVERAGE |
| Policy and Coverage | POLICY_COVERAGE |
| Payment and Premium Invoice | PAYMENT_ALLOCATION |

Associative entities must contain the foreign keys required to represent the relationship and may include additional business attributes.

## 6. Relationship and Cardinality Standards

Relationships must accurately represent business rules.

The following relationship types will be used:

| Relationship Type | Meaning | Example |
|---|---|---|
| 1:1 | One parent record relates to one child record | A specific one-to-one extension, if justified |
| 1:M | One parent record relates to multiple child records | CUSTOMER to CUSTOMER_ADDRESS |
| M:N | Multiple records on both sides relate to each other | PRODUCT to COVERAGE_TYPE before resolution |

### Relationship Modelling Guidelines

- Every relationship must have a documented business meaning.
- Parent and child entities must be identified.
- Mandatory and optional relationships must be defined.
- Foreign key placement must be consistent with the relationship.
- Many-to-many relationships must be resolved in the LDM.
- Relationship cardinality must agree with documented business rules.

## 7. Physical Data Model Standards

The PDM must represent the database implementation of the logical model.

### 7.1 Database Standards

- Target database: PostgreSQL.
- Use PostgreSQL-compatible data types.
- Define appropriate primary and foreign key constraints.
- Define nullability based on business requirements.
- Apply unique and check constraints where appropriate.
- Create indexes based on expected query and join requirements.
- Avoid unnecessary database objects.

### 7.2 Proposed Data Type Standards

| Data Attribute | Proposed PostgreSQL Data Type | Reason |
|---|---|---|
| Technical identifier | BIGINT or UUID | Unique record identification |
| Business identifier | VARCHAR | Business numbers and codes |
| Name | VARCHAR(200) | Person, organisation or product names |
| Description | VARCHAR or TEXT | Descriptive information |
| Date | DATE | Business dates |
| Timestamp | TIMESTAMP WITH TIME ZONE | Time-aware event or audit timestamps |
| Monetary amount | NUMERIC(18,2) | Financial precision |
| Percentage | NUMERIC(7,4) | Percentage values with fractional precision |
| Boolean indicator | BOOLEAN | True/false attributes |
| Status code | VARCHAR(30) | Controlled status values |

Final data types and lengths must be validated against the actual attribute definitions and expected data ranges.

### 7.3 Monetary Data Standards

- Use NUMERIC rather than FLOAT or REAL for financial values.
- Store currency information alongside monetary values.
- Do not combine different currencies without an explicit conversion rule.
- Document the precision and scale of monetary attributes.
- Maintain original transaction amounts where currency conversion is required.

### 7.4 Date and Timestamp Standards

- Use DATE for business dates that do not require time information.
- Use TIMESTAMP WITH TIME ZONE for events requiring time-zone-aware timestamps.
- Distinguish business-effective dates from transaction timestamps.
- Use consistent date and timestamp definitions.
- Document the time-zone handling approach.

### 7.5 Nullability Standards

- Mandatory business attributes must be defined as NOT NULL where appropriate.
- Optional attributes may allow NULL values.
- Unknown, unavailable and not-applicable values must not be treated as interchangeable.
- Avoid arbitrary default values for missing business information.
- Document the handling of missing or invalid source values.

## 8. Audit and Metadata Standards

Relevant physical tables should include appropriate audit attributes based on their business and technical requirements.

| Attribute | Description |
|---|---|
| SOURCE_SYSTEM_CODE | Identifies the originating source system |
| SOURCE_RECORD_ID | Original source record identifier |
| CREATED_TIMESTAMP | Record creation timestamp |
| UPDATED_TIMESTAMP | Last update timestamp |
| CREATED_BY | Record creation process or user |
| UPDATED_BY | Last update process or user |
| BATCH_ID | Identifies the ingestion or processing batch |

Not every table must contain every audit attribute. The applicable columns will be selected according to the data integration and audit requirements.

## 9. Historical Data Management Standards

Historical data management must be based on documented business requirements.

### 9.1 Operational History

Where business history is required, maintain appropriate effective dates and transaction dates.

Examples:

- Policy status history.
- Policy endorsement history.
- Claim status history.
- Agent branch assignment history.

### 9.2 Slowly Changing Dimensions

The following dimensional history approaches will be considered:

| SCD Type | Description | Use Case |
|---|---|---|
| Type 0 | Retain the original value without change | Immutable historical attributes |
| Type 1 | Overwrite the existing value | Corrections where historical changes are not required |
| Type 2 | Create a new version of the dimension record | Historical customer, product or agent attribute changes |
| Type 3 | Retain limited previous values in additional columns | Specific reporting needs requiring limited history |

Type 2 dimensions should generally include:

- Surrogate key.
- Business key.
- Effective start date.
- Effective end date.
- Current record indicator.

The chosen SCD strategy must be documented for each relevant dimension.

## 10. Dimensional Modelling Standards

The dimensional model will follow analytical modelling principles.

### 10.1 Fact Table Standards

Each fact table must have:

- A documented business process.
- A clearly defined grain.
- Appropriate dimension relationships.
- Measures with defined business meaning.
- Documented aggregation behaviour.

### 10.2 Dimension Table Standards

Each dimension must:

- Represent a business analysis perspective.
- Have a surrogate primary key.
- Retain appropriate business identifiers.
- Include descriptive attributes.
- Support historical tracking where required.

### 10.3 Fact Table Naming Convention

Use the prefix `FACT_` for fact tables.

Examples:

- FACT_PREMIUM_BILLING
- FACT_PAYMENT_TRANSACTION
- FACT_CLAIM
- FACT_POLICY_SNAPSHOT

### 10.4 Dimension Table Naming Convention

Use the prefix `DIM_` for dimension tables.

Examples:

- DIM_CUSTOMER
- DIM_PRODUCT
- DIM_POLICY
- DIM_AGENT
- DIM_BRANCH
- DIM_DATE

### 10.5 Fact Table Grain

The grain must be documented before identifying measures.

Example:

**FACT_PAYMENT_TRANSACTION**

Proposed grain: One row per individual payment transaction.

Example:

**FACT_PREMIUM_BILLING**

Proposed grain: One row per premium invoice.

The final grain must be validated against the actual reporting requirements and source data assumptions.

## 11. Reference Data Standards

Reference data should be maintained consistently across the enterprise model.

Examples:

- POLICY_STATUS
- PAYMENT_STATUS
- CLAIM_STATUS
- PRODUCT_CATEGORY
- COVERAGE_TYPE
- CUSTOMER_TYPE
- CURRENCY

Standards:

- Use consistent business codes and descriptions.
- Avoid inconsistent free-text status values.
- Define valid values and meanings.
- Maintain effective dates where reference values change over time.
- Document source system mappings for reference values.

## 12. ERwin Data Modeler Standards

ERwin Data Modeler will be used to create and maintain the project's data models.

### 12.1 Model Organisation

Maintain separate model deliverables for:

- Conceptual Data Model.
- Logical Data Model.
- Physical Data Model.
- Dimensional Data Model.

Where supported by the ERwin version and project workflow, related models may be maintained within a coordinated model environment.

### 12.2 Model Documentation

Each model must include:

- Model name.
- Model description.
- Version number.
- Creation or update date.
- Business domain.
- Model owner or author role.
- Assumptions and relevant design decisions.

### 12.3 Entity and Attribute Documentation

- Every entity must have a meaningful definition.
- Important attributes must have business definitions.
- Primary and foreign keys must be clearly identified.
- Relationship names must be meaningful.
- Subject areas should be used to organise related business entities where appropriate.

### 12.4 Model Quality Review

Before publishing a model:

- Review entity and attribute names.
- Check for duplicate or redundant entities.
- Validate primary and foreign key definitions.
- Review relationship cardinality and optionality.
- Check for unresolved many-to-many relationships in the LDM.
- Verify logical-to-physical consistency.
- Review model completeness against requirements.

## 13. Documentation Standards

All project documentation must follow consistent conventions.

| Document Type | Recommended Format |
|---|---|
| Project documentation | Markdown (.md) |
| Data dictionaries | Excel (.xlsx) |
| Source-to-target mapping | Excel (.xlsx) |
| ERwin model files | Native ERwin model format supported by the installed version |
| Model diagrams | PDF and PNG |
| Architecture diagrams | Draw.io and PNG |
| Database scripts | SQL (.sql) |
| Synthetic data | CSV (.csv) |

Documentation must:

- Include a title and project name.
- Include document version and status.
- Use consistent terminology.
- Include relevant requirement and rule identifiers.
- Clearly distinguish assumptions from confirmed design decisions.
- Be updated when model changes affect documented information.

## 14. Version Control Standards

GitHub will be used to maintain project documentation and deliverables.

Recommended practices:

- Maintain a clear folder structure.
- Use descriptive file names.
- Maintain version information in key documents.
- Use meaningful commit messages.
- Avoid uploading temporary or duplicate files.
- Review files before committing.
- Do not publish confidential or sensitive information.
- Maintain consistency between model diagrams, documentation and SQL scripts.

Recommended commit message examples:

- `docs: add insurance business requirements`
- `model: add conceptual data model`
- `model: update policy and coverage relationships`
- `sql: create customer and policy tables`
- `test: add referential integrity checks`

## 15. Data Security and Privacy Standards

- Use synthetic customer and transaction data.
- Do not include actual customer names, addresses, phone numbers or financial information.
- Do not upload employer or client-owned ERwin models.
- Do not publish credentials, database passwords or connection strings.
- Review all files before making the repository public.
- Treat the proposed security architecture as a design consideration unless it is actually implemented.

## 16. Standards Compliance Checklist

The following checklist will be used during model reviews.

| Review Area | Validation |
|---|---|
| Entity Naming | Consistent entity naming convention followed |
| Attribute Naming | Clear and meaningful attribute names |
| Primary Keys | Every entity has an appropriate primary key |
| Foreign Keys | Relationships have appropriate foreign keys |
| Business Keys | Business identifiers documented |
| Normalisation | LDM follows appropriate normalisation principles |
| Relationships | Cardinality and optionality validated |
| Data Types | Appropriate PostgreSQL-compatible data types |
| Nullability | Mandatory and optional attributes identified |
| Referential Integrity | Relationships and constraints reviewed |
| Historical Tracking | History requirements addressed |
| Dimensional Modelling | Fact grain and measures documented |
| Documentation | Entity and attribute definitions available |
| Version Control | Changes maintained in GitHub |

## 17. Standard Maintenance

These standards will be reviewed and updated as the project progresses.

Any exception to the defined standards must:

- Be documented.
- Include a reason for the exception.
- Identify the affected entities or attributes.
- Be reflected in the relevant model documentation.

---

**End of Document**
