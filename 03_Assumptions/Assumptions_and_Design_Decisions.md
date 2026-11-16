# Assumptions and Design Decisions
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Assumptions and Design Decisions |
| Document Version | 1.0 |
| Document Status | Draft – Proposed Design |
| Related Documents | BRD, Business Rules, Functional Requirements |
| Data Modelling Tool | ERwin Data Modeler |
| Target Database | PostgreSQL |

---

## 1. Purpose

This document records the assumptions and design decisions made during the design of the proposed Insurance Enterprise Data Warehouse.

Since actual business requirements, source system metadata and production data are not available, the project uses realistic hypothetical business scenarios and synthetic data.

The assumptions provide a consistent foundation for enterprise data modelling, while the design decisions explain how the proposed solution will address identified business requirements.

This document will be updated as the Conceptual, Logical, Physical and Dimensional Data Models are developed.

## 2. Scope of Assumptions

The assumptions cover the following areas:

- Business and organisational assumptions.
- Customer and policy management.
- Product and coverage management.
- Premium and payment processing.
- Claims management.
- Agent and branch management.
- Source system integration.
- Enterprise data modelling.
- Historical data management.
- Dimensional modelling.
- Database and technical design.
- Data quality and validation.

## 3. Business and Organisational Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-001 | SecureLife Insurance Ltd. is a fictional organisation created for this portfolio project. | All company-specific business requirements and structures are hypothetical. |
| ASM-002 | The organisation offers Life, Health and Motor insurance products. | The enterprise model must support all three insurance business categories. |
| ASM-003 | The organisation operates multiple independent operational applications. | The EDW must support integration of data from multiple source systems. |
| ASM-004 | The business requires consolidated reporting across insurance domains. | Common enterprise entities and identifiers will be established. |
| ASM-005 | Business requirements are assumed and have not been validated through actual stakeholder interviews. | Requirements may be refined as modelling progresses. |
| ASM-006 | Synthetic data will be used for database implementation and testing. | No production or confidential data will be included in the repository. |

## 4. Customer Management Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-007 | Each customer will have a unique enterprise customer identifier. | CUSTOMER will have an enterprise primary key. |
| ASM-008 | A customer may hold multiple insurance policies. | CUSTOMER and POLICY will have a one-to-many relationship through the policyholder association. |
| ASM-009 | A policy may have multiple policyholders, where applicable. | POLICY_HOLDER will be modelled as an associative entity between CUSTOMER and POLICY. |
| ASM-010 | Customer information may originate from multiple source systems. | Source system identifiers and source references will be retained. |
| ASM-011 | A customer may maintain multiple addresses and contact details. | CUSTOMER_ADDRESS and CUSTOMER_CONTACT will be modelled separately. |
| ASM-012 | Customer profile changes may need to be historically tracked. | Appropriate effective dates and history-tracking mechanisms will be considered. |
| ASM-013 | A customer and an insured person may be different individuals. | CUSTOMER and INSURED_PARTY roles will be evaluated during conceptual and logical modelling. |

## 5. Product and Coverage Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-014 | Each insurance product will have a unique product identifier. | INSURANCE_PRODUCT will have a unique business key. |
| ASM-015 | Products will be classified under Life, Health or Motor categories. | PRODUCT_CATEGORY will be modelled as a separate reference entity. |
| ASM-016 | A product may offer multiple coverage types. | PRODUCT_COVERAGE will resolve the many-to-many product and coverage relationship. |
| ASM-017 | A coverage type may be offered under multiple products. | Coverage definitions will be maintained independently of products. |
| ASM-018 | Product definitions and coverage availability may change over time. | PRODUCT_VERSION or an equivalent effective-dated structure will be considered. |
| ASM-019 | Different insurance categories may require different attributes. | Common product attributes will be separated from product-specific details where justified by requirements. |

