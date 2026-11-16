# Functional Requirements
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Functional Requirements |
| Document Version | 1.0 |
| Document Status | Draft – Assumed Requirements |
| Related Document | Business Requirements Document |
| Target Database | PostgreSQL |

---

## 1. Purpose

This document defines the functional requirements for the proposed Insurance Enterprise Data Warehouse.

Functional requirements describe the capabilities and data processing activities that the solution must support to satisfy business requirements.

These requirements will guide:

- Data model design.
- Source system integration.
- Data transformation.
- Historical data management.
- Dimensional modelling.
- Database implementation.
- Data quality and validation.

## 2. Requirement Priority

The following priority classification is used:

| Priority | Description |
|---|---|
| High | Essential requirement for the proposed EDW |
| Medium | Important requirement that supports business analysis |
| Low | Additional capability that can be considered in a future enhancement |

## 3. Customer Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-001 | The EDW shall maintain a consolidated customer record using a unique enterprise customer identifier. | High |
| FR-002 | The EDW shall store customer attributes such as customer name, customer type, date of birth or incorporation date, and relevant identification details. | High |
| FR-003 | The EDW shall maintain multiple addresses associated with a customer, including address type and effective dates where available. | Medium |
| FR-004 | The EDW shall maintain multiple customer contact details, including email addresses and phone numbers. | Medium |
| FR-005 | The EDW shall retain original customer identifiers from contributing source systems for traceability. | High |
| FR-006 | The EDW shall support historical tracking of selected customer attribute changes. | Medium |

## 4. Product Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-007 | The EDW shall maintain insurance product information with a unique product identifier. | High |
| FR-008 | The EDW shall classify insurance products into categories such as Life, Health and Motor. | High |
| FR-009 | The EDW shall maintain coverage types associated with insurance products. | High |
| FR-010 | The EDW shall support the association of multiple coverage types with multiple insurance products through an appropriate relationship structure. | High |
| FR-011 | The EDW shall maintain product versions and their effective dates where available. | Medium |
| FR-012 | The EDW shall maintain product status information to distinguish active and inactive products. | Medium |

## 5. Policy Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-013 | The EDW shall maintain policy information using a unique policy number. | High |
| FR-014 | The EDW shall associate each policy with the relevant insurance product and product version. | High |
| FR-015 | The EDW shall support the association of multiple customers with a policy through policyholder relationship records where applicable. | High |
| FR-016 | The EDW shall maintain policy coverage details, including coverage type and applicable coverage amounts or limits where available. | High |
| FR-017 | The EDW shall maintain policy effective start date, expiry date and policy status. | High |
| FR-018 | The EDW shall maintain policy renewal information and allow renewal history to be analysed. | Medium |
| FR-019 | The EDW shall maintain policy endorsement and revision information with relevant effective dates. | Medium |
| FR-020 | The EDW shall support historical tracking of policy status changes. | Medium |
| FR-021 | The EDW shall maintain beneficiary and nominee associations for applicable policies. | Medium |

## 6. Premium and Billing Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-022 | The EDW shall maintain premium invoice information associated with the relevant insurance policy. | High |
| FR-023 | The EDW shall store invoice number, invoice date, due date, invoice amount, currency and invoice status. | High |
| FR-024 | The EDW shall support multiple premium invoices associated with a single policy. | High |
| FR-025 | The EDW shall maintain premium schedules for single-payment and instalment-based billing arrangements. | Medium |
| FR-026 | The EDW shall maintain premium adjustments with traceability to the affected policy or invoice. | Medium |
| FR-027 | The EDW shall support the analysis of billed premium, allocated payments and outstanding premium. | High |

## 7. Payment Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-028 | The EDW shall maintain payment transactions using unique source transaction references. | High |
| FR-029 | The EDW shall store payment transaction date, amount, currency and payment status. | High |
| FR-030 | The EDW shall support payment allocation records linking payment transactions to premium invoices. | High |
| FR-031 | The EDW shall support partial payments and multiple payment allocations against an invoice. | High |
| FR-032 | The EDW shall distinguish successful, failed, pending and refunded payment transactions. | High |
| FR-033 | The EDW shall maintain refund information and its association with the original payment transaction where available. | Medium |
| FR-034 | The EDW shall support payment reconciliation between payment transactions and invoice allocations. | High |

## 8. Claims Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-035 | The EDW shall maintain claim information using a unique claim identifier. | High |
| FR-036 | The EDW shall associate each claim with the relevant insurance policy. | High |
| FR-037 | The EDW shall maintain claim registration date, incident date, claim amount and claim status where available. | High |
| FR-038 | The EDW shall maintain claim status history to support analysis of claim lifecycle changes. | Medium |
| FR-039 | The EDW shall maintain claim assessment information and assessed amounts. | Medium |
| FR-040 | The EDW shall maintain claim settlement information, including settlement amount and settlement date. | High |
| FR-041 | The EDW shall support claims analysis by customer, policy, product, status and reporting period. | High |

## 9. Agent and Branch Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-042 | The EDW shall maintain agent information using a unique agent identifier. | Medium |
| FR-043 | The EDW shall maintain broker information and relevant broker identifiers. | Medium |
| FR-044 | The EDW shall maintain branch details and associate agents with relevant branches. | Medium |
| FR-045 | The EDW shall associate policies with the relevant selling or servicing agent where source information is available. | Medium |
| FR-046 | The EDW shall retain agent and branch assignment history where required for historical reporting. | Low |

