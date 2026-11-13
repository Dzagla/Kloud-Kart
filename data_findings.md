# Data findings — Kloud Kart

## Summary

Kloud Kart's three visible problems have three separate root causes, and all three are cheap to fix at the company's size. None needs a warehouse, a lakehouse or live dashboards.

1. **The website and the reports share one machine.** Monday exports compete with customers for the same database, which is why the site crawled twice last month. The cause is the arrangement, not the size: the database is about 40 GB and the exports are a few hundred thousand rows.
2. **Nobody owns the definition of a business number.** Nana and Finance each calculate figures by hand from their own copy, with their own rules. Until one definition exists, no tool can make their numbers agree.
3. **Customer lists leave the database with no record.** About 300,000 people are on Marketing's list, and nobody knows how many copies exist or who holds them. That makes a 90-day response to a Data Protection Commission complaint difficult to meet and impossible to prove.

Two further risks sit beneath these: one developer holds all the knowledge, and the board is being asked to buy things (a warehouse, live dashboards, forecasting) that do not address any of the three causes above.

No dataset, query logs, server measurements or sample reports were supplied. Findings rest on the case brief, and where I name a likely cause I say so. The first month of the roadmap exists to turn these likely causes into measured ones.

## Reconciliation

No source files or row-level data were supplied, so no real reconciliation is possible. This table shows the reconciliation that must be run in the first month. It is a plan, not a result.

| Stage | Rows | Delta | Reason |
|---|---|---|---|
| Orders in the main database for one fixed week | Not supplied | n/a | Starting point; counted by the single definition in ADR-002 |
| Nana's Monday report for the same week | Not supplied | Not calculable | To be compared line by line with the row above |
| Finance's spreadsheet for the same week | Not supplied | Not calculable | To be compared line by line with the row above |
| Remaining gap, split into: different rules, different cut-off times, missing or duplicate orders, hand-calculation errors | Not supplied | Not calculable | Each gap is assigned to one cause, so it can be fixed once |

Scale for reference, from the brief: about 4,000 orders a day, so roughly 28,000 in a week. A gap of even 1% is about 280 orders.

## Findings, ranked by risk

Ranking is by risk to Nana in front of the board: what is most likely to be asked, most damaging if unanswered, and hardest to fix after the fact.

### F-01: Customer-list copies are not tracked — Severity: High

- **What it is:** Marketing exports lists of about 300,000 customers and the company keeps no record of where the copies are or who holds them. Root cause: there is no register and no end date on any export.
- **How I detected it:** Stated in the brief. The 90-day complaint rule in the brief makes it concrete: the company would need to find every copy of a customer's data within that time.
- **Scale:** About 300,000 people in one list. Number of copies, locations and holders: unknown. Whether any copy sits with an outside agency: unknown.
- **Effect on the client's number:** None on revenue. The exposure is regulatory (Ghana's Data Protection Act, 2012 (Act 843), enforced by the Data Protection Commission) and reputational. I cannot put a cedi value on it; the brief gives no penalty or complaint history. The cost of a failure is the ability to answer "did you delete it?" truthfully.
- **What I did about it:** Designed ADR-003 (register plus deletion routine) and built the register tool with tests (`improvement/`). It starts recording from day one; older copies still need the first-90-days search.
- **Residual risk:** Older copies are unknown; the register records what people declare, not what they hide. Spot-checks are built into the roadmap.

### F-02: Monday exports slow the live website — Severity: High

- **What it is:** Reports and customers use one database on one machine. Root cause: no separation between selling and reporting.
- **How I detected it:** Two slowdowns during Monday exports, last month, are stated in the brief.
- **Scale:** At about 4,000 orders a day, an average hour carries about 170 orders (4,000 ÷ 24). Each hour of crawl puts roughly that many orders at risk, more at peak. Duration of the two slowdowns: not supplied, so I cannot give a total.
- **Effect on the client's number:** Lost or abandoned orders. Not quantified. Order value is not in the brief.
- **What I did about it:** ADR-001 moves all reports and exports to the already-approved second copy of the database. The developer also checks the Monday queries for wasted work, as a cheap companion step.
- **Residual risk:** I have not seen query logs, so I cannot rule out that one or two badly written queries are the trigger. If so, the second copy still fixes the effect on the site, but bad queries would then slow reports. Hence the check.

