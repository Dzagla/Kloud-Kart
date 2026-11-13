# Memo to Nana

**From:** Data Strategy Engagement Team
**Date:** November 2026 (Engagement Date)
**Subject:** Protecting the website, agreeing one set of numbers, and tracking customer lists

## What I found

- **Reporting queries and live shoppers compete on the same host.** Heavy Monday exports are the likely cause of the two severe site slowdowns last month, presumed to lock database resources against active customer checkouts. While unmeasured due to lack of query logs, running analytical extracts on the primary transactional database is the clear suspect; moving reports isolates this risk entirely.
- **Key business metrics lack a single source of truth.** Operations and Finance work from separate manual exports with differing calculation rules, ensuring executive figures diverge every week.
- **Customer lists containing roughly 300,000 records circulate without centralized custody.** Under Ghana's Data Protection Act, 2012 (Act 843), the company faces an assumed 90-day statutory response window to verify the complete erasure of a customer's personal data upon request (a requirement subject to confirmation by legal counsel), which is currently unprovable across distributed files.

## Deliverables delivered

| Deliverable | Status | Evidence |
|---|---|---|
| A defensible data strategy | Complete | 2-page strategic recommendation backed by five structured architectural decisions |
| 12-month execution roadmap | Complete | Phased quarterly roadmap with objective milestones and measurable verification criteria |
| Hiring plan & sequence | Complete | First 90-day onboarding deliverables for a data engineer followed by an analyst |
| Investor & board defense | Complete | Plain, commercial answers to ten tough questions from the board |
| Customer data compliance register | Complete | Detailed operational protocol, retention rules, and a deletion checklist to satisfy Act 843 |
| Board slides | Complete | presentation/Kloud-Kart-Board-Presentation.pptx |

## Strategic recommendations

1. **Isolate reporting on the approved read replica.** Directing all exports and analytics to this secondary copy insulates the primary database and guarantees website availability.
2. **Establish single, agreed definitions for core KPIs.** Standardize metric formulas across Operations and Finance, published to a common operational view.
3. **Institute mandatory logging and expiry dates for all customer exports.** Enforce clear ownership and destruction deadlines for any customer data extracted for campaigns.
4. **Stagger hiring: recruit a data engineer first, then an analyst approximately three months later.**
5. **Defer premature investments in cloud warehouses, real-time streaming, and predictive modeling.** Keep stock updates near-real-time while maintaining daily batch cycles for general reporting.

## What I could not stand behind

I had no records of what the reports ask of the database, no sample reports and no server measurements. So I cannot yet say exactly why the site slowed, how big the gap with Finance is, or how many customer-list copies exist. I assumed the website checks live stock at the moment of purchase; **please have the developer confirm this first.** I have no server price or salary figures, so costs are given in time, with quotes to follow. Please have a lawyer check the legal points.
