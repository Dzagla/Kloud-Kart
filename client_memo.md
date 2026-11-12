# Memo to Nana

**From:** Data Strategy Engagement Team  
**Date:** 12 November 2026  
**Subject:** Reporting reliability, website performance and customer-data handling

## What I found

Three issues need attention:

- **Customer information:** Marketing exports a customer list of approximately 300,000 people, but copies are not tracked. This could make it difficult to locate and manage every copy when a customer requests deletion.
- **Website performance:** The live website and MySQL database run on the same machine. Monday reporting exports have slowed the live site twice in the past month.
- **Different business figures:** Nana's Monday figures do not match Finance's spreadsheet. The reason for the difference has not yet been established.

The reporting slowdown may be made worse by queries retrieving more historical records or columns than a report needs. This is a possibility to test, not a confirmed cause.

## What I built

I documented the known findings, their possible business effects, and the evidence still needed. The performance investigation should compare the reporting period required with the data actually scanned and returned, and review query execution plans and server/database resource use.

## What you asked for

| What you asked for | Status | Evidence |
|---|---|---|
| Reliable reporting | Investigation required | Nana's and Finance's figures differ; the cause is not yet verified |
| Protect the live website during reporting | Investigation and solution required | Two slowdowns during Monday exports are reported in the case |
| Handle customer information responsibly | Investigation and controls required | Customer exports are not tracked, according to the case |
| Fresh stock information | Requirement identified | The case says stock counts cannot go stale |
| Real-time information for every other area | Not established as necessary | The case allows other data to refresh daily |

## What I recommend

My current proposal is to assess a read replica as a way to isolate reporting queries from the live website's primary database. Before committing to it, first examine and, where appropriate, optimise the existing reporting queries. In particular, check whether they retrieve unnecessary historical records, select unnecessary columns, or perform expensive scans, joins, sorting or aggregations.

The read-replica proposal should be confirmed only after comparing the measured benefit with the additional server, replication monitoring, lag management and operational work it introduces. The team should also verify that reporting activity on the replica will not create unacceptable load on the primary database.

## What I could not stand behind

The available case information does not establish the exact technical cause of the slowdowns, the size or cause of the reporting mismatch, the number and locations of customer-data copies, or the revenue affected. No query logs, execution plans, server metrics or sample reports were supplied. These points must be verified before presenting them as facts.
