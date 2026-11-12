# ADR-001: Retain the Existing Database Architecture and Scale Resources on Demand

**Status:** Accepted  
**Decision owner:** Kloud Kart  
**Decision:** Maintain the existing MySQL architecture, with on-demand provisioning of additional CPU and memory resources when reporting workloads increase, particularly on Mondays.

## Context

Kloud Kart currently operates its live website and MySQL database on the same machine. The database is approximately 40 GB, and Monday reporting exports have slowed the live website twice in the previous month.

The company has a small technical team and a limited data-hiring budget. The case also states that a second server or read replica is pre-approved, but this decision does not introduce either at this stage.

## Decision

Retain the existing database architecture and provision additional CPU and memory resources on demand when reporting workloads require them, particularly during Monday reporting.

Query-performance investigation and optimisation should accompany this approach. The team should examine date filters, records scanned versus returned, selected columns, joins, sorting, aggregations, indexes, query execution plans, and server/database resource utilisation.

## Decision rationale

- The database is relatively small at approximately 40 GB.
- The technical team is small, so avoiding additional infrastructure reduces operational complexity.
- The case reports approximately 4,000 orders per day; the 300,000 figure refers to the Marketing customer list, not daily orders.
- On-demand resource provisioning may accommodate temporary increases in reporting workload without introducing a separate reporting environment.
- This approach retains the current architecture while allowing capacity to be adjusted when workload demands justify it.

## Alternatives considered

### Alternative A: Introduce a read replica

A read replica would provide a separate database server for reporting queries while replicating changes from the primary database.

It could reduce direct reporting-query pressure on the primary database, but it introduces additional infrastructure, replication monitoring, lag management, and operational responsibilities. It was not selected at this stage because the chosen approach prioritises retaining the current architecture and keeping operational complexity low.

### Alternative B: Create a separate reporting database populated on a schedule

A separate reporting database could isolate reporting workloads and support reporting-specific data structures. However, it would require data-transfer jobs, monitoring, reconciliation, and additional operational maintenance. It was not selected at this stage for the same simplicity and team-capacity reasons.

## Consequences

### Benefits

- Retains the current architecture.
- Avoids introducing replication or a separate reporting data pipeline at this stage.
- Limits additional operational components for a small technical team.
- Allows computing capacity to be increased when workload demands justify it.

### Costs and risks

- Additional CPU and memory provisioning may increase infrastructure costs.
- Reporting queries and live website operations continue to share database resources.
- Scaling resources alone may not resolve inefficient queries or excessive data retrieval.
- The chosen approach depends on the hosting environment supporting resource changes without unacceptable disruption.
- Capacity increases may become insufficient as data volumes and business traffic grow.

## Revisit conditions

Reconsider this decision if measured performance shows that query optimisation and resource scaling cannot adequately protect live website performance, if resource costs become disproportionate, or if business growth makes the current architecture unsuitable.

## What this decision survives

The decision is based on the current case constraints and the team's present capacity. If workload measurements or growth invalidate those assumptions, the architecture should be reviewed rather than retaining it by default.
