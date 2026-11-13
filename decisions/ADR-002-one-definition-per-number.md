# ADR-002: Define each business number once, and serve every report from that one definition on the replica

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Nana Adjei (Head of Operations), with sign-off from Finance

## Context

Nana rebuilds her Monday numbers from CSV exports. Finance keeps its own spreadsheet. The two never match. I have not seen either file, so I cannot say why. The likely suspects are different meanings for the same word (for example, whether "revenue" counts cancelled or refunded orders, or delivery fees), different date cut-offs, and exports taken at different times. These are hypotheses until the two files are compared.

Whatever the cause, the pattern is the same: two people each calculate the number by hand, from their own copy, with their own rules. Investors asked about "real-time analytics" while the company cannot yet agree on yesterday's revenue.

ADR-001 puts reporting on a read replica. That gives a safe place to build one shared set of reports. Nana is unavailable for questions, so the defaults below are my decisions, to be signed off by Finance in the first month.

## Decision

Kloud Kart will write down one definition for each of its ten or so most important numbers, build each of them once as a saved view on the replica, and show them on one dashboard that Operations and Finance both use. The spreadsheets stop being the source of truth. Dashboard figures refresh daily, except stock, which refreshes every few minutes and shows a visible "last updated" time.

**Starting definitions (my decision, Finance to confirm or change in month one):**

| Number | Definition used |
|---|---|
| Orders | Orders placed and paid, not cancelled, counted by the Accra-time date of payment |
| Revenue | Value of those orders in cedis, after discounts and refunds, excluding delivery fees and tax |
| Average order value | Revenue divided by orders |
| Refund rate | Refunded orders divided by orders, same date basis |
| Active customers | Customers with at least one order in the previous 90 days |
| Stock on hand | Units in the warehouse, minus units reserved for paid orders not yet shipped |

If Finance prefers a different rule for any row, the rule changes in one place and every report changes with it. What matters is that there is only one.

## Alternatives considered

### Alternative A: Keep separate spreadsheets and reconcile them by hand each week

- **How it would work:** Operations and Finance keep their own files. One person compares them every Monday and explains the gaps.
- **Why it is attractive:** No build cost, nobody has to change how they work, and Finance keeps full control of its own file.
- **Why rejected:** It makes someone's weekly job the cleaning-up of a problem that returns every week. It also keeps the Monday exports, which is where the slowdowns come from, and keeps more copies of customer data lying around. It does not give Nana an answer when an investor asks which number is right.

### Alternative B: Build a data warehouse with a modelling layer first, then the dashboard

- **How it would work:** Load all data into a separate warehouse, model it in stages, and build the dashboard on top.
- **Why it is attractive:** It is the standard way large companies do this, and it would scale if the business grew many times over.
- **Why rejected:** The first hire would spend their first six months building plumbing before Nana sees one trusted number. The same single set of definitions can be delivered in weeks as saved views on the replica. The warehouse remains an option once the triggers in ADR-001 are hit; the written definitions carry over to it unchanged, so this decision loses nothing.

## Consequences

- **What this buys:** One answer to "what was revenue last week?" Nana and Finance can open the same page. Monday no longer needs a CSV export, which removes the main source of heavy queries and of untracked customer-data copies. Every number can be traced to its written definition.
- **What this costs:** About 2 weeks of Nana's and Finance's time to agree the definitions, and 4-6 weeks of the first hire's time to build and test the views and dashboard. Dashboard tool cost depends on the choice made in the first 90 days; I have no quote and have not assumed one. A free or low-cost option should be tried first given Finance's concern.
- **What it costs the client if I am wrong:** If Finance rejects a definition, the cost is a re-run of that one view, not a rebuild. If the dashboard turns out to be heavy for the replica, it can be given its own refresh schedule. If the real cause of the mismatch turns out to be bad data (missing or duplicated orders) rather than different rules, then the dashboard will faithfully display the wrong numbers, which is why the first-month reconciliation of the two files is a precondition, not a nice-to-have.
- **What would make me revisit this:** Finance and Operations still disagree after three months of using the same dashboard; the dashboard needs data that does not live in the website database (for example, Nigerian payment partners); or more than about 25 people need access, at which point permissions and speed need a fresh look.

## What this survives

- **Nigeria pilot adds a second currency and new order sources:** Survives if currency is added to the definitions, which is a small change. Revisit if new sources sit outside the website database.
- **Investors push for real-time on everything:** Survives. Only stock needs to be fresh because only stock causes harm when stale (overselling). Anything else gets the faster refresh only if a named person can show a decision that depends on it, and ADR-004 records that test.
- **The first hire leaves in month three:** Survives, because the definitions are written in plain language and the views are saved in the database, not in one person's head.
- **Finance refuses to move off its spreadsheet:** Does not fully survive. The dashboard would then be a second number rather than the number. The mitigation is that Finance signs the definitions in month one and the board is told that the dashboard is the figure used in board papers from quarter two.
- **Replica goes down:** Dashboard shows its last good figures with a clear "last updated" notice; the website is unaffected.
