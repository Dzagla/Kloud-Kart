# Hiring plan: the two data roles

The board has budgeted two data hires this financial year. I have not seen the pay bands, so this plan states roles, order and first-90-day outcomes, not salaries. See ADR-005 for why the order is engineer first.

## Hire 1: Data engineer (starts as soon as possible)

**What they own:** The second copy of the database, the saved definitions and the shared page, and the alerts that tell us when something is behind or broken. They take over from the developer everything that is reporting-related, so reports are no longer one person's knowledge.

**What to look for:** Strong database and reporting skills in the system Kloud Kart already runs; has fixed slow reports before; writes things down. Python is useful, not essential. They should be comfortable being the only data engineer.

**First 90 days (outcomes Nana can verify)**

| Days | Outcome |
|---|---|
| 1–30 | Reads the Monday queries and measures how long each takes and how much it reads. Works with the developer to put the second copy live and moves Monday's export onto it. Confirms how stock is checked at purchase. **Check:** Monday's export runs with no website slowdown. |
| 31–60 | Builds the first saved definitions from the ones signed by you and Finance, runs them against one week of real orders and reports every difference. **Check:** a list of why each gap exists. |
| 61–90 | First version of the shared page with the six key numbers; stock view with "last updated" and a lag warning; a written set-up and recovery guide that someone else could follow. **Check:** you and Finance read the same figure; the developer follows the guide and rebuilds the second copy in a test. |

## Hire 2: Data analyst and data steward (starts about 3–4 months after Hire 1)

**What they own:** The meaning of the numbers, the customer-list register, the monthly check and the link to Finance, Marketing and Operations. They answer "why did this number change?" and "who has this customer's data?"

**What to look for:** Comfortable with Finance and Marketing teams, careful about detail, can explain a number to a non-technical person; has handled personal data responsibly. Strong SQL; Python is a plus.

**First 90 days (outcomes Nana can verify)**

| Days | Outcome |
|---|---|
| 1–30 | Takes over the register from you; reviews every entry with its holder; confirms end dates. Reads the data protection law and the agency contract with a lawyer. **Check:** register entries each have an owner and an end date. |
| 31–60 | Runs a practice deletion request from receipt to evidence file. Finds out where it was slow and fixes it. **Check:** the practice finishes inside the 30-day target. |
| 61–90 | Spot-checks Marketing and the agency against the register; adds Nigeria to the definitions; starts a monthly one-page report for you on gaps, late copies and open requests. **Check:** the first monthly report arrives and finds no unregistered list. |

## What neither hire does this year

Demand forecasting, a warehouse, or live dashboards beyond stock. If the year-end review says forecasting is worth trying, it is scoped as a small project with a clear stop point, not as a third hire.

## If one hire is lost or delayed

- **Engineer delayed:** The developer builds the second copy; you cover definitions with Finance. The shared page slips by about a quarter.
- **Analyst delayed:** You run the register with a named backup; the engineer covers definitions; the monthly review is done by you.
- **Both delayed beyond month 6:** Tell the board. This plan assumes at least the engineer is in post by month 3.
