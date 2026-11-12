# Data findings — Kloud Kart

## Summary

Kloud Kart's current data environment presents three main areas of concern:

1. **Customer data governance:** Marketing exports customer lists without a clear record of where exported copies go or how they are managed. This creates potential privacy, legal and reputational exposure.
2. **Database workload contention:** Heavy Monday exports have slowed the live website on two occasions in the previous month. The website and MySQL database operate on the same machine, so export activity may compete with live application workloads for resources.
3. **Inconsistent business reporting:** Nana's operational figures and Finance's spreadsheet figures do not match. This suggests that the organisation may not have agreed definitions and calculation rules for key business measures.

These issues should not be treated as proof that Kloud Kart needs machine learning, real-time dashboards or a particular storage platform. They indicate possible weaknesses in data governance, reporting standardisation and the separation of operational and analytical workloads.

The root causes described below are hypotheses based on the case information. They have not been independently verified.

## Reconciliation

| Stage | Rows | Delta | Reason |
|---|---:|---:|---|
| Source records | Not provided | Not established | The case brief does not provide the underlying sales, order or customer records. |
| Exported records | Not provided | Not established | No export files or row counts were supplied for reconciliation. |
| Reported figures | Not provided | Not established | Nana's and Finance's figures are said to differ, but the actual values and calculation rules were not supplied. |

A numerical reconciliation cannot be completed from the information available in the case brief. The differing reports are recorded as an observed issue, but the size and cause of the difference cannot be quantified here.

## Findings, ranked by risk

### F-01: Customer data exports are not adequately tracked — Severity: High

- **What it is:** Marketing exports customer lists without clear tracking of the exported copies or documented procedures for managing them.
- **How I detected it:** The case brief states that Marketing exports customer lists without copy tracking.
- **Scale:** The Marketing list contains approximately 300,000 people. The number of exports, copies, recipients and storage locations is not provided.
- **Effect on the client's number:** No direct effect on a sales or financial figure has been established. However, untracked copies may make it difficult to locate and manage customer information, including when responding to a deletion request.
- **What I did about it:** No corrective action is evidenced in the case information reviewed for this diagnosis.
- **Residual risk:** The locations of exported copies, the people who can access them, the applicable retention practices and the process for handling deletion requests remain unverified. Potential privacy, legal and reputational exposure therefore remains.

### F-02: Heavy exports affect live website performance — Severity: High

- **What it is:** Heavy Monday exports have slowed the live website. The MySQL database and live website operate on the same machine.
- **How I detected it:** The case brief reports that Monday exports slowed the live site twice in the previous month and identifies the shared-machine setup.
- **Scale:** The database is approximately 40 GB. Monday exports involve a few hundred thousand rows. The duration of the slowdown, number of affected users and number of failed or abandoned orders are not provided.
- **Effect on the client's number:** The case establishes a website-performance impact, but does not quantify lost orders, lost revenue or the effect on conversion.
- **What I did about it:** No performance change or remediation is evidenced in the case information reviewed for this diagnosis.
- **Residual risk:** The exact bottleneck has not been established. CPU, memory, disk I/O, database locks, query plans and other possible causes would need investigation before attributing the slowdown to a specific resource.

### F-03: Business reports produce conflicting figures — Severity: High

- **What it is:** Nana's operational figures and Finance's spreadsheet figures do not match.
- **How I detected it:** The case brief explicitly describes a mismatch between the figures rebuilt by Nana and Finance's spreadsheet.
- **Scale:** The number of affected metrics, reporting periods and records is not provided. The size of the differences cannot be calculated from the available information.
- **Effect on the client's number:** Conflicting reports may cause management and investor discussions to rely on different versions of business performance. The actual numerical effect is not established.
- **What I did about it:** No reconciliation or agreed organisation-wide metric definitions are evidenced in the case information reviewed for this diagnosis.
- **Residual risk:** The cause remains unverified. Possible explanations include different metric definitions, reporting periods, source data, filters or duplicate/missing records. These should be investigated before selecting a corrective approach.

## Looked wrong, is not wrong

| Apparent problem | Why it looks wrong | Why it is actually fine |
|---|---|---|
| Not established from the available case information | The case brief does not provide a specific apparent problem that has been investigated and confirmed as acceptable. | No item can responsibly be classified as “actually fine” without supporting evidence. |

## Could not verify

The following matters could not be verified from the case brief alone:

- The exact formulas, definitions, filters and reporting periods used by Nana and Finance.
- The number of rows, records or amount of money represented by the reporting mismatch.
- Whether duplicate or missing records contribute to the reporting differences.
- The precise technical bottleneck responsible for the Monday website slowdown.
- The duration of each slowdown and its effect on completed orders, revenue and customers.
- The number of customer-list exports, their recipients, storage locations and onward copies.
- Whether access permissions, retention rules and deletion procedures are documented and followed.
- Whether all customer-data copies can be located and managed within the stated 90-day response window.

These are evidence gaps, not confirmed findings. They should remain explicit until supporting records, system measurements or process documentation are available.