### F-03: Operations and Finance numbers disagree — Severity: Medium-High

- **What it is:** The same week produces two different totals. Root cause (probable): each person calculates by hand, with their own rules and cut-off times, from separate exports.
- **How I detected it:** Stated in the brief. I have not seen either file.
- **Scale:** Unknown: number of metrics, size of gaps, periods affected.
- **Effect on the client's number:** Every board number is open to challenge. The investors have already asked about data strategy; the first demand will be a number they can trust.
- **What I did about it:** ADR-002 sets one written definition per key number and starting definitions for six of them. The first-month reconciliation tests whether rules are the only cause.
- **Residual risk:** If the gap comes from missing or duplicate orders or from stock and payment data that disagree, definitions alone will not close it.

### F-04: Stock counts may not be protected at the moment of sale — Severity: Medium (unverified)

- **What it is:** The brief says stale stock is how the company oversells. I do not know whether the website checks stock in the main database at the moment of purchase.
- **How I detected it:** Stated in the brief, as a constraint. The checkout behaviour is not described.
- **Scale:** Unknown.
- **Effect on the client's number:** Oversold orders mean refunds and angry customers. No count supplied.
- **What I did about it:** ADR-004 keeps the sale-time check on the main database and adds a visible "last updated" time to the stock view.
- **Residual risk:** If the checkout does not check live stock, this moves to the top of the list. It is the first item to verify.

### F-05: One developer holds all the knowledge — Severity: Medium

- **What it is:** One PHP/MySQL developer built and runs everything. Nobody else has run a data system or written Python professionally.
- **How I detected it:** Stated in the brief.
- **Scale:** One person.
- **Effect on the client's number:** Not a number today; it becomes one the day that person leaves or is ill during a slowdown.
- **What I did about it:** ADR-005 hires an engineer first; the first 90 days include a written set-up and recovery guide.
- **Residual risk:** Until the engineer starts, the risk stands.

## Looked wrong, is not wrong

| Apparent problem | Why it looks wrong | Why it is actually fine |
|---|---|---|
| No data warehouse or lakehouse | Investors expect one and the developer suggested buying one | The database is about 40 GB and grows 15–20% a year. The problem is sharing a machine and not agreeing definitions, and a warehouse fixes neither on its own (ADR-001, ADR-002). |
| Not real-time everywhere | A board member saw a live dashboard elsewhere | The brief states only stock counts must be fresh; everything else can refresh daily (ADR-004). |
| 4,000 orders a day on one machine | It sounds like it needs a larger system | It is about one order every 22 seconds. That is a moderate load; the trouble is mixing it with reports. |
| No forecasting yet | "ML for demand forecasting" is on the wish list | Forecasting needs a stable, agreed history. Building it on numbers that disagree would forecast the disagreement. It is placed at the end of the year as a test, not a hire. |

## Could not verify

- The exact cause of the two slowdowns, and how long each lasted.
- How many orders, or how much revenue, were lost to them.
- Whether Monday queries pull more history or columns than needed.
- The size and cause of the gap between Nana's and Finance's numbers.
- How many copies of customer lists exist, where, and who holds them, including any outside agency.
- Whether the website checks stock in the main database at the moment of purchase.
- The current server bill and the market cost of the two roles; I have assumed no figures.
- Whether Ghanaian data protection rules restrict hosting customer data outside Ghana (relevant to the cloud warehouse alternative), and whether the Nigeria pilot brings Nigeria's own data protection law into play.

**Evidence boundary:** Everything above is either stated in the brief or labelled as an assumption or a likely cause. Nothing has been measured.
