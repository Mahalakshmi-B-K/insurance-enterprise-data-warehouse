# Project Charter
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Project Charter |
| Document Version | 1.0 |
| Document Status | Approved for Portfolio Design |
| Project Type | Enterprise Data Modelling and Data Warehouse Design |
| Prepared By | Independent Data Modelling Portfolio Project |
| Target Database | PostgreSQL |
| Data Modelling Tool | ERwin Data Modeler |

---

## 1. Project Background

SecureLife Insurance Ltd. is a fictional insurance organisation offering Life, Health and Motor insurance products.

The organisation operates multiple business applications to manage customer information, insurance policies, premium billing, payment transactions, claims processing, agent details and insurance products.

As business operations expand, information distributed across these applications can create challenges in data integration, reporting consistency, data quality and enterprise-level analysis.

To address these challenges, this project proposes the design of an Enterprise Data Warehouse (EDW) that consolidates information from multiple operational systems into a centralised and integrated data environment.

The project focuses on enterprise data modelling, data architecture design, database structures and analytical data models.

## 2. Project Purpose

The purpose of this project is to demonstrate the design and development of an enterprise-level insurance data warehouse using industry-standard data modelling practices.

The project will establish a structured data foundation to support:

- Unified customer and policy information.
- Insurance premium and payment analysis.
- Claims and settlement reporting.
- Product and agent performance analysis.
- Historical data tracking.
- Enterprise reporting and business intelligence.

## 3. Project Vision

To design a scalable, integrated and well-governed enterprise data model that provides a consistent view of insurance business information across multiple operational domains.

## 4. Business Objectives

The primary objectives are:

1. Consolidate insurance business information from multiple hypothetical operational systems.
2. Establish a common enterprise data structure across business domains.
3. Develop Conceptual, Logical and Physical Data Models.
4. Define standardised business entities, attributes, relationships and constraints.
5. Implement dimensional models to support analytical reporting.
6. Establish source-to-target mappings and transformation rules.
7. Implement the physical database design using PostgreSQL.
8. Define data quality, referential integrity and reconciliation checks.
9. Document data lineage, modelling standards and design decisions.

## 5. Project Scope Summary

The project covers the design of an enterprise data warehouse for the following business domains:

- Customer Management
- Product Management
- Policy Administration
- Premium and Billing
- Payment Processing
- Claims Management
- Agent and Broker Management
- Beneficiary and Nominee Management

The proposed solution includes conceptual, logical, physical and dimensional data modelling, together with database implementation and validation documentation.

Detailed scope boundaries are maintained in the accompanying Project Scope and Objectives document.

## 6. Proposed Source Systems

The project assumes integration from the following fictional operational systems:

| Source ID | Source System | Business Purpose |
|---|---|---|
| SRC-001 | Customer Relationship Management (CRM) | Customer information and contact details |
| SRC-002 | Policy Administration System (PAS) | Policy creation, coverage and renewals |
| SRC-003 | Claims Management System (CMS) | Claim registration, assessment and settlement |
| SRC-004 | Premium Billing System (PBS) | Premium schedules, invoices and adjustments |
| SRC-005 | Payment Processing System (PPS) | Payment transactions, allocations and refunds |
| SRC-006 | Agent Management System (AMS) | Agent, broker and branch information |
| SRC-007 | Product Management System (PMS) | Insurance products and coverage definitions |

These source systems are hypothetical and are created for the purpose of this portfolio project.

## 7. Proposed Solution Architecture

The proposed architecture follows a layered enterprise data warehouse approach:

1. Source Systems
2. Data Ingestion and Staging Layer
3. Data Cleansing and Integration Layer
4. Enterprise Data Warehouse Layer
5. Dimensional Data Mart Layer
6. Reporting and Analytics Layer

The architecture will be documented using logical architecture diagrams.

Actual production infrastructure, live integrations and automated deployment are outside the current project scope.

## 8. Project Methodology

The project will follow a structured data modelling and warehouse design lifecycle.

| Phase | Activities | Expected Deliverables |
|---|---|---|
| 1. Project Initiation | Define project purpose, objectives and scope | Project Charter |
| 2. Requirements Analysis | Identify business requirements and rules | BRD and Business Rules |
| 3. Source Analysis | Identify source systems, tables and attributes | Source Inventory |
| 4. Conceptual Modelling | Identify business entities and relationships | CDM |
| 5. Logical Modelling | Define attributes, keys and relationships | LDM |
| 6. Physical Modelling | Define database tables, columns and constraints | PDM |
| 7. Dimensional Modelling | Design facts, dimensions and historical tracking | Dimensional Model |
| 8. Source-to-Target Mapping | Define source mappings and transformations | Mapping Document |
| 9. Database Implementation | Generate and execute SQL scripts | PostgreSQL Structures |
| 10. Testing and Validation | Perform data quality and integrity checks | Test Results |

## 9. Tools and Technologies

| Tool / Technology | Usage |
|---|---|
| ERwin Data Modeler | Enterprise data modelling |
| PostgreSQL | Target database |
| DBeaver | Database development and SQL execution |
| SQL | Database implementation and validation |
| Draw.io | Architecture diagrams |
| Microsoft Excel | Data dictionaries, inventories and mappings |
| Git | Version control |
| GitHub | Project documentation and portfolio hosting |
| Power BI (Optional) | Analytical reporting demonstration |

## 10. Key Stakeholders and Responsibilities

The following are proposed project roles, not actual assigned individuals.

| Stakeholder | Responsibility |
|---|---|
| Business Stakeholders | Define business needs and reporting requirements |
| Business Analyst | Document business requirements and rules |
| Data Architect | Define enterprise data architecture and integration approach |
| Senior Data Modeller | Design CDM, LDM and PDM |
| ETL/Data Engineer | Implement data ingestion and transformation logic |
| Database Developer | Implement physical database structures |
| BI Developer | Develop analytical reporting models and dashboards |
| Data Quality Analyst | Define and validate data quality rules |

## 11. Key Assumptions

- All source systems and business requirements are hypothetical.
- Synthetic data will be used for demonstration.
- PostgreSQL will be used as the target relational database.
- ERwin Data Modeler will be used for enterprise data modelling.
- The enterprise logical model will generally follow 3NF principles.
- Dimensional models will follow documented business process grain and Star Schema principles where appropriate.
- Historical tracking will be applied where business requirements require it.
- All design decisions will be documented.

## 12. Risks and Constraints

| Risk / Constraint | Mitigation |
|---|---|
| No actual business requirements available | Define and document realistic business assumptions |
| No production source data | Generate synthetic sample datasets |
| Ambiguous business relationships | Document business rules and modelling decisions |
| Changes in requirements | Maintain version-controlled documentation |
| Complex historical data requirements | Define history-tracking rules during logical and dimensional modelling |
| Limited project environment | Use PostgreSQL and locally available modelling tools |

## 13. Success Criteria

The project will be considered successfully completed when:

- All identified business domains are represented in the enterprise data model.
- Conceptual, Logical and Physical Data Models are documented.
- Primary and foreign key relationships are defined.
- Dimensional models and fact table grains are documented.
- Source-to-target mappings are available.
- PostgreSQL database structures are implemented.
- Synthetic data is available for testing.
- Data quality and referential integrity checks are documented and executed.
- Architecture and modelling decisions are maintained in GitHub.

## 14. Project Approval

This document establishes the proposed direction and boundaries of the independent portfolio project.

Since SecureLife Insurance Ltd. is fictional, formal organisational approval is not applicable.

**Document Status:** Approved for Portfolio Design

---

**End of Document**
