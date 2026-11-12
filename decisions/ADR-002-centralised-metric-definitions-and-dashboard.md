# ADR-002: Establish Organisation-Wide Business Metric Definitions and a Centralised Reporting Dashboard

**Status:** Accepted  
**Decision owner:** Kloud Kart

## Context

Nana's Monday figures do not match Finance's spreadsheet. The case does not establish the exact cause of the disagreement. Different definitions, filters, reporting periods, or calculation methods may be contributing factors.

Nana and Finance need to work from the same agreed business metric definitions. The company also has a small technical team and a limited data-hiring budget. The current MySQL database is approximately 40 GB, and the existing architecture is to be retained under ADR-001.

## Decision

Kloud Kart will agree on organisation-wide definitions and calculation rules for its business metrics. A centralised dashboard will present those agreed metrics so that Nana and Finance can view and export the same figures, even when accessing the dashboard through different user roles.

The dashboard does not have to be real-time. Its refresh frequency should reflect the business need for each metric.

The dashboard will read directly from the existing MySQL database. A separate warehouse, lake, or lakehouse will not be introduced for this reporting requirement at this stage.

## Decision rationale

- Agreeing on shared metric definitions gives Nana and Finance a common basis for reporting.
- A centralised dashboard reduces reliance on separately prepared spreadsheets that may use different formulas, filters, or reporting periods.
- Role-based access allows different authorised users to access the same agreed figures according to their responsibilities.
- The dashboard does not require real-time updates for every metric; the case allows most data, other than stock counts, to refresh daily.
- Reading from the existing MySQL database avoids introducing a separate analytical storage platform and its associated infrastructure and operational responsibilities.
- Keeping the solution relatively simple is intended to make it manageable by a small team of two data hires.

## Alternatives considered

### Alternative A: Allow Nana and Finance to maintain separate spreadsheets and calculations

This preserves the current working approach and requires little initial system development.

It was not selected because separate calculations and reporting processes can continue to produce inconsistent figures and make it harder to establish one organisation-wide view.

### Alternative B: Introduce a separate warehouse, lake, or lakehouse for reporting

A separate analytical platform could provide an independent environment for reporting and more extensive data processing.

It was not selected at this stage because the immediate requirement is to establish shared metric definitions and provide a common dashboard. Introducing another data platform would add infrastructure, operational work, and governance responsibilities that may not be justified by the current scale and team capacity.

## Consequences

### Benefits

- Nana and Finance can view and export the same agreed business figures.
- Metric definitions and calculation rules become organisation-wide rather than being recreated in separate spreadsheets.
- Role-based access can limit which dashboard information different users can access.
- The approach avoids the immediate cost and operational burden of a separate analytical data platform.
- The solution is intended to remain manageable by the two data hires.

### Costs and risks

- The dashboard's queries will run against the existing MySQL database, which also supports the live website.
- Poorly designed or heavy dashboard queries could affect live-site performance.
- The dashboard depends on the availability and performance of the operational database.
- Metric definitions must be agreed, documented, maintained, and updated when business requirements change.
- Different user roles require carefully defined access permissions; role-based presentation alone does not prove that access is secure.
- A non-real-time dashboard may not be suitable for metrics that require more frequent updates, particularly stock counts.

## What this buys, what it costs, and what happens if it is wrong

This decision buys a common reporting view without introducing another data platform. It costs time to agree definitions, build and maintain the dashboard, and manage access. It also places reporting query load on the existing MySQL database.

If direct dashboard queries create unacceptable pressure on the live system, Kloud Kart will need to review query design, refresh strategy, resource capacity, or the decision to keep reporting on the operational database.

## Revisit conditions

Reconsider this decision if dashboard queries materially affect live website performance, if reporting needs grow beyond what the current database can support, if the business requires more complex historical analysis or additional data sources, or if the two-person team cannot maintain the solution reliably.

## What this decision survives

The approach is intended for Kloud Kart's current scale, reporting needs, and team capacity. It should not be treated as a permanent restriction against a separate analytical platform if measured workload, business growth, or new requirements justify one.
