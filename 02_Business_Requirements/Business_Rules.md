# Business Rules
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Business Rules |
| Document Version | 1.0 |
| Document Status | Draft – Assumed Business Rules |
| Related Document | Business Requirements Document |
| Data Modelling Tool | ERwin Data Modeler |

---

## 1. Purpose

This document defines the business rules governing the insurance business processes covered by the proposed Enterprise Data Warehouse.

Business rules describe the constraints, relationships and operational logic that determine how business data is created, maintained and associated.

These rules will be used as inputs for:

- Conceptual Data Modelling.
- Logical Data Modelling.
- Entity relationship definitions.
- Attribute and key identification.
- Relationship cardinality and optionality.
- Data integrity constraints.
- Source-to-target mapping.
- Data quality and validation scenarios.

All rules in this document are assumed for the fictional SecureLife Insurance Ltd. portfolio project and may be refined during detailed modelling.

## 2. Customer Management Rules

| Rule ID | Business Rule |
|---|---|
| BR-001 | Each customer must have a unique enterprise customer identifier. |
| BR-002 | A customer can hold one or more insurance policies. |
| BR-003 | A policy must have at least one associated policyholder. |
| BR-004 | A customer may have multiple addresses, such as residential and mailing addresses. |
| BR-005 | A customer may maintain multiple contact details, such as phone numbers and email addresses. |
| BR-006 | Customer records received from different source systems must retain their original source identifiers for traceability. |
| BR-007 | Customer information changes should be historically tracked where required by the reporting needs. |

## 3. Insurance Product Rules

| Rule ID | Business Rule |
|---|---|
| BR-008 | Each insurance product must have a unique product identifier. |
| BR-009 | Every insurance product must belong to an insurance product category. |
| BR-010 | An insurance product may offer multiple coverage types. |
| BR-011 | A coverage type may be associated with multiple insurance products. |
| BR-012 | Product definitions and coverage availability may change over time and should support version tracking. |
| BR-013 | A policy must be associated with a valid insurance product. |

## 4. Policy Management Rules

| Rule ID | Business Rule |
|---|---|
| BR-014 | Each insurance policy must have a unique policy number. |
| BR-015 | Every policy must be associated with one insurance product. |
| BR-016 | A policy must have at least one policyholder. |
| BR-017 | A customer may be associated with multiple policies. |
| BR-018 | A policy may contain one or more coverage records. |
| BR-019 | A policy may have multiple beneficiaries or nominees, where applicable. |
| BR-020 | A policy must have a defined effective start date. |
| BR-021 | Where a policy has an expiry date, the expiry date must not be earlier than its effective start date. |
| BR-022 | A policy may undergo multiple renewals during its lifetime. |
| BR-023 | A policy may have multiple endorsements or revisions. |
| BR-024 | Policy status changes should be retained for historical reporting. |
| BR-025 | A policy must be associated with a valid product version applicable under the relevant business rules. |

## 5. Premium and Billing Rules

| Rule ID | Business Rule |
|---|---|
| BR-026 | A policy may have multiple premium invoices during its lifetime. |
| BR-027 | Each premium invoice must have a unique invoice identifier within its defined business key scope. |
| BR-028 | A premium invoice must be associated with a valid policy. |
| BR-029 | A policy may follow a single-payment or instalment-based billing schedule, depending on the product and policy terms. |
| BR-030 | A premium invoice must maintain an invoice amount, issue date and due date. |
| BR-031 | An invoice may be settled through one or more payment allocations. |
| BR-032 | Premium adjustments must be recorded separately or otherwise traceably linked to the affected billing record. |
| BR-033 | Outstanding premium must be calculated using the invoice amount, applicable adjustments and valid payment allocations, subject to the defined accounting rules. |

## 6. Payment Management Rules

| Rule ID | Business Rule |
|---|---|
| BR-034 | Each payment transaction must have a unique transaction reference within its source system. |
| BR-035 | A customer may make multiple payment transactions. |
| BR-036 | A payment transaction may be allocated across multiple premium invoices where permitted. |
| BR-037 | A premium invoice may receive allocations from multiple payment transactions. |
| BR-038 | Payment allocations must retain the relationship between the payment transaction and the premium invoice. |
| BR-039 | Payment transactions must maintain transaction date, amount, currency and status. |
| BR-040 | Failed, pending, successful and refunded transactions must be distinguishable. |
| BR-041 | Refunds must be traceably associated with the original payment transaction where applicable. |

## 7. Claims Management Rules

| Rule ID | Business Rule |
|---|---|
| BR-042 | Each claim must have a unique claim identifier within its defined business key scope. |
| BR-043 | A claim must be associated with a valid insurance policy. |
| BR-044 | A policy may have multiple claims during its lifetime. |
| BR-045 | A claim must maintain a claim registration date. |
| BR-046 | A claim may pass through multiple statuses during its lifecycle. |
| BR-047 | Claim status changes must be retained for historical analysis. |
| BR-048 | A claim may have one or more assessment records, depending on the business process. |
| BR-049 | A claim may have settlement information when a settlement is made. |
| BR-050 | Approved, rejected, pending and settled claims must be distinguishable for reporting. |

## 8. Agent and Branch Management Rules