## 6. Policy Management Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-020 | Every policy will have a unique policy number within the defined business key scope. | POLICY_NUMBER will be documented as a business key. |
| ASM-021 | Every policy must be associated with one insurance product. | POLICY will reference INSURANCE_PRODUCT or the applicable product version. |
| ASM-022 | A policy may contain multiple coverage records. | POLICY_COVERAGE will associate policies with applicable coverage definitions. |
| ASM-023 | A policy may undergo multiple renewals. | Policy renewal information will be maintained separately or through a suitable history structure. |
| ASM-024 | A policy may undergo multiple endorsements or revisions. | POLICY_ENDORSEMENT will capture endorsement details. |
| ASM-025 | Policy status may change during its lifecycle. | Policy status history will be maintained for historical analysis. |
| ASM-026 | A policy may have multiple beneficiaries or nominees, where applicable. | POLICY_BENEFICIARY and POLICY_NOMINEE associations will be considered. |
| ASM-027 | A policy may cover multiple insured persons or assets, depending on the product. | Separate insured-party and insured-asset relationships will be evaluated before finalising the LDM. |

## 7. Premium and Billing Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-028 | A policy may generate multiple premium invoices during its lifetime. | POLICY and PREMIUM_INVOICE will have a one-to-many relationship. |
| ASM-029 | Premiums may be billed as a single payment or through instalments. | PREMIUM_SCHEDULE will maintain instalment information where applicable. |
| ASM-030 | Premium invoices may be adjusted after initial creation. | PREMIUM_ADJUSTMENT will capture adjustment details. |
| ASM-031 | Outstanding premium will be derived from invoice amounts, adjustments and valid payment allocations. | Derived financial measures will use documented calculation rules. |
| ASM-032 | All financial amounts must retain their applicable currency. | Currency codes will be captured for relevant financial transactions. |

## 8. Payment Management Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-033 | A customer may make multiple payment transactions. | CUSTOMER and PAYMENT_TRANSACTION may have a one-to-many relationship where customer attribution is available. |
| ASM-034 | A payment may be allocated against multiple premium invoices. | PAYMENT_ALLOCATION will be used as an associative entity. |
| ASM-035 | A premium invoice may receive payments from multiple transactions. | PAYMENT_ALLOCATION will support multiple allocations per invoice. |
| ASM-036 | Payment transactions may have successful, failed, pending or refunded statuses. | Payment status will be standardised using a reference structure or controlled values. |
| ASM-037 | Refunds must be traceable to original payment transactions where available. | PAYMENT_REFUND will maintain the original transaction reference. |
| ASM-038 | Payment transactions and invoice allocations may be recorded in different source systems. | Source identifiers and reconciliation attributes will be retained. |

## 9. Claims Management Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-039 | A policy may have multiple claims during its lifetime. | POLICY and CLAIM will have a one-to-many relationship. |
| ASM-040 | Each claim must be associated with a valid policy. | CLAIM will reference POLICY. |
| ASM-041 | A claim may pass through multiple statuses. | CLAIM_STATUS_HISTORY will capture status changes. |
| ASM-042 | A claim may have multiple assessment records. | CLAIM_ASSESSMENT will be designed as a separate entity. |
| ASM-043 | A claim may have one or more settlement transactions. | CLAIM_SETTLEMENT will support settlement history and partial settlements if required. |
| ASM-044 | Claim amounts and settlement amounts may be different. | Separate attributes and measures will be maintained. |

## 10. Agent and Branch Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-045 | Each agent will have a unique agent identifier. | AGENT will have a unique business key. |
| ASM-046 | An agent may be assigned to different branches over time. | AGENT_BRANCH or an equivalent effective-dated association will be considered. |
| ASM-047 | A branch may have multiple agents. | Branch-to-agent relationships will support multiple assignments. |
| ASM-048 | A policy may be associated with a selling or servicing agent. | Policy-agent association will be modelled where the business requirement supports it. |
| ASM-049 | Agent and broker information may originate from separate source systems. | Separate source identifiers and entity relationships will be retained. |

