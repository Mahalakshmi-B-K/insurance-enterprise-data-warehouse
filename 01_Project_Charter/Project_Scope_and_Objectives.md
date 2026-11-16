# Project Scope and Objectives
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Project Scope and Objectives |
| Document Version | 1.0 |
| Document Status | Draft |
| Target Database | PostgreSQL |
| Data Modelling Tool | ERwin Data Modeler |

---

## 1. Purpose

This document defines the scope, objectives, inclusions, exclusions, business domains and expected deliverables of the Insurance Enterprise Data Warehouse project.

It establishes the boundaries of the proposed solution to ensure that data modelling and database design activities remain aligned with the intended business requirements.

## 2. Project Objectives

The main objective is to design an integrated enterprise data warehouse that supports insurance business reporting and analytics.

The specific objectives are:

### 2.1 Enterprise Data Modelling

- Identify enterprise-level business entities.
- Define entity attributes and relationships.
- Establish primary keys, foreign keys and business keys.
- Apply appropriate normalisation principles.
- Maintain consistent naming conventions and modelling standards.

### 2.2 Data Integration

- Identify hypothetical operational source systems.
- Understand source data structures and attributes.
- Define source-to-target mappings.
- Document data transformation and standardisation rules.
- Retain source system identifiers for traceability.

### 2.3 Data Warehouse Design

- Develop an integrated enterprise logical data model.
- Design physical database structures.
- Define data types, constraints and indexes.
- Support historical data tracking.
- Develop dimensional models for analytical reporting.

### 2.4 Data Quality and Validation

- Define data quality rules.
- Validate primary and foreign key relationships.
- Identify duplicate and missing records.
- Define data reconciliation scenarios.
- Validate consistency between source and target structures.

## 3. In-Scope Activities

The following activities are included in this project.

### 3.1 Business Requirements Analysis

- Identify business requirements across insurance domains.
- Document business rules and assumptions.
- Identify reporting and analytical requirements.
- Establish entity-level business definitions.

### 3.2 Source System Analysis

- Identify hypothetical source applications.
- Prepare source system inventory.
- Identify source tables and attributes.
- Document source data definitions.
- Identify potential source-to-target relationships.

### 3.3 Conceptual Data Modelling

- Identify major business entities.
- Define high-level business relationships.
- Establish entity definitions.
- Represent the enterprise business view.

### 3.4 Logical Data Modelling

- Define detailed entities and attributes.
- Identify primary and foreign keys.
- Define relationship cardinality and optionality.
- Apply normalisation principles.
- Define business keys and alternate keys.
- Document data integrity rules.
- Resolve appropriate many-to-many relationships.

### 3.5 Physical Data Modelling

- Convert logical entities into physical tables.
- Define PostgreSQL data types.
- Define primary key and foreign key constraints.
- Define indexes and database constraints.
- Establish physical naming conventions.
- Generate SQL DDL scripts.

### 3.6 Dimensional Modelling

- Identify analytical business processes.
- Define fact table grain.
- Design fact and dimension tables.
- Apply Star Schema modelling where appropriate.
- Define surrogate keys.
- Design Slowly Changing Dimensions (SCD).
- Document measures, dimensions and hierarchies.

### 3.7 Source-to-Target Mapping

- Map source attributes to target attributes.
- Define transformation logic.
- Document data type conversions.
- Define default and derived values.
- Document data lineage and mapping dependencies.

### 3.8 Database Implementation

- Create PostgreSQL schemas.
- Implement tables and relationships.
- Execute database DDL scripts.
- Load synthetic sample data.
- Validate database structures.

### 3.9 Testing and Validation

- Validate primary and foreign key constraints.
- Perform referential integrity checks.
- Validate mandatory attributes.
- Identify duplicate records.
- Perform source-to-target reconciliation scenarios.
- Document test execution results.

### 3.10 Architecture Documentation

- Create enterprise data architecture diagrams.
- Document data flow between layers.
- Illustrate source-to-target integration.
- Document the proposed warehouse architecture.

## 4. Business Domains Covered

| Business Domain | Scope |
|---|---|
| Customer Management | Customer profiles, addresses, contact information and documents |
| Product Management | Insurance products, product categories and coverage types |
| Policy Management | Policy details, holders, coverage, endorsements and renewals |
| Premium Management | Premium schedules, invoices and adjustments |
| Payment Management | Payment transactions, allocations and refunds |
| Claims Management | Claim registration, assessment, status and settlement |
| Agent Management | Agents, brokers, branches and licensing |
| Beneficiary Management | Beneficiaries and nominees associated with policies |

