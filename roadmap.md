# Kloud Kart — 12-month roadmap

This is a working roadmap structure. It adds an early reporting-query investigation in light of the updated findings. The exact implementation choices and success thresholds should be confirmed against measured results and the learner's own architecture decision.

## Quarter 1 — Establish the facts and reduce immediate uncertainty

**Outcome for Nana:** The team can explain what is slowing Monday reporting, what differs between the two reports, and where customer-list copies are held.

- Capture the Monday reporting queries and their execution plans.
- Check the reporting date filters and compare records scanned with records returned.
- Check whether unnecessary historical records or columns are being retrieved.
- Review expensive joins, sorting, aggregations, indexes, and database/server resource use during exports.
- Compare Nana's and Finance's source data, reporting periods, filters, formulas, and metric definitions.
- Inventory customer-list exports, their locations, owners, access, and deletion process.

**How Nana can verify it:** A short findings report shows the measured query behaviour, the cause(s) supported by evidence, the reconciliation results, and an inventory/process for locating customer-data copies.

## Quarter 2 — Address the verified causes and establish dependable reporting

**Outcome for Nana:** Reporting is less disruptive to the live website, and the business has an agreed basis for its key figures.

- Apply query improvements justified by the Quarter 1 measurements.
- Evaluate the proposed read replica against the measured workload and operational cost before implementation.
- If the read replica is selected, test replication lag, reporting workload isolation, monitoring, and failure handling.
- Agree and document definitions and calculation rules for the priority business metrics.
- Establish a repeatable reporting process and compare its outputs with the agreed definitions.

**How Nana can verify it:** Monday reporting has measured performance results; the team can show whether the live-site impact has reduced; Nana and Finance can trace priority figures to agreed definitions.

## Quarter 3 — Strengthen data handling and operational controls

**Outcome for Nana:** The company can identify and manage customer-data copies and operate its reporting process consistently.

- Establish ownership and access rules for customer-list exports.
- Maintain a register of where exported customer data is stored and who is responsible for it.
- Test the process for locating and managing copies when a deletion request is received.
- Document operational checks for reporting, data freshness, replication (if used), and failures.
- Review whether the process works across the systems and locations identified in the customer-data inventory.

**How Nana can verify it:** A sample deletion-request exercise produces an auditable record of the copies identified and the actions taken; reporting and operational checks are documented.

## Quarter 4 — Review results and prepare for growth

**Outcome for Nana:** Management has evidence that the reporting and data-handling improvements are working and understands what needs to change as the business grows.

- Review reporting performance, live-site impact, reconciliation results, and customer-data handling.
- Compare actual infrastructure and operating costs with the estimates used in the decision.
- Review whether the current approach can support the business's growth and Nigeria pilot.
- Record unresolved risks, capacity limits, and the conditions that would trigger a change in approach.
- Present a concise year-end review using measures Nana can understand.

**How Nana can verify it:** A year-end report compares baseline and current measures, actual costs, remaining risks, and agreed next steps.

## Measures to establish in Quarter 1

Do not invent baselines or targets before measurement. Establish these first, then agree target values:

- Monday export duration and its effect on live-site response time.
- Query execution time, records scanned, and records returned.
- Replication lag and reporting workload impact, if a replica is implemented.
- Difference between Nana's and Finance's priority figures before and after reconciliation.
- Time and completeness of the process for locating customer-data copies in a deletion-request exercise.
