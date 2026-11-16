# Insurance Enterprise Data Warehouse (EDW)

**A Real-World-Inspired Enterprise Data Modelling Portfolio Project**

## 1. Project Overview

This project focuses on designing an Enterprise Data Warehouse (EDW) for a fictional insurance company, **SecureLife Insurance Ltd.**, offering Life, Health and Motor insurance products.

The objective is to design an integrated enterprise data architecture that consolidates information from multiple operational source systems into a centralised data warehouse to support business reporting, analytics and informed decision-making.

The project demonstrates the end-to-end data modelling lifecycle, including conceptual, logical, physical and dimensional data modelling, source-to-target mapping, database implementation and data validation.

All business requirements, company details, source systems and sample data used in this project are fictional or assumed for portfolio demonstration purposes.

## 2. Business Problem

Insurance companies typically maintain customer, policy, premium, payment and claims information across multiple operational systems.

This can result in:

- Customer information being distributed across different systems.
- Difficulty obtaining a consolidated view of policies and claims.
- Inconsistent data definitions and business rules.
- Challenges in tracking premium collections and outstanding payments.
- Limited visibility into insurance business performance.

The proposed EDW aims to address these challenges by creating a unified and integrated data foundation.

## 3. Project Objectives

- Design an enterprise-level data model for the insurance business.
- Identify and document business entities, attributes and relationships.
- Develop Conceptual, Logical and Physical Data Models.
- Design an analytical data model using dimensional modelling techniques.
- Define source-to-target mappings and transformation rules.
- Implement the physical database structure using PostgreSQL.
- Develop data quality checks and validation scenarios.
- Document enterprise data architecture and modelling decisions.

## 4. Business Scope

The project covers the following insurance business domains:

| Business Domain | Description |
|---|---|
| Customer Management | Customer profiles, contact details and addresses |
| Product Management | Life, Health and Motor insurance products |
| Policy Management | Policy details, holders, coverage and renewals |
| Premium Management | Premium schedules, invoices and adjustments |
| Payment Management | Payment transactions, allocations and refunds |
| Claims Management | Claim registration, assessment and settlement |
| Agent Management | Agents, brokers and branch information |
| Beneficiary Management | Policy beneficiaries and nominees |

## 5. Proposed Source Systems

The project assumes integration from the following fictional operational systems:

| Source System | Description |
|---|---|
| CRM | Customer Relationship Management |
| PAS | Policy Administration System |
| CMS | Claims Management System |
| PBS | Premium Billing System |
| PPS | Payment Processing System |
| AMS | Agent Management System |
| PMS | Product Management System |

These systems represent hypothetical source applications and are not connected to any actual insurance organisation.

## 6. Proposed Data Architecture

The proposed architecture follows a layered data warehouse approach:

1. **Source Systems:** Operational applications containing insurance business data.
2. **Staging Layer:** Initial landing and storage of extracted source data.
3. **Data Integration Layer:** Data cleansing, standardisation, transformation and integration.
4. **Enterprise Data Warehouse:** Centralised and integrated enterprise data model.
5. **Dimensional Layer:** Analytical structures designed for reporting and business intelligence.
6. **Reporting Layer:** Business reports, dashboards and analytical consumption.

The architecture is a proposed logical design for this portfolio project; it does not represent a deployed production integration pipeline.

## 7. Data Modelling Approach

The project follows a structured data modelling methodology.

### Conceptual Data Model (CDM)
- Identify core business entities.
- Define business relationships.
- Establish the high-level enterprise data structure.

### Logical Data Model (LDM)
- Define entities, attributes and relationships.
- Identify primary keys and foreign keys.
- Apply normalisation principles.
- Define business keys and data integrity rules.

### Physical Data Model (PDM)
- Convert logical entities into database tables.
- Define column data types, constraints and indexes.
- Apply PostgreSQL database design standards.

### Dimensional Data Model
- Identify business processes and fact table grain.
- Design fact and dimension tables.
- Apply Star Schema modelling.
- Define historical tracking requirements, including Slowly Changing Dimensions (SCD).

## 8. Technology Stack

| Tool / Technology | Purpose |
|---|---|
| ERwin Data Modeler | Conceptual, Logical and Physical Data Modelling |
| PostgreSQL | Target relational database |
| DBeaver | Database development and SQL execution |
| SQL | DDL, DML and data validation |
| Draw.io | Data architecture diagrams |
| Git | Version control |
| GitHub | Project repository and documentation |
| Power BI (Optional) | Reporting and dashboard demonstration |

## 9. Repository Structure

The repository is organised according to the project lifecycle.

```text
insurance-enterprise-data-warehouse/
│
├── README.md
│
├── 01_Project_Charter/
│   └── Project_Charter.md
│
├── 02_Business_Requirements/
│   └── Business_Requirements_Document.md
│
├── 03_Assumptions/
│   └── Assumptions_and_Design_Decisions.md
│
├── 04_Source_System_Inventory/
│   └── Source_System_Inventory.md
│
├── 05_Conceptual_Data_Model/
│
├── 06_Logical_Data_Model/
│
├── 07_Physical_Data_Model/
│
├── 08_Dimensional_Model/
│
├── 09_Source_To_Target_Mapping/
│
├── 10_SQL_Scripts/
│
├── 11_Sample_Data/
│
├── 12_Testing_Validation/
│
└── 13_Architecture_Diagrams/
```

## 10. Project Deliverables

The planned project deliverables include:

- Project Charter
- Business Requirements Document (BRD)
- Assumptions and Design Decisions
- Source System Inventory
- Conceptual Data Model (CDM)
- Logical Data Model (LDM)
- Physical Data Model (PDM)
- Dimensional Data Model
- Source-to-Target Mapping Document
- Database DDL and SQL Scripts
- Synthetic Sample Data
- Data Quality and Validation Scenarios
- Enterprise Data Architecture Diagrams

## 11. Project Status

| Project Phase | Status |
|---|---|
| Project Initiation | Completed |
| Business Requirements | Drafted |
| Assumptions and Design Decisions | Drafted |
| Source System Inventory | Drafted |
| Conceptual Data Modelling | Pending |
| Logical Data Modelling | Pending |
| Physical Data Modelling | Pending |
| Dimensional Modelling | Pending |
| Source-to-Target Mapping | Pending |
| SQL Implementation | Pending |
| Data Validation | Pending |
| Architecture Documentation | Pending |

*Project status will be updated as each phase is completed.*

## 12. Disclaimer

This is an independent data modelling portfolio project created for learning and professional demonstration purposes.

SecureLife Insurance Ltd. is a fictional organisation. All business requirements, source systems, data structures, business rules and sample datasets are hypothetical or synthetic.

No confidential information, proprietary data models or intellectual property from any employer or client has been used.
