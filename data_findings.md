# Data findings — Kloud Kart

## Summary

Kloud Kart has three evidenced areas of concern:

1. **Customer-data handling:** Marketing exports customer lists, but the case does not establish that copies are tracked. This creates a risk when customers request deletion and the company must locate and manage every copy of their personal data.
2. **Live-site performance:** Monday reporting exports have slowed the live website twice in the last month. The reporting workload is therefore affecting an operational system.
3. **Inconsistent reporting:** Nana's Monday figures do not match Finance's spreadsheet. The company does not yet have an evidenced, organisation-wide agreement on how key business metrics are defined and calculated.

The shared MySQL database and live website running on the same machine are an established architectural constraint. However, the exact technical cause of the slowdowns has not been measured. Inefficient reporting queries—including queries that retrieve or process more historical data than the report needs—are additional possibilities to investigate, not confirmed findings.

No source dataset, query logs, execution plans, server metrics, or sample exports were supplied for this assessment. Therefore, row counts, financial effects, and technical root causes cannot yet be quantified.

## Reconciliation

No source files or row-level data were supplied, so a numerical reconciliation cannot be performed.

| Stage | Rows | Delta | Reason |
|---|---:|---:|---|
| Source orders | Not supplied | Not calculable | No source extract provided |
| Nana's Monday report | Not supplied | Not calculable | No report supplied |
| Finance spreadsheet | Not supplied | Not calculable | No spreadsheet supplied |

The mismatch between Nana's and Finance's figures is stated in the case brief, but its size and cause remain unverified.

## Findings, ranked by risk

### F-01: Customer-data copies are not tracked — Severity: High (provisional)

- **What it is:** Marketing exports customer lists, but the case indicates that copies are not tracked. If the company cannot identify where exported personal data is stored or who holds it, responding to a deletion request within the stated 90-day period may be difficult.
- **How I detected it:** This is stated in the Kloud Kart case brief: Marketing exports customer lists without copy tracking, and the company must be able to respond to a Data Protection Commission complaint within 90 days.
- **Scale:** The Marketing list contains approximately 300,000 people. The number of exported copies, their locations, and the number of people represented in each copy are not known.
- **Effect on the client's number:** No direct effect on a business metric has been quantified. The potential effects are regulatory, financial, operational, and reputational.
- **What I did about it:** Identified customer-data copy tracking and the ability to locate and manage copies as areas requiring investigation and control.
- **Residual risk:** The actual locations of copies, access permissions, retention practices, deletion procedures, and evidence of compliance have not been verified.

### F-02: Reporting exports affect live-site performance — Severity: High (provisional)

- **What it is:** The live website and MySQL database run on the same machine. The case states that Monday exports slowed the live site twice in the previous month. Reporting activity may therefore be competing with customer-facing operations for shared resources.
- **How I detected it:** The shared-server arrangement and the two reported slowdowns are stated in the case brief.
- **Scale:** The database is approximately 40 GB, and Monday exports contain a few hundred thousand rows. The duration of the slowdowns, number of affected users, and exact resource consumption are not supplied.
- **Effect on the client's number:** The slowdown could affect customer experience and sales, but lost orders or revenue have not been quantified.
- **What I did about it:** Identified the reporting workload and shared infrastructure as a performance risk. The reporting queries should be examined before attributing the slowdown to one specific technical cause.
- **Residual risk:** The precise bottleneck is unknown. Possible contributing factors to check include:
  - Queries scanning or returning more records than the report requires.
  - Historical records being loaded when only a recent reporting period is needed.
  - Selecting unnecessary columns.
  - Expensive joins, sorting, or aggregations.
  - Missing or unsuitable indexes.
  - CPU, memory, disk I/O, or database-lock contention on the shared machine.

  These are investigation points, not confirmed causes. Query execution plans, records scanned versus returned, query duration, database metrics, and server metrics are needed to establish the cause.

### F-03: Nana's and Finance's reports do not agree — Severity: Medium (provisional)

- **What it is:** Nana's Monday figures differ from Finance's spreadsheet. One possible explanation is that the teams use different definitions, filters, date ranges, or calculation methods for business metrics such as revenue, operating cost, or active customers.
- **How I detected it:** The disagreement between Nana's and Finance's figures is stated in the case brief. The reason for the disagreement has not been established.
- **Scale:** The number of affected metrics, size of the differences, and reporting periods involved are not known.
- **Effect on the client's number:** Management may make decisions using inconsistent figures. The financial or operational impact cannot be quantified without comparing the reports.
- **What I did about it:** Identified the need to compare the source data, reporting periods, filters, formulas, and metric definitions used by both reports.
- **Residual risk:** Different metric definitions are only a hypothesis. Other possible causes include missing or duplicated records, different source extracts, timing differences, and calculation errors. The original reports and their underlying queries or formulas are needed to determine the cause.

## Looked wrong, is not wrong

| Apparent problem | Why it looks wrong | Why it is actually fine |
|---|---|---|
| The company does not have real-time reporting for every business area | Real-time analytics may appear desirable to investors | The case states that stock counts cannot go stale, while other data can refresh daily. Different data needs may justify different freshness levels; real-time processing is not automatically necessary everywhere. |
| The database is approximately 40 GB | The size may sound large enough to require a complex data platform | Database size alone does not establish that a warehouse or lakehouse is necessary. The workload, growth, reporting needs, team capacity, and costs also matter. |

## Could not verify

- The exact cause of the two live-site slowdowns.
- Whether Monday reporting queries retrieve unnecessary historical records or select unnecessary columns.
- Whether relevant indexes exist and are being used.
- Query execution times, execution plans, rows scanned, rows returned, and database/server resource utilisation.
- The exact difference between Nana's report and Finance's spreadsheet.
- Whether the mismatch comes from metric definitions, date ranges, filters, missing records, duplicates, or calculation errors.
- The number and locations of customer-data exports and copies.
- Whether access controls, retention rules, and deletion procedures are consistently applied.
- The number of orders or amount of revenue affected by reporting-related slowdowns.
- The financial value of the risks identified above.

**Evidence boundary:** Findings above are based on facts stated in the case brief and the learner's initial diagnosis. Items described as possible causes or explanations must be validated before being presented as established facts.
