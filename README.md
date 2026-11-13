# DE01 — Kloud Kart Data Strategy & Architecture Case Study

Submission repository for the DE01 Data Engineering and Analytics case study. Kloud Kart is an Accra e-commerce company (about 4,000 orders a day, piloting Nigeria) whose orders, stock and customer accounts share one MySQL database with the live website. The brief asks what the company should build first, at its size and budget, and how to defend it to a board.

## The recommendation in four lines

1. Move all reports onto the pre-approved second copy of the database so the website is never touched by reporting.
2. Write one definition per key business number and show them on one shared page.
3. Register every customer list that leaves the company and run deletion requests through a tested routine.
4. Keep stock up to the minute and everything else daily; hire a data engineer first and a data analyst second; defer a warehouse, wider real-time and forecasting, each with a written trigger.

## Where to find each deliverable

| Deliverable | File |
|---|---|
| 1. Situation diagnosis (ranked findings) | `data_findings.md` |
| 2. Recommendation (2 pages) | `recommendation.md` |
| 2. Client memo (1 page) | `client_memo.md` |
| 2. Roadmap (1 page, quarterly) | `roadmap.md` |
| 2. Hiring plan, first 90 days | `hiring_plan.md` |
| 2. Investor questions | `investor_qa.md` |
| 3. Decision records | `decisions/ADR-001` to `ADR-005` |
| 4. Board presentation | `presentation/Kloud-Kart-Board-Presentation.pptx`  |
| 5. Improvement beyond the brief | `improvement/improvement.md`  |

## Decision records

| ADR | Decision | Rejected alternatives |
|---|---|---|
| 001 | Move all reporting and exports to a read replica | Scale up the single machine; buy a cloud warehouse |
| 002 | One definition per business number, served from the replica | Separate spreadsheets; warehouse-first build |
| 003 | Customer-list register and tested deletion routine | Block all exports; written policy with yearly audit |
| 004 | Only stock is fresh to the minute; everything else daily | Real-time everything; daily everything |
| 005 | Hire the engineer first, the analyst second | Analyst first; two engineers |

## Repository structure

```text
DE01-Kloud-Kart/
├── README.md
├── data_findings.md
├── recommendation.md
├── client_memo.md
├── roadmap.md
├── hiring_plan.md
├── investor_qa.md
├── decisions/
│   ├── ADR-001-reporting-on-read-replica.md
│   ├── ADR-002-one-definition-per-number.md
│   ├── ADR-003-customer-list-register-and-deletion-routine.md
│   ├── ADR-004-real-time-for-stock-only.md
│   └── ADR-005-hire-order-engineer-then-analyst.md
├── presentation/            (to follow)
└── improvement/
    └── improvement.md
```

## Evidence boundary

No dataset, query logs, server measurements or sample reports were supplied. Every finding rests on the brief or is labelled as an assumption or likely cause. Costs are given in time and effort, not currency, because no server price or salary figures were provided; quotes are a week-2 task in the roadmap. Legal points (Act 843 requirements, hosting abroad, Nigeria's rules, the agency contract) need a lawyer's review and are flagged as such throughout.

## The improvement deliverable

The improvement beyond the brief (`improvement/improvement.md`) provides an operational data protection register and 4-step customer deletion protocol. It specifies how marketing exports must be recorded, tracked, and verified across all holding locations to ensure compliance with Ghana's Data Protection Act, 2012 (Act 843) within 30 days.

---

**Project:** DE01 — Kloud Kart Data Strategy & Architecture Case Study
**Domain:** Data Engineering and Analytics
**Location:** Accra, Ghana