## 11. Source System and Integration Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-050 | Seven hypothetical source systems will contribute data to the EDW. | Source inventory will identify each contributing application. |
| ASM-051 | Source systems may use different identifiers for the same business entity. | Enterprise identifiers and source-system cross-reference structures will be considered. |
| ASM-052 | Source systems may use different naming conventions and data formats. | Standardisation and transformation rules will be documented. |
| ASM-053 | Source records may contain duplicates or incomplete information. | Data quality and record matching rules will be defined. |
| ASM-054 | Each integrated record should retain appropriate source lineage. | Source system code, source record ID and audit metadata will be considered. |
| ASM-055 | The proposed integration will use a staging and integration approach. | The architecture will include logical staging and integration layers. |
| ASM-056 | Actual source extracts and source metadata are unavailable. | Source table structures and attributes are assumed for modelling purposes. |

## 12. Enterprise Data Modelling Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-057 | The enterprise logical data model will generally follow Third Normal Form (3NF). | Redundant data and unnecessary update dependencies will be minimised. |
| ASM-058 | Each major business entity will have an appropriate primary key. | Entity identity and relationship integrity will be established. |
| ASM-059 | Business identifiers will be distinguished from technical primary keys. | Business keys and surrogate or generated primary keys will be documented separately. |
| ASM-060 | Many-to-many relationships will be resolved using associative entities where appropriate. | Entities such as POLICY_HOLDER, POLICY_COVERAGE and PAYMENT_ALLOCATION will be considered. |
| ASM-061 | Reference data such as policy status and payment status will use controlled definitions. | Reference entities or controlled value domains will be introduced where appropriate. |
| ASM-062 | Audit attributes will be maintained for relevant target entities. | Created date, updated date and source metadata will be considered. |
| ASM-063 | Entity and attribute definitions will be documented. | Data dictionaries will be maintained with the models. |

## 13. Historical Data Management Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-064 | Selected business entities require historical tracking. | History requirements will be assessed entity by entity. |
| ASM-065 | Type 1 Slowly Changing Dimensions may be used when historical changes do not need to be preserved. | Selected dimensional attributes may be overwritten. |
| ASM-066 | Type 2 Slowly Changing Dimensions will be used where historical versions are required. | Effective start date, effective end date and current record indicator will be considered. |
| ASM-067 | Transactional events such as payments and claims must retain their event dates. | Transaction history will be represented as separate business events. |
| ASM-068 | Effective dates and transaction dates represent different business concepts. | Separate date attributes will be maintained where applicable. |

## 14. Dimensional Modelling Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-069 | The analytical model will use dimensional modelling principles. | Fact and dimension tables will be designed for reporting. |
| ASM-070 | Fact table grain must be defined before measures and dimensions are finalised. | Each fact table will have a documented grain statement. |
| ASM-071 | Star Schema will be the preferred dimensional structure where appropriate. | Dimensions will be directly associated with relevant fact tables. |
| ASM-072 | Conformed dimensions will be shared across business processes where their definitions are consistent. | Common dimensions such as DATE, CUSTOMER and PRODUCT will be considered. |
| ASM-073 | Surrogate keys will be used for dimensional entities. | Fact tables will reference dimension surrogate keys. |
| ASM-074 | Transactional and periodic snapshot facts may be required for different reporting needs. | Fact table types will be selected based on business process and reporting requirements. |
| ASM-075 | Measures must have documented aggregation behaviour. | Additive, semi-additive and non-additive measures will be distinguished. |