## 5. Out-of-Scope Activities

The following activities are excluded from the current project.

| Excluded Area | Reason |
|---|---|
| Actual insurance company integration | No real organisation or source environment is available |
| Production data migration | Only synthetic data will be used |
| Live API integration | Not required for the modelling portfolio |
| Real-time payment processing | Payment processing application development is excluded |
| Insurance underwriting engine | Underwriting business application implementation is excluded |
| Automated claim adjudication | Claim decision engine development is excluded |
| Customer-facing web/mobile application | Application development is not part of the project |
| Production cloud deployment | Infrastructure provisioning and production deployment are excluded |
| Regulatory certification | Formal legal and regulatory compliance certification is excluded |
| Enterprise-wide production ETL deployment | Actual production ETL orchestration is excluded |

## 6. Expected Project Deliverables

| Phase | Deliverable | Description |
|---|---|---|
| Project Initiation | Project Charter | Project purpose, background and approach |
| Requirements | Business Requirements Document | Business requirements and rules |
| Requirements | Assumptions and Design Decisions | Documented design assumptions |
| Source Analysis | Source System Inventory | Hypothetical source applications and structures |
| Conceptual Modelling | Conceptual Data Model | High-level enterprise entities |
| Conceptual Modelling | Entity Definitions | Business definitions of entities |
| Logical Modelling | Logical Data Model | Detailed attributes and relationships |
| Logical Modelling | Data Dictionary | Attribute definitions and metadata |
| Physical Modelling | Physical Data Model | PostgreSQL table structures |
| Physical Modelling | DDL Scripts | SQL database creation scripts |
| Dimensional Modelling | Dimensional Data Model | Fact and dimension structures |
| Dimensional Modelling | Star Schema Diagrams | Analytical model diagrams |
| Data Integration | Source-to-Target Mapping | Attribute-level mappings and transformations |
| Implementation | Synthetic Sample Data | Fictional test datasets |
| Testing | Data Quality Rules | Data quality validation requirements |
| Testing | Test Execution Results | Evidence of validation activities |
| Architecture | Enterprise Data Architecture | Proposed architecture diagrams |

## 7. Proposed Data Warehouse Layers

The project will use the following logical layers:

| Layer | Purpose |
|---|---|
| Source Layer | Operational insurance systems |
| Staging Layer | Initial source data landing |
| Integration Layer | Cleansing, standardisation and integration |
| Enterprise Data Warehouse Layer | Integrated enterprise data structures |
| Dimensional Layer | Fact and dimension models |
| Presentation Layer | Reporting and analytics |

The layers represent the proposed design. Their implementation as separate physical platforms is not mandatory for this portfolio project.

## 8. Technical Scope

### Data Modelling
- ERwin Data Modeler
- Conceptual, Logical and Physical modelling
- Dimensional modelling
- Naming conventions and modelling standards

### Database
- PostgreSQL
- SQL DDL and DML
- Constraints and indexes
- Data validation queries

### Documentation and Version Control
- Markdown
- Microsoft Excel
- Draw.io
- Git and GitHub

## 9. Key Constraints

- The project uses hypothetical business requirements.
- Actual source system metadata is unavailable.
- Sample data must be synthetic.
- Modelling decisions must be documented with clear justifications.
- The database implementation is intended for demonstration, not production deployment.
- The final design may evolve as detailed requirements and modelling decisions are developed.

## 10. Project Completion Criteria

The project scope will be considered fulfilled when:

1. All identified business domains have been modelled.
2. CDM, LDM and PDM deliverables are completed.
3. Relationships, cardinalities and key constraints are documented.
4. Dimensional models have documented fact table grains.
5. Source-to-target mappings and transformation rules are prepared.
6. PostgreSQL database structures are created successfully.
7. Synthetic data is loaded for demonstration.
8. Data quality and validation scenarios are executed.
9. Architecture diagrams and technical documentation are available.
10. All final deliverables are organised and maintained in GitHub.

## 11. Scope Change Management

Any significant change to the project scope, such as adding a new insurance business domain, additional source systems or new analytical requirements, will be documented in the project assumptions and design decisions.

Changes will be assessed for their impact on:

- Business requirements
- Enterprise data model
- Database design
- Source-to-target mappings
- Dimensional models
- Testing and validation

The relevant project documents will be updated to maintain consistency.

---

**End of Document**
