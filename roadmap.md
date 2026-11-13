# Kloud Kart: 12-month roadmap

Each quarter ends with something you can check yourself. Month 1 starts when the board approves the plan.

| | **Quarter 1: Protect the site, find the facts** | **Quarter 2: One set of numbers** | **Quarter 3: Make it routine** | **Quarter 4: Prove it, decide what is next** |
|---|---|---|---|---|
| **What happens** | Second copy of the database goes live and all reports move to it. The developer checks the Monday queries. Finance and Operations compare one week of figures line by line and sign the definitions. Marketing starts the register. A search finds existing customer-list copies. Data engineer starts. | Saved definitions and a shared page go live with six key numbers. Board papers use the page. Spreadsheets stop being the source. Stock view shows its last-updated time. Data analyst starts. | The analyst reviews the register monthly. A practice deletion request is run end to end. Nigeria is added to the definitions. Agency contract clause is in place. Lag and failure alerts are tested. | Year-end review against the starting measurements. Check on whether the data is clean enough to try demand forecasting. Review the warehouse triggers. Plan year two. |
| **What you can verify** | Monday's export runs with no site slowdown, shown by the developer's before-and-after timings. One page lists every known copy of the customer list, with holder and end date. Finance and you sign the same definitions. Developer confirms stock is checked at purchase. | You and Finance open the same page and read the same figure for the same week. Board papers quote it. Stock view shows a "last updated" time and a warning if it falls behind. | A practice request produces an audit evidence file, finished inside the 30-day target. The monthly compliance report shows no copy kept past its end date. A spot-check of Marketing and the agency finds no unregistered list. | A one-page year-end report: slowdowns before and after, the gap between your and Finance's numbers before and after, requests closed on time, actual cost against the plan. Written answer on forecasting, warehouse and what next. |
| **Starting measures** (taken in Q1, before any target is set) | Number and length of slowdowns; time to run Monday exports; gap between your and Finance's totals for one week; number of customer-list copies found. | Same measures, re-read. | Days to complete a practice deletion request. | All of the above, compared. |
| **What it needs** | Developer 2–3 weeks. You and Finance 2 weeks. Server quote in week 2. Legal check started. | First hire 4–6 weeks. | Second hire's time; small lawyer fee. | A few days of your time for the review. |

## What would move something earlier or later

- **Earlier:** If the developer confirms stock is not checked at purchase, fixing that jumps to the front of Q1.
- **Later:** If the engineer starts after month 3, the second-copy work stays with the developer and the shared page slips by about a quarter.
- **Triggers that change the plan (planning assumptions & judgement calls to be validated in Q4):** More than about 12,000 orders a day (3× current volume), database footprint exceeding 200 GB (5× current size), a read replica falling more than 15 minutes behind twice a week, or an operational requirement to join data from external payment partners in Nigeria. Any one initiates a formal cloud warehouse review.

## What is not in the plan

Live dashboards beyond stock, demand forecasting, and a data warehouse. Each has a reason and a trigger in the decision records.
