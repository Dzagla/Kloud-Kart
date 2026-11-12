# DE01 — Kloud Kart Data Strategy & Architecture Case Study

## Overview

This project is part of the **DE01 Data Engineering and Analytics** learning programme.

It focuses on developing and evaluating a data strategy for **Kloud Kart**, a fictional e-commerce company based in Accra, Ghana, that is experiencing challenges with its data infrastructure, reporting processes and customer data management.

The project involves analysing the company's existing situation, evaluating architectural options, documenting decisions and communicating a practical data strategy that supports business growth.

## Case Study Background

Kloud Kart is an e-commerce business processing approximately 4,000 orders daily. Its orders, inventory and customer account information are stored in a MySQL database running on the same machine as its live website.

The company faces several challenges:

- Heavy reporting exports have slowed down the live website.
- Operations and Finance produce conflicting business figures.
- Customer information is exported for marketing without adequate tracking of copies.
- The company wants to improve its data capabilities while preparing for expansion into Nigeria.

Management is considering investments in data warehousing, real-time analytics and machine learning. However, the company has limited resources and only has the budget for two data engineering hires.

## Project Objectives

The objectives of this project are to:

1. Assess the company's existing data architecture and identify its major weaknesses.
2. Evaluate possible data engineering solutions against business requirements.
3. Develop a practical and cost-conscious data strategy.
4. Document important architectural decisions and their trade-offs.
5. Develop a 12-month implementation roadmap.
6. Communicate recommendations to business stakeholders.
7. Build an additional improvement that provides value beyond the original requirements.

## Project Deliverables

The project is organised around five major deliverables.

| Deliverable | Description |
|---|---|
| 1. Data Findings | Document identified problems, evidence, risks and outstanding uncertainties. |
| 2. Client Recommendation & Roadmap | Present the proposed strategy and a quarterly 12-month implementation plan. |
| 3. Architecture Decision Records (ADRs) | Document important architectural decisions, alternatives and consequences. |
| 4. Board Presentation | Communicate findings, recommendations, costs and implementation plans in business-friendly language. |
| 5. Additional Improvement | Build and document one practical improvement beyond the original case requirements. |

## Key Project Constraints

The proposed strategy must account for the following case-study constraints:

- A maximum of two data engineering hires.
- The existing MySQL database and live website must remain operational.
- Recommendations must account for Ghana's Data Protection Act, 2012 (Act 843).
- The company must be able to respond to a Data Protection Commission complaint concerning deleted customer information within 90 days.
- Inventory information cannot become stale because of the risk of overselling.
- Other business information can be refreshed daily.
- A second server or read replica has been pre-approved.
- Recommendations must be understandable to non-technical stakeholders.

## Repository Structure

```text
DE01-Kloud-Kart/
│
├── README.md
│
├── data_findings.md
│
├── client_memo.md
│
├── roadmap.md
│
├── decisions/
│   ├── ADR-001-short-slug.md
│   ├── ADR-002-short-slug.md
│   ├── ADR-003-short-slug.md
│   └── ADR-004-short-slug.md
│
├── presentation/
│   └── kloud-kart-board-presentation.pptx
│
└── improvement/
    ├── improvement.md
    └── [additional working artefact]
```

*The structure above is the suggested organisation for the submission. Filenames and folders should reflect the actual files included in the final repository.*

## Approach

The project follows a structured approach to data strategy development:

1. **Understand the business:** Examine the case study, business needs and operational constraints.
2. **Identify problems:** Separate observed issues from possible root causes and unverified assumptions.
3. **Evaluate options:** Consider available architectural approaches, their costs, benefits and operational requirements.
4. **Document decisions:** Record significant decisions and the alternatives considered.
5. **Plan implementation:** Translate the proposed strategy into measurable quarterly business outcomes.
6. **Communicate findings:** Prepare a board-ready presentation and client recommendation.
7. **Build an improvement:** Develop an additional practical artefact and explain its value.

## Technology and Architecture Considerations

The case study involves evaluating concepts and approaches including:

- Relational databases and database replication.
- Data extraction and transformation.
- Batch and stream processing.
- Data warehouses, data lakes and data marts.
- Data quality and data governance.
- Data modelling and business metrics.
- Data privacy and regulatory compliance.

Specific technologies and services should only be included where they are justified by the project requirements.

## Compliance Considerations

Data management recommendations must consider Ghana's Data Protection Act, 2012 (Act 843).

Particular attention should be given to:

- Customer data protection.
- Access control and accountability.
- Tracking exported copies of personal data.
- Data retention and deletion.
- Regulatory obligations and response requirements.

## Project Status

This repository serves as the working and submission repository for the DE01 Kloud Kart case study.

Each deliverable should be reviewed for completeness, supporting evidence and consistency with the final architectural decisions.

## Learning Outcomes

Through this project, the learner demonstrates an understanding of:

- Data engineering principles and architecture.
- Business-driven technology decisions.
- Data lifecycle management.
- Architectural trade-offs.
- Data governance and quality.
- Technical communication and stakeholder engagement.

---

**Project:** DE01 — Kloud Kart Data Strategy & Architecture Case Study  
**Domain:** Data Engineering and Analytics  
**Case Study:** E-commerce Data Strategy  
**Location:** Accra, Ghana