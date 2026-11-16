# Business Requirements Document (BRD)
## Insurance Enterprise Data Warehouse (EDW)

| Document Information | Details |
|---|---|
| Project Name | Insurance Enterprise Data Warehouse |
| Organisation | SecureLife Insurance Ltd. (Fictional) |
| Document Name | Business Requirements Document |
| Document Version | 1.0 |
| Document Status | Draft – Assumed Requirements |
| Prepared For | Portfolio Design |
| Target Database | PostgreSQL |
| Data Modelling Tool | ERwin Data Modeler |

---

## 1. Introduction

### 1.1 Purpose

This Business Requirements Document (BRD) defines the business requirements for designing an Enterprise Data Warehouse (EDW) for SecureLife Insurance Ltd., a fictional insurance organisation offering Life, Health and Motor insurance products.

The document identifies the business needs, data requirements, reporting expectations and high-level capabilities required to establish a centralised insurance data warehouse.

It will serve as the foundation for subsequent data modelling activities, including Conceptual Data Modelling (CDM), Logical Data Modelling (LDM), Physical Data Modelling (PDM), dimensional modelling and source-to-target mapping.

### 1.2 Business Background

The fictional organisation operates multiple business applications to manage customer information, insurance products, policies, premiums, payments, claims and agent details.

Business information is assumed to be maintained across separate operational systems. This can make it difficult to obtain a consolidated view of customers, policies, financial transactions and claims.

The proposed EDW will provide an integrated data foundation for enterprise reporting and business analytics.

### 1.3 Business Problem

The key business challenges assumed for this project are:

- Customer information is distributed across multiple systems.
- Policy and coverage information is maintained in policy administration applications.
- Premium invoices and payment transactions are maintained separately.
- Claims information is managed independently from policy and customer information.
- Business users require a consolidated view of insurance operations.
- Inconsistent identifiers and data definitions may affect reporting accuracy.
- Historical information is required to analyse business changes over time.

### 1.4 Proposed Business Solution

Design an integrated Enterprise Data Warehouse that consolidates information from the following business areas:

- Customer Management
- Product Management
- Policy Administration
- Premium and Billing
- Payment Processing
- Claims Management
- Agent and Broker Management
- Beneficiary and Nominee Management

The EDW will provide standardised and integrated data structures to support reporting, analytics and historical analysis.

---

## 2. Business Objectives

The project aims to:

1. Establish a unified view of customer and insurance policy information.
2. Integrate data from multiple operational source systems.
3. Standardise business definitions and data structures.
4. Support premium collection and payment analysis.
5. Enable claims and settlement reporting.
6. Provide product, agent and branch performance analysis.
7. Maintain historical changes for selected business entities.
8. Improve data consistency and traceability.
9. Support analytical reporting through dimensional models.
10. Establish a scalable foundation for future business intelligence requirements.

---

## 3. Project Scope

### 3.1 In Scope

- Customer and contact information integration.
- Insurance product and coverage information.
- Policy and policyholder information.
- Beneficiary and nominee information.
- Policy renewals and endorsements.
- Premium schedules and invoices.
- Payment transactions, allocations and refunds.
- Claims registration, assessment and settlement.
- Agent, broker and branch information.
- Enterprise data modelling.
- Dimensional modelling.
- Source-to-target mapping.
- Database implementation and data validation.

### 3.2 Out of Scope

- Development of customer-facing applications.
- Actual policy issuance and underwriting processing.
- Live payment gateway integration.
- Automated claims adjudication.
- Real-time production data integration.
- Actual production deployment.
- Regulatory certification or compliance approval.

---

## 4. Business Stakeholders

The following roles represent hypothetical stakeholders for the proposed solution.

| Stakeholder | Business Interest |
|---|---|
| Business Management | Overall insurance business performance |
| Customer Service Team | Customer profiles and policy information |
| Policy Administration Team | Policy creation, coverage and renewals |
| Finance Team | Premium invoices, collections and refunds |
| Claims Team | Claim registration, assessment and settlement |
| Product Management Team | Product and coverage performance |
| Agent Management Team | Agent, broker and branch performance |
| Data and Analytics Team | Integrated data and analytical reporting |

---

## 5. Business Domains and Requirements

### 5.1 Customer Management

The organisation requires a consolidated view of customers across its insurance business.

