# Recommendation: what Kloud Kart should build first

**For:** Nana Adjei, Head of Operations   **Date:** 13 November 2026

## The answer

Kloud Kart does not have a big-data problem. It has three small, fixable ones: reports and shoppers share one machine, nobody owns the definition of a business number, and customer lists leave with no record. Fix those, in that order of urgency, and the company has a real data strategy that fits a 4,000-orders-a-day business with a team of one developer and two new hires.

**Build first:**

1. **A second copy of the database for reports only.** The server is already approved. Every report and export reads from it, so the website is never touched. (Decision 1)
2. **One written definition per key number, shown on one page.** You and Finance read the same figures. (Decision 2)
3. **A register of every customer list, and a tested routine for deletion requests.** Built and working. (Decision 3)
4. **Up-to-the-minute stock, and daily everything else.** (Decision 4)
5. **Two hires: a data engineer first, a data analyst second.** (Decision 5)

## What it costs

I have no server price, current hosting bill or salary figures, so I will not invent them. This table gives the cost in things you can verify. Quotes should be collected in the first two weeks.

| Item | Money | People's time |
|---|---|---|
| Second server for reports | About the same monthly bill as the current server (quote needed) | Developer: 2–3 weeks |
| Agreeing definitions | None | You and Finance: about 2 weeks |
| Dashboard | Start with a free option; pay only if needed (quote needed) | First hire: 4–6 weeks |
| Customer-list register | None (already built) | 5 minutes per export; 1 week to get Marketing and the agency using it |
| Two data hires | The board's existing budget | n/a |
| Legal check on the data law and agency contract | A lawyer's fee (quote needed) | Small |

For comparison, the options I recommend against cost far more: a cloud data warehouse adds a monthly charge that grows with use and about six months of the first hire's time before you see one trusted number; live dashboards for everything would take most of a year.

## Why this fits Kloud Kart, not Amazon

About 4,000 orders a day is one every 22 seconds. The database is about 40 GB and grows 15–20% a year. That is small and slow-growing. A second copy of the database handles this comfortably for years. The tests that would tell us to buy something bigger are written down in Decision 1: more than about 12,000 orders a day, more than about 200 GB, or needing data from outside the website.

## The wish list

- **"A data warehouse, or maybe a lakehouse."** Not yet. It solves the same problem as the second server but adds cost, a new skill and a copy-of-data risk that needs a legal check. It is the next step once the triggers above are hit.
- **"Real-time dashboards."** For stock only. Nothing else you do changes if a chart is seconds old rather than a day old. (Decision 4)
- **"ML for demand forecasting, eventually."** Not this year, and not a hire. Forecasting built on numbers that disagree forecasts the disagreement. The roadmap ends the year with a check on whether the data is clean enough to try.
- **"Just buy Snowflake or BigQuery."** The developer is right that it would work. It is the wrong first move for the reasons above, and Finance was right to flinch.

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
