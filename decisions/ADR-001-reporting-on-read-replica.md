# ADR-001: Move all reporting and exports onto the pre-approved read replica

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Nana Adjei (Head of Operations)

## Context

Orders, inventory and customer accounts sit in one MySQL database on the same machine as the live website. Twice last month a Monday export slowed the site to a crawl. About 4,000 orders a day are placed on that machine, so every slow minute is a minute customers may fail to check out.

The database is roughly 40 GB and the Monday exports are a few hundred thousand rows. That is small. The problem is not size; it is that reporting and selling share one machine. A second server or read replica is already pre-approved, so the cost of the obvious fix is already accepted.

Two other facts shape the decision. Stock counts must never go stale (that is how the company oversells), but everything else can refresh daily. And Kloud Kart has one PHP/MySQL developer and nobody who has run a warehouse.

## Decision

We will run a read replica (a live, read-only copy of the database on a second server) and move every report, dashboard and export onto it, so that only the website and the order system touch the main database. Stock levels shown to customers and used for order checks continue to come from the main database; the replica is never used to decide whether an item can be sold.

## Alternatives considered

### Alternative A: Keep one machine and add computing power on demand (the previous draft of this ADR)

- **How it would work:** Leave everything where it is. Rent extra processor and memory on Mondays, and tune the slow reports.
- **Why it is attractive:** No new server, no new moving parts, cheapest on paper.
- **Why rejected:** More power on the same machine does not stop reports and customers competing for the same disk and the same database locks. It also assumes the host can change capacity without downtime, which has not been verified. It treats the symptom on the day it appears and leaves the board with no answer when the next slowdown happens. Report tuning is still worth doing (see below), but it is not a substitute.

### Alternative B: Buy a cloud data warehouse (Snowflake or BigQuery), as the developer suggested

- **How it would work:** Copy data nightly from MySQL into a hosted warehouse and run all reports there.
- **Why it is attractive:** Reports can never slow the website. It scales far past Kloud Kart's size, and the board has heard the word "warehouse".
- **Why rejected:** It solves the same problem as the replica but adds a copy pipeline, a new cost line that moves with usage, and a skill nobody on the team has. Finance has already flinched at the price. It also sends customer data to a foreign hosting region, which needs a separate Data Protection Act review before any personal data leaves Ghana. At 40 GB and 15-20% growth a year, the replica does the job at a fraction of the effort. This is a later option, not a first step (see revisit triggers).

## Consequences

- **What this buys:** The website is protected from reporting. Reporting can run at any hour, not just quietly on Monday mornings. The fix uses an already-approved purchase and one technology the developer already knows. Nothing changes for the people who use the reports.
- **What this costs:** One extra server, with a monthly hosting bill about the same as the current machine (to be confirmed by quote; I have no price data and have not assumed one). About 2-3 weeks of the developer's time to set up and test, plus a small ongoing duty to watch that the copy is keeping up. Reports on the replica can be a few seconds to a few minutes behind the main database; that is acceptable for everything except stock.
- **What it costs the client if I am wrong:** If the replica is not enough, Kloud Kart has spent one server and some weeks, and the server remains useful as a backup. Nothing is lost that cannot be reused if a warehouse is bought later. The worse failure is a slow or broken replica that nobody notices, so a lag alert is part of the decision, not an extra.
- **What would make me revisit this:** Any one of these, measured over a month: the replica falls more than 15 minutes behind more than twice a week; reports on the replica take more than twice as long as today's; daily orders pass about 12,000 (three times today); data passes about 200 GB; or Finance or investors need to join data from sources outside the website database, such as Nigerian payment partners. A warehouse is then the next step.

## What this survives

- **Nigeria pilot doubles orders:** Survives. Extra load lands on the main database only through sales, and reports are unaffected.
- **Reporting load doubles (more users, more dashboards):** Survives; the replica absorbs it. If it does not, the replica can be upgraded without touching the website.
- **Replica fails or falls behind:** The website keeps selling. Reports pause or show a "last updated" warning. Nobody is allowed to fall back to running reports on the main database during an outage; that rule is what protects the site.
- **The one developer is away or leaves:** Survives with a written set-up and recovery guide, which is a first-90-days task for the first data hire.
- **Hiring slips to three months later:** Survives. The developer can set up the replica alone; the hires are needed for the work after it, not for this.
- **What it does not survive:** A board demand for live, second-by-second dashboards across the whole business. That is a different and much larger project, and ADR-004 (real-time scope) addresses it.

**Companion step, no extra cost:** Before the replica goes live, the developer reviews the Monday export queries for wasted work (pulling years of history or unused columns when a week is enough). I have not seen the queries, so I am not claiming this was the cause; I am claiming it is cheap to check and the replica should not hide a bad habit.