Key requirements:

- Maintain unique customer identification.
- Store customer personal and business details as applicable.
- Maintain customer addresses and contact information.
- Support multiple addresses and contact details where applicable.
- Associate customers with multiple insurance policies.
- Maintain customer information received from different source systems.
- Track relevant historical customer changes.

### 5.2 Product Management

The organisation requires standardised information about insurance products and their available coverages.

Key requirements:

- Maintain insurance product details.
- Classify products into Life, Health and Motor categories.
- Maintain product-specific coverage definitions.
- Support multiple coverage options under a product.
- Maintain product versions and effective dates.
- Identify active and inactive products.

### 5.3 Policy Management

The organisation requires a consolidated view of insurance policies.

Key requirements:

- Maintain unique policy identification.
- Associate policies with insurance products.
- Associate policies with customers and policyholders.
- Support multiple coverages under a policy.
- Maintain policy start and end dates.
- Track policy status.
- Support policy renewals and endorsements.
- Maintain beneficiaries and nominees where applicable.
- Preserve policy history for analytical reporting.

### 5.4 Premium and Billing Management

The organisation requires visibility into premium billing and outstanding amounts.

Key requirements:

- Maintain premium schedules.
- Generate and store premium invoice information.
- Associate invoices with relevant policies.
- Support instalment-based premium billing.
- Maintain invoice due dates and payment statuses.
- Record premium adjustments.
- Support analysis of billed, collected and outstanding premiums.

### 5.5 Payment Management

The organisation requires consolidated payment transaction information.

Key requirements:

- Maintain unique payment transaction references.
- Associate payments with customers and relevant policies where available.
- Support allocation of payments against premium invoices.
- Support partial and multiple payments.
- Maintain payment transaction dates and amounts.
- Record failed, successful and pending payments.
- Maintain refund information.
- Support payment reconciliation and collection reporting.

### 5.6 Claims Management

The organisation requires visibility into claims registered against insurance policies.

Key requirements:

- Maintain unique claim identification.
- Associate claims with relevant policies.
- Identify the customer or insured party associated with a claim.
- Maintain claim registration and incident dates.
- Track claim status changes.
- Maintain claim assessment information.
- Record approved, rejected and settled claim amounts.
- Maintain claim settlement details.
- Support claims analysis by product, policy, customer and period.

### 5.7 Agent and Broker Management

The organisation requires information about agents, brokers and their associated branches.

Key requirements:

- Maintain agent and broker details.
- Maintain agent identification and licensing information.
- Associate agents with branches.
- Associate policies with the responsible selling or servicing agent where applicable.
- Support agent performance reporting.
- Maintain relevant historical assignment information.

### 5.8 Beneficiary and Nominee Management

The organisation requires beneficiary and nominee information associated with insurance policies.

Key requirements:

- Maintain beneficiary and nominee details.
- Associate beneficiaries and nominees with relevant policies.
- Support multiple beneficiaries or nominees for a policy.
- Capture allocation percentages where applicable.
- Maintain effective dates and relationship details where applicable.

---

## 6. Business Reporting Requirements

The proposed EDW should support the following analytical reporting requirements.

| Report ID | Report Name | Business Purpose |
|---|---|---|
| RPT-001 | Customer Summary Report | Analyse customer distribution and profiles |
| RPT-002 | Policy Summary Report | Analyse policies by product, status and period |
| RPT-003 | Policy Renewal Report | Identify upcoming and completed renewals |
| RPT-004 | Premium Collection Report | Analyse billed and collected premiums |
| RPT-005 | Outstanding Premium Report | Identify unpaid and overdue invoices |
| RPT-006 | Payment Reconciliation Report | Compare payment transactions and invoice allocations |
| RPT-007 | Claims Summary Report | Analyse claims by status, product and period |
| RPT-008 | Claims Settlement Report | Analyse approved and settled claim amounts |
| RPT-009 | Agent Performance Report | Analyse policies and premiums by agent |
| RPT-010 | Product Performance Report | Compare product-level policy and claims performance |
| RPT-011 | Branch Performance Report | Analyse business performance by branch |
| RPT-012 | Customer Policy History Report | View customer policy history over time |

These are proposed reporting requirements. Actual dashboard layouts and report calculations will be defined during dimensional modelling.

