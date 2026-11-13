# Recommendation: what Kloud Kart should build first

**For:** Nana Adjei, Head of Operations   **Date:** November 2026 (Engagement Date)

## The answer

Kloud Kart does not have a big-data problem. It has three small, fixable ones: reports and shoppers share one machine, nobody owns the definition of a business number, and customer lists leave with no record. Fix those, in that order of urgency, and the company has a real data strategy that fits a 4,000-orders-a-day business with a team of one developer and two new hires.

**Build first:**

1. **A dedicated read replica isolated for analytics and exports.** Sizing and budget are pre-cleared in principle, keeping production checkout isolated from reporting strain. (Decision 1)
2. **Single, reconciled definitions for core performance numbers, displayed on a shared operational view.** Unifies operational metrics across Nana and Finance. (Decision 2)
3. **A mandatory customer data extraction register paired with a step-by-step deletion verification workflow.** Operational protocol established and ready to deploy. (Decision 3)
4. **Up-to-the-minute stock verification, with standard daily batch refresh for all other metrics.** (Decision 4)
5. **Two sequenced hires: a data engineer first to secure pipelines, followed by an analyst.** (Decision 5)

## What it costs

I have no server price, current hosting bill or salary figures, so I will not invent them. This table gives the cost in things you can verify. Quotes should be collected in the first two weeks.

| Item | Money | People's time |
|---|---|---|
| Second server for reports | About the same monthly bill as the current server (quote needed) | Developer: 2–3 weeks |
| Agreeing definitions | None | You and Finance: about 2 weeks |
| Dashboard | Start with a free option; pay only if needed (quote needed) | First hire: 4–6 weeks |
| Customer-list register | Operational policy (no tooling license) | 5 minutes per export logged; 1 week to align Marketing and agency partners |
| Two data hires | The board's existing budget | n/a |
| Legal check on the data law and agency contract | A lawyer's fee (quote needed) | Small |

For comparison, the options I recommend against cost far more: a cloud data warehouse adds a monthly charge that grows with use and about six months of the first hire's time before you see one trusted number; live dashboards for everything would take most of a year.

## Why this fits Kloud Kart, not Amazon

With roughly 4,000 daily checkouts distributed over 24 hours and a 40 GB relational store expanding at 15–20% annually, transaction throughput is steady rather than volatile. A dedicated read-only replica provides ample headroom for reporting workloads across several years of expansion. The threshold conditions that would justify enterprise warehousing are clearly defined in Decision 1: sustained volumes exceeding 12,000 orders daily, database footprint passing 200 GB, or an operational need to blend diverse external transaction feeds.

## The wish list

- **"A data warehouse, or maybe a lakehouse."** Not yet. It solves the same isolation problem as a read replica but introduces recurring consumption billing, complex ETL maintenance, and cross-border data transfer concerns under Act 843. It becomes appropriate once the scale thresholds above are reached.
- **"Real-time dashboards."** Strictly reserved for inventory. Operational decisions in merchandising and logistics do not change if aggregate performance figures update on a daily cadence rather than minute-by-minute. (Decision 4)
- **"ML for demand forecasting, eventually."** Deferred until data baselines are stable. Training machine learning algorithms on inconsistent sales totals simply compounds accounting discrepancy into inventory errors. The roadmap evaluates readiness in Q4 as a feasibility assessment, not a dedicated hire.
- **"Just buy Snowflake or BigQuery."** The developer correctly observes that cloud platforms can scale, but introducing variable-cost infrastructure before foundational metric definitions exist is premature, and Finance’s initial hesitation was justified.

## Decisions I made because you were unavailable

Report numbers use the starting definitions in Decision 2. Campaign lists must be destroyed after 90 days unless you extend them. The engineer is hired first. Stock is protected at the moment of purchase. Change any of these and the plan holds; the decision records say what each change costs.

## What the plan survives

- **Orders double with the Nigeria pilot:** Yes. Extra load lands on selling, which reports no longer touch.
- **A complaint arrives next month:** Partly. The register shortens the hunt but does not know about older copies until the first-90-days search is done.
- **Hiring slips by three months:** Yes. The developer can build the second copy and you can run the register in the meantime.
- **The board cuts to one hire:** The engineer alone delivers the second copy, definitions and dashboard. Customer-list duties fall back to you, which is less safe.
- **Investors demand live everything:** No. Decision 4 and the investor answers explain why, and what we would do if a named decision needed it.

## What I could not verify

The cause of the slowdowns, the size of the gap with Finance, the number of customer-list copies, whether stock is checked at the moment of purchase, and the legal points (hosting abroad, Nigeria's rules, the agency contract). The first month of the roadmap measures or confirms each.

*Decisions are in `decisions/`. Investor answers are in `investor_qa.md`. Hiring detail is in `hiring_plan.md`.*