## 15. Database and Technical Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-076 | PostgreSQL will be the target relational database. | Physical data types and database-specific features will follow PostgreSQL compatibility. |
| ASM-077 | ERwin Data Modeler will be used for CDM, LDM and PDM development. | Models will follow ERwin modelling conventions. |
| ASM-078 | DBeaver will be used for database connectivity and SQL execution. | SQL scripts will be compatible with the selected PostgreSQL version. |
| ASM-079 | SQL scripts will be maintained in GitHub. | Database implementation will be version-controlled. |
| ASM-080 | The project will use locally generated synthetic data. | Test datasets will be documented and contain no real customer information. |
| ASM-081 | Database performance tuning will be demonstrated at a basic design level. | Indexes and appropriate data types will be considered; production benchmarking is excluded. |

## 16. Security and Privacy Assumptions

| Assumption ID | Assumption | Design Impact |
|---|---|---|
| ASM-082 | No actual personally identifiable customer information will be used. | All sample customer data must be synthetic. |
| ASM-083 | Sensitive customer attributes will not be published in the public repository. | Documentation and sample datasets will be reviewed before publication. |
| ASM-084 | The proposed architecture may include role-based access controls as a future implementation consideration. | Security requirements may be documented conceptually but are not a deployed feature. |

---

## 17. Key Design Decisions

The following table summarises the proposed design decisions.

| Decision ID | Design Area | Proposed Decision | Reason |
|---|---|---|---|
| DD-001 | Enterprise Model | Develop an integrated enterprise data model | Establish a consistent business view |
| DD-002 | Logical Model | Follow 3NF principles where appropriate | Reduce unnecessary redundancy |
| DD-003 | Primary Keys | Use stable technical primary keys | Support reliable relationships |
| DD-004 | Business Keys | Retain source and business identifiers | Support traceability and reconciliation |
| DD-005 | Many-to-Many Relationships | Use associative entities | Resolve complex business relationships |
| DD-006 | Historical Tracking | Apply Type 1 or Type 2 based on attribute requirements | Support the required level of history |
| DD-007 | Dimensional Model | Use Star Schema where appropriate | Support analytical querying |
| DD-008 | Fact Table Design | Document grain before selecting measures | Prevent incorrect aggregation |
| DD-009 | Target Database | PostgreSQL | Provide an accessible relational implementation platform |
| DD-010 | Audit Metadata | Include relevant audit and lineage attributes | Support traceability and data quality |
| DD-011 | Data Integration | Retain source system and source record identifiers | Enable source-to-target reconciliation |
| DD-012 | Sample Data | Use synthetic datasets | Protect confidentiality and privacy |

## 18. Items Requiring Further Analysis

The following decisions must be validated or refined during detailed modelling.

| Item | Area | Question to Resolve |
|---|---|---|
| DA-001 | Customer | Can a customer be both a policyholder and an insured person? |
| DA-002 | Policy | Can a policy have joint policyholders? |
| DA-003 | Insurance Coverage | Can one policy cover multiple persons or assets? |
| DA-004 | Premium | Can an invoice be associated with multiple policies? |
| DA-005 | Payment | Can one payment cover invoices belonging to different policies? |
| DA-006 | Payment | How are overpayments and unapplied payments handled? |
| DA-007 | Claims | Can a claim have multiple partial settlements? |
| DA-008 | Product | How are product versions and coverage changes maintained? |
| DA-009 | Policy | How are renewals and endorsements represented? |
| DA-010 | History | Which attributes require Type 2 historical tracking? |
| DA-011 | Agent | Can a policy have multiple agents or brokers? |
| DA-012 | Beneficiary | How are beneficiary allocation percentages validated? |

These items will be addressed through documented design decisions as the project progresses.

## 19. Assumption and Design Decision Governance

- Every assumption must have a unique identifier.
- Design decisions must be documented with a reason.
- Changes to assumptions must be reflected in the relevant data models.
- Any impact on business requirements must be reviewed.
- Assumptions that are no longer valid must be revised or marked as superseded.
- The document version must be updated when significant design decisions change.

---

## 20. Document Status

This document contains proposed assumptions and design decisions for an independent portfolio project.

It does not represent confirmed requirements from a real insurance organisation.

**Current Status:** Draft – Proposed Design

---

**End of Document**
