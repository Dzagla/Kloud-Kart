# ADR-005: Hire the data engineer first, the data analyst second

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Nana Adjei (Head of Operations)

## Context

The board has budgeted two data hires this financial year, not three. The company has one developer who knows the database and the website. Nobody else has run a data system or written Python professionally. The plan needs two kinds of work: building and running the reporting copy, saved definitions and dashboard (technical), and owning the definitions, the register, the reconciliation with Finance and the people side of data (analytical and governance). A third hire for forecasting is not available.

The order matters because the first hire sets what the second has to work with, and because the company is exposed to one person leaving.

## Decision

The first hire is a data engineer with strong database and reporting skills, starting as soon as possible. The second is a data analyst who also acts as data steward, starting about three to four months later. Machine learning for demand forecasting is not a hire this year.

## Alternatives considered

### Alternative A: Analyst first, engineer second

- **How it would work:** An analyst starts first, takes the reconciliation with Finance, writes the definitions, owns the register and builds the first reports.
- **Why it is attractive:** The visible pain is that Nana's and Finance's numbers disagree. An analyst could reach that faster than an engineer. The register and definitions need no engineering.
- **Why rejected:** Without the reporting copy and saved views, the analyst would build reports on the same shared server, repeating the Monday slowdowns, or rely on more spreadsheet exports, which is the problem we are fixing. The developer is also the only person who can set up the replica and cannot do it plus the dashboard plus their day job. The compliance register is already built and Nana can run it in the meantime.

### Alternative B: Two engineers

- **How it would work:** Two technical hires split infrastructure and pipelines, to be safe on the technical side and ready for later growth.
- **Why it is attractive:** Strong technical coverage, and no single point of failure for the data systems.
- **Why rejected:** Nobody would own definitions, the register and the link to Finance and Marketing, which is where the board will look first. At 40 GB and 4,000 orders a day the technical load is moderate; the harder problem is agreement on what numbers mean and who handles customer data. Two engineers would build faster and still disagree with Finance.

## Consequences

- **What this buys:** The reporting copy, dashboard and a documented set-up arrive in the first two quarters, so the second hire starts with trusted data. It also reduces the risk of one person holding all the knowledge.
- **What this costs:** About three to four months with no dedicated analyst. During that time Nana and Finance spend about 2 weeks on definitions and Nana runs the register. The roles are in `hiring_plan.md`. The salaries are the board's existing budget; I have not seen the figures.
- **What it costs the client if I am wrong:** If the analyst should have come first, the cost is a slower reconciliation and a longer wait for one agreed number, perhaps by a quarter. If the engineer cannot be hired in time, the developer sets up the replica alone with Nana covering definitions, and the plan slips by weeks, not months.
- **What would make me revisit this:** The first hire has not started by month 3; the reconciliation reveals data errors that are not fixable by definitions; or the first hire turns out to be strong on analysis and weak on engineering (swap the order).

## What this survives

- **Both hires arrive late:** Survives with delay, because the developer can build the replica and Nana can run the register in the meantime.
- **The first hire leaves in the first year:** Survives better than today, because the first 90 days include a written recovery guide and definitions are written down. It does not survive if the guide is skipped.
- **Budget falls to one hire:** The engineer alone can deliver the replica, definitions and dashboard. The register and governance would fall to Nana, which is less safe and should be stated to the board.
- **Pressure to add ML forecasting:** Not survived and not claimed. The plan sets up what forecasting needs (clean, agreed history) and records a year-end test; see the roadmap.
