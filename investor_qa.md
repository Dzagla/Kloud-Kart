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
Not this year. Forecasting learns from history. If the history is disputed, we forecast the dispute. We spend this year making the numbers agreed and trusted, then test at year end whether the data is clean enough to try. The test is part of the plan.

**6. "What if a customer asks you to delete their data?"**
We have a register of every customer list that leaves the company, with its holder and an end date. When a request arrives it produces the list of every copy to clean, and the request closes only when each is signed off. We aim for 30 days against the 90-day limit. I should be honest: lists copied before the register started are still being found. A search for them is in the first 90 days.

**7. "Are you compliant with Ghana's Data Protection Act?"**
I would not claim that yet. The plan puts in the controls the law points to: knowing where customer data is, keeping it only as long as needed, and being able to prove a deletion. Whether Kloud Kart meets every requirement needs a lawyer's review, which is in the plan. The cloud-hosting and Nigeria questions need that review too.

**8. "How do we know this is working?"**
By things you can check: Monday exports stop slowing the site; Finance and Operations show the same number for the same week; a practice deletion request finishes inside the target. The year-end review compares each against the measurements taken in the first month.

**9. "What if you are wrong?"**
Then we lose one server and some weeks, and the server stays useful as a backup. Each decision has a written trigger for revisiting it, and a note on what it costs if it was the wrong call.

**10. "Why only two hires, and why that order?"**
The budget is two. The engineer comes first because reports cannot be moved, trusted or alerted on until someone can build and run them, and because today one developer holds all the knowledge. The analyst follows to own meaning and customer data once there is trusted data to own.