| Rule ID | Business Rule |
|---|---|
| BR-051 | Each agent must have a unique agent identifier. |
| BR-052 | An agent may be associated with one or more branches over time, subject to assignment history. |
| BR-053 | A branch may have multiple agents. |
| BR-054 | A policy may be associated with a selling or servicing agent where applicable. |
| BR-055 | Agent and branch assignment changes should be retained where historical reporting requires them. |
| BR-056 | Agent licensing information must retain its validity period where applicable. |

## 9. Beneficiary and Nominee Rules

| Rule ID | Business Rule |
|---|---|
| BR-057 | A policy may have multiple beneficiaries or nominees, depending on the product and policy terms. |
| BR-058 | Each beneficiary or nominee association must be linked to the relevant policy. |
| BR-059 | Beneficiary allocation percentages, where applicable, must follow the applicable policy rules. |
| BR-060 | The total allocation percentage for a policy's beneficiary distribution must not exceed 100% and should equal 100% where the distribution is required to be fully allocated. |
| BR-061 | Beneficiary and nominee changes should retain effective dates where historical tracking is required. |

## 10. Enterprise Data and Integration Rules

| Rule ID | Business Rule |
|---|---|
| BR-062 | Source system identifiers must be retained for traceability. |
| BR-063 | Each integrated record must be identifiable by its source system or equivalent lineage metadata. |
| BR-064 | Enterprise identifiers must be consistently applied to integrated business entities. |
| BR-065 | Duplicate source records must be identified and handled using documented matching and survivorship rules. |
| BR-066 | Mandatory target attributes must be populated or handled according to documented exception rules. |
| BR-067 | Date, timestamp, currency and status values must follow agreed standard definitions. |
| BR-068 | Historical changes must be captured according to the selected history-tracking strategy. |
| BR-069 | Related records must maintain referential integrity in the target data model. |
| BR-070 | Data transformations must be documented and traceable to their source attributes. |

---

## 11. Key Relationship Rules for Data Modelling

The following table summarises the major entity relationships implied by the business rules.

| Parent Entity | Child Entity | Relationship | Explanation |
|---|---|---|---|
| CUSTOMER | CUSTOMER_ADDRESS | 1:M | A customer may have multiple addresses |
| CUSTOMER | CUSTOMER_CONTACT | 1:M | A customer may have multiple contact details |
| CUSTOMER | POLICY_HOLDER | 1:M | A customer may hold multiple policies |
| POLICY | POLICY_HOLDER | 1:M | A policy must have at least one policyholder |
| INSURANCE_PRODUCT | POLICY | 1:M | A product may be associated with multiple policies |
| INSURANCE_PRODUCT | PRODUCT_COVERAGE | 1:M | A product may offer multiple coverage types |
| COVERAGE_TYPE | PRODUCT_COVERAGE | 1:M | A coverage type may be offered by multiple products |
| POLICY | POLICY_COVERAGE | 1:M | A policy may contain multiple coverage records |
| POLICY | PREMIUM_INVOICE | 1:M | A policy may generate multiple invoices |
| PAYMENT_TRANSACTION | PAYMENT_ALLOCATION | 1:M | A payment may have multiple allocations |
| PREMIUM_INVOICE | PAYMENT_ALLOCATION | 1:M | An invoice may receive multiple allocations |
| POLICY | CLAIM | 1:M | A policy may have multiple claims |
| CLAIM | CLAIM_STATUS_HISTORY | 1:M | A claim may have multiple status changes |
| CLAIM | CLAIM_ASSESSMENT | 1:M | A claim may have multiple assessments |
| CLAIM | CLAIM_SETTLEMENT | 1:M | A claim may have settlement records |
| BRANCH | AGENT | 1:M | A branch may have multiple agents, subject to assignment history |
| POLICY | POLICY_BENEFICIARY | 1:M | A policy may have multiple beneficiaries |
| POLICY | POLICY_NOMINEE | 1:M | A policy may have multiple nominees |

**Modelling note:** These are proposed relationships. The final CDM and LDM must distinguish direct relationships from associative entities and historical assignment entities. For example, `POLICY_HOLDER` resolves the many-to-many relationship between `CUSTOMER` and `POLICY`.

## 12. Important Modelling Considerations

The following points require detailed design decisions during logical modelling:

1. Whether the customer and insured person are always the same individual.
2. Whether a policy supports joint policyholders.
3. Whether multiple insured persons or assets can be covered under one policy.
4. Whether payment transactions can be allocated across invoices belonging to different policies.
5. Whether claim settlements can occur in multiple instalments.
6. How policy endorsements and renewals affect policy history.
7. How customer and product history should be maintained.
8. How beneficiary and nominee allocation rules vary by insurance product.

These questions should be addressed through explicit assumptions and design decisions rather than silently built into the model.

## 13. Business Rule Governance

Each business rule has a unique identifier to support traceability.

The rules will be linked to:

- Business requirements.
- Conceptual entities.
- Logical entities and attributes.
- Relationship constraints.
- Physical database constraints where enforceable.
- Source-to-target transformation rules.
- Data quality validation test cases.

Changes to business rules must be reflected in the relevant data models and documentation.

---

**End of Document**
