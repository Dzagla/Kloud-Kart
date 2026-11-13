# Investor questions: straight answers

For Nana to use in the board meeting. Each answer is short enough to say out loud. Where I could not verify something, the answer says so.

**1. "What is your data strategy?"**
Three things in order. Protect the website from reports, so we stop losing sales on Mondays. Agree one definition for each key number, so you never see two totals for the same week. Track every customer list, so we can prove what we deleted. Two hires carry it through the year. Everything bigger waits until the business needs it.

**2. "Why don't you have real-time analytics?"**
We do, where it matters: stock. Selling something we do not have costs us money immediately. Nothing else we do changes if a chart is a day old, so we are not paying for live charts on those. If someone shows us a decision that needs faster numbers, we will speed up that one number.

**3. "Why not a data warehouse or lakehouse, like other companies?"**
At about 4,000 orders a day and 40 GB, a second copy of the database does the same job for a fraction of the cost and effort. We have written down the point where that stops being true: about 12,000 orders a day, about 200 GB, or needing data from outside the website. At that point we revisit.

**4. "Your developer wants to buy a cloud data platform. Why are you overruling him?"**
He is not wrong that it would work. It is the wrong first step: it adds a monthly charge that grows with use, a skill nobody here has, and a legal question about sending customer data out of Ghana. The second server is already approved and solves the same problem sooner.

**5. "When will you do machine-learning forecasting?"**
Predictive algorithms need clean, reconciled transaction history to learn from. Until Operations and Finance align on baseline sales figures, any forecasting model would merely project accounting confusion into inventory purchasing. We get the data foundation right first, then evaluate forecasting feasibility in Q4.

**6. "What if a customer asks you to delete their data?"**
We have established an operational register requiring every customer export to have a named custodian and an explicit expiration date. When an erasure request arrives, it generates an audit checklist across all storage locations, requiring written sign-off before closing. We enforce a 30-day internal resolution target against the statutory 90-day limit. For legacy lists extracted prior to this protocol, a comprehensive discovery audit is scheduled in Q1.

**7. "Are you compliant with Ghana's Data Protection Act?"**
We are putting the primary controls in place immediately: centralized custody tracking, strict retention limits, and verifiable deletion routines. To ensure full compliance with Ghana's Act 843 and assess cross-border implications for our Nigeria expansion, we have scheduled a formal legal review with qualified counsel in Q1.

**8. "How do we know this is working?"**
By tangible operational milestones: Monday exports finish without causing site slowdowns; Finance and Operations present matching revenue figures for the same calendar week; and practice deletion requests complete within our 30-day target.

**9. "What if you are wrong?"**
Our exposure is minimal: the secondary server remains permanently valuable as a disaster-recovery failover for the live e-commerce site. Furthermore, every decision has explicit volume triggers that tell us exactly when and how to transition to enterprise platforms without wasting capital.

**10. "Why only two hires, and why that order?"**
The budget is two. The engineer comes first because reports cannot be moved, trusted or alerted on until someone can build and run them, and because today one developer holds all the knowledge. The analyst follows to own meaning and customer data once there is trusted data to own.
