# ADR-004: Make only stock counts fresh to the minute; refresh everything else daily

- **Status:** Accepted
- **Date:** 2026-11-13
- **Author:** Data Strategy Engagement Team
- **Decision owner:** Nana Adjei (Head of Operations)

## Context

Investors asked about "real-time analytics" and a board member saw a live dashboard at another company. The brief says stock counts must not go stale, because that is how Kloud Kart oversells, and that everything else can refresh daily. With a daily volume of roughly 4,000 transactions, incoming checkout traffic is steady and predictable rather than an extreme-velocity streaming pipeline problem.

Two different things are called "real-time" here. One is the safety check when a customer buys: is there stock? The other is what people see on a dashboard. They have different risks. A wrong answer at checkout loses money and trust immediately. A dashboard that is an hour old does not change any decision at Kloud Kart that I can find.

I have not seen how the website currently checks stock at purchase. I am assuming it reads the main database at the moment of sale. That must be confirmed in the first month; if it does not, fixing it is the most urgent item in the plan.

## Decision

The check that decides whether an item can be sold stays on the main database and is made at the moment of purchase. The operations stock view on the dashboard refreshes every few minutes from the replica and shows a "last updated" time. A warning appears if the copy is more than 5 minutes behind. Every other number refreshes once a day. Any request for faster refresh must name the person who would act on it and what they would do differently.

## Alternatives considered

### Alternative A: Real-time dashboards for everything

- **How it would work:** Stream every order, payment and stock change into a live system so every chart moves within seconds.
- **Why it is attractive:** It impresses investors and is what the board member asked for. It would make future uses, such as live fraud alerts, easier.
- **Why rejected:** It needs a streaming system that nobody on the team has operated, it costs far more to run and to fix when it breaks, and it would take most of a year of the first hire's time. At 4,000 orders a day, nothing the Operations team does would change if the sales chart were seconds old rather than a day old. It also puts the live site at risk again if built on the main database.

### Alternative B: Daily refresh for everything, including stock

- **How it would work:** One daily reporting cycle for all numbers, with the same simple setup.
- **Why it is attractive:** Simplest possible design and cheapest.
- **Why rejected:** The brief states stock cannot go stale. A stock figure up to a day old would invite staff to promise items that are gone. Even if the website checks at purchase, Operations would plan restocking on old numbers.

## Consequences

- **What this buys:** Real-time where it prevents a loss, and simplicity everywhere else. Nana can say to investors "we are real-time where it matters and can tell you why." The first hire's time goes to trusted numbers, not plumbing.
- **What this costs:** The investors who liked the live-dashboard idea may be disappointed; suggested answers are in `investor_qa.md`. A little developer time to build the lag alert and the "last updated" display, and to confirm how stock is checked at purchase.
- **Downside if assumptions fail:** If an operational need emerges requiring sub-hour figures (such as rapid-fire flash sales), increasing the refresh frequency on an individual SQL view is simple and inexpensive. Conversely, if discovery confirms that checkout does not validate live inventory on the primary database, implementing that transactional check becomes our immediate P0 fix.
- **What would make me revisit this:** A named person shows a decision that is hurt by day-old numbers; orders pass about 12,000 a day; flash sales or a Nigeria launch make stock move faster than the few-minute refresh; or the stock copy is more than 5 minutes behind more than twice in a month.

## What this survives

- **Orders triple:** Survives for the purchase check, which is a single lookup. The few-minute stock view survives until about the 12,000-orders mark in ADR-001.
- **A flash sale spikes traffic:** The sale-time check on the main database is unaffected by reports. The risk is the dashboard looking behind during the spike; it will say so.
- **The copy of the database falls behind:** The stock view shows a warning and Operations is told not to trust it. Customers are unaffected.
- **Investors press for "real-time AI":** This ADR does not satisfy that wish and does not claim to. It records that the plan makes the data trustworthy first, which any later live or forecasting work needs.