---

## 7. High-Level Data Requirements

The EDW must support the following major information groups:

| Data Group | Key Information |
|---|---|
| Customer | Customer ID, name, type, date of birth or incorporation date |
| Customer Address | Address type, location and effective dates |
| Customer Contact | Email, phone and contact type |
| Insurance Product | Product ID, name, category and status |
| Coverage | Coverage ID, type, limits and conditions |
| Policy | Policy number, product, dates and status |
| Policy Holder | Customer and policy relationship |
| Policy Coverage | Coverage associated with a policy |
| Beneficiary | Beneficiary details and allocation |
| Nominee | Nominee details and relationship |
| Premium Invoice | Invoice number, amount, due date and status |
| Payment | Transaction reference, amount, date and status |
| Payment Allocation | Payment amount allocated to an invoice |
| Claim | Claim number, policy, incident date and status |
| Claim Assessment | Assessment details and assessed amount |
| Claim Settlement | Settlement amount and settlement date |
| Agent | Agent identification and details |
| Broker | Broker identification and details |
| Branch | Branch identification and location |

Detailed attributes, data types, keys and relationships will be defined during logical and physical modelling.

---

## 8. Data Integration Requirements

The proposed EDW will consolidate data from seven hypothetical source systems.

| Source ID | System | Data Domains |
|---|---|---|
| SRC-001 | CRM | Customer, address and contact |
| SRC-002 | PAS | Policy, policyholder, coverage, renewal and endorsement |
| SRC-003 | CMS | Claim, assessment, status and settlement |
| SRC-004 | PBS | Premium invoice, schedule and adjustment |
| SRC-005 | PPS | Payment, allocation and refund |
| SRC-006 | AMS | Agent, broker, branch and licence |
| SRC-007 | PMS | Product, category and coverage definitions |

The integration design must:

- Retain source system identifiers.
- Identify source records and their corresponding target entities.
- Standardise common business attributes.
- Define transformation and validation rules.
- Support traceability between source and target records.
- Address duplicate and inconsistent source records through documented rules.

---

## 9. Historical Data Requirements

The EDW should preserve historical information where changes are relevant to business analysis.

Examples include:

- Customer address changes.
- Customer profile changes.
- Insurance product version changes.
- Policy status changes.
- Policy endorsement history.
- Agent and branch assignment changes.
- Claims status history.

Historical tracking methods will be selected based on the business requirements and documented in the logical and dimensional design.

---

## 10. Data Quality Requirements

The proposed EDW should support the following data quality dimensions:

| Data Quality Dimension | Requirement |
|---|---|
| Completeness | Mandatory business attributes should be populated |
| Accuracy | Data should reflect valid business information |
| Consistency | Common attributes should follow standard definitions |
| Uniqueness | Duplicate business identifiers should be identified |
| Validity | Data should comply with defined formats and allowed values |
| Referential Integrity | Related records should maintain valid relationships |
| Timeliness | Data should be available according to the defined refresh process |

---

## 11. Assumptions and Dependencies

- All business requirements are assumed for demonstration.
- The organisation and source systems are fictional.
- Source system structures are hypothetical.
- No actual business stakeholder interviews have been conducted.
- Synthetic datasets will be used.
- PostgreSQL is the target database.
- ERwin Data Modeler is the modelling tool.
- Business definitions and relationships may be refined during modelling.
- Source-to-target mappings will be based on the assumed source inventory.

---

## 12. Requirements Traceability

Each business requirement will receive a unique identifier and will be traced through the project lifecycle.

The intended traceability path is:

**Business Requirement → Business Rule → Conceptual Entity → Logical Entity/Attribute → Physical Table/Column → Source-to-Target Mapping → Validation Test Case**

A requirements traceability matrix will be maintained as the modelling phases progress.

---

## 13. Approval and Document Status

This BRD represents the assumed business requirements for an independent portfolio project.

Since SecureLife Insurance Ltd. is fictional, formal business stakeholder approval is not applicable.

| Item | Status |
|---|---|
| Business requirements identified | Drafted |
| Business domains identified | Drafted |
| Reporting requirements identified | Drafted |
| Data integration requirements identified | Drafted |
| Stakeholder validation | Not applicable – fictional project |
| Requirements baseline | To be refined during modelling |

---

**End of Document**