## 10. Data Integration Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-047 | The EDW design shall support integration of data from the seven identified hypothetical source systems. | High |
| FR-048 | The integration design shall retain source system identifiers and source record references. | High |
| FR-049 | The solution shall support standardisation of common attributes such as dates, statuses, identifiers and currencies. | High |
| FR-050 | The solution shall define source-to-target mappings for attributes included in the integrated data model. | High |
| FR-051 | The solution shall document transformation logic for derived, defaulted and standardised attributes. | High |
| FR-052 | The solution shall support identification and handling of duplicate source records using documented matching rules. | Medium |
| FR-053 | The solution shall maintain appropriate data lineage and audit metadata for integrated records. | Medium |

## 11. Historical Data Management Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-054 | The data model shall support historical tracking of selected customer attributes. | Medium |
| FR-055 | The data model shall support historical tracking of selected product and coverage changes. | Medium |
| FR-056 | The data model shall support policy status and endorsement history. | High |
| FR-057 | The dimensional model shall support the selected Slowly Changing Dimension strategy for applicable dimensions. | Medium |
| FR-058 | Historical records shall retain appropriate effective dates and, where required, end dates. | Medium |

## 12. Data Quality and Validation Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-059 | The solution shall identify records with missing mandatory business attributes. | High |
| FR-060 | The solution shall identify duplicate business identifiers based on defined uniqueness rules. | High |
| FR-061 | The solution shall validate primary key and foreign key relationships. | High |
| FR-062 | The solution shall identify invalid date ranges, including expiry dates earlier than effective start dates. | Medium |
| FR-063 | The solution shall validate payment allocation amounts against the relevant transaction and invoice amounts according to documented business rules. | High |
| FR-064 | The solution shall support source-to-target record count and amount reconciliation scenarios. | High |
| FR-065 | The solution shall document validation results and data quality exceptions. | High |

## 13. Dimensional Modelling and Reporting Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-066 | The dimensional model shall support customer, product, policy, agent, branch and date analysis. | High |
| FR-067 | The solution shall define fact table grain before identifying fact table measures and dimensions. | High |
| FR-068 | The dimensional model shall support premium billing and collection analysis. | High |
| FR-069 | The dimensional model shall support claims and settlement analysis. | High |
| FR-070 | The dimensional model shall support policy and renewal analysis. | High |
| FR-071 | The solution shall support historical reporting using appropriate date dimensions and historical dimension records. | Medium |
| FR-072 | The dimensional model shall document measures, dimensions, keys and relevant hierarchies. | High |

## 14. Technical and Database Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-073 | The physical database design shall be compatible with PostgreSQL. | High |
| FR-074 | Physical tables shall have appropriately defined primary keys and foreign keys. | High |
| FR-075 | Physical columns shall have suitable data types, lengths, precision and nullability. | High |
| FR-076 | The database design shall include appropriate constraints to maintain data integrity. | High |
| FR-077 | SQL scripts shall be provided to create the required schemas, tables, constraints and indexes. | High |
| FR-078 | The project shall use synthetic datasets to demonstrate database implementation and validation. | High |

---

## 15. Functional Requirement Traceability

Functional requirements will be linked to the corresponding business requirements, business rules and data model objects.

The following is the proposed traceability structure:

| Functional Area | Example Requirement | Related Data Model Objects |
|---|---|---|
| Customer | FR-001 | CUSTOMER |
| Customer Address | FR-003 | CUSTOMER_ADDRESS |
| Product | FR-007 | INSURANCE_PRODUCT |
| Product Coverage | FR-010 | PRODUCT_COVERAGE, COVERAGE_TYPE |
| Policy | FR-013 | POLICY |
| Policyholder | FR-015 | POLICY_HOLDER |
| Policy Coverage | FR-016 | POLICY_COVERAGE |
| Premium | FR-022 | PREMIUM_INVOICE |
| Payment | FR-028 | PAYMENT_TRANSACTION |
| Payment Allocation | FR-030 | PAYMENT_ALLOCATION |
| Claims | FR-035 | CLAIM |
| Claim Assessment | FR-039 | CLAIM_ASSESSMENT |
| Claim Settlement | FR-040 | CLAIM_SETTLEMENT |
| Agent | FR-042 | AGENT |
| Branch | FR-044 | BRANCH |

The traceability matrix will be expanded as the CDM, LDM, PDM and source-to-target mapping documents are developed.

## 16. Acceptance Criteria

The functional requirements will be considered addressed when:

1. Each requirement has a unique identifier.
2. Required business entities and attributes are represented in the data models.
3. Relationships and data integrity rules are documented.
4. Source-to-target mappings are available for identified source attributes.
5. Historical data requirements are addressed in the appropriate models.
6. PostgreSQL structures are created for the agreed physical model.
7. Synthetic data is available for demonstration.
8. Validation scenarios are documented and executed.
9. Requirement traceability is maintained across project deliverables.

## 17. Assumptions and Limitations

- Requirements are hypothetical and intended for portfolio demonstration.
- Actual operational source systems are not available.
- Data integration and transformation logic will be designed but not deployed in a production environment.
- Reporting requirements describe analytical capabilities rather than fully developed production dashboards.
- Business rules may be refined as detailed modelling progresses.
- Functional requirements will be updated when modelling decisions are finalised.

---

**End of Document**
