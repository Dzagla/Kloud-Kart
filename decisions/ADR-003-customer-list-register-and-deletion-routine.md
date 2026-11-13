# ADR-003: Control customer lists through a register and a tested deletion routine

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Nana Adjei (Head of Operations)

## Context

Marketing exports a list of about 300,000 customers and nobody tracks the copies. Ghana's Data Protection Act, 2012 (Act 843) gives customers rights over their personal data and expects it to be kept secure and not held longer than needed. The brief says Kloud Kart has 90 days to respond to a Data Protection Commission complaint about a deleted customer's data. Deleting a customer from the main database does not delete the copies, so today the company could not prove it had done what it said.

The company also cannot simply stop Marketing exporting lists: campaign messages are sent from outside tools and by an agency. Nobody on the team has run a data-governance programme, and the one developer is already stretched. The control has to be light enough that people actually follow it.

## Decision

Every customer list that leaves the main database must be recorded in a register (who, what, where, for what purpose, and an end date), and the holder destroys it by that date. Customer lists are only released from the reporting copy of the database to named people, and each release is logged. When a deletion request arrives, the register produces the checklist of every copy to clean, and the request is closed only when every step is signed off, with a 30-day internal target inside the 90-day limit. The default end date for a campaign list is 90 days (my decision; Nana can shorten it).

The register and routine are built (see `improvement/`). Nothing in this decision depends on new software being bought.

## Alternatives considered

### Alternative A: Block customer exports entirely

- **How it would work:** Marketing sends all campaigns from inside a system Kloud Kart controls, so no list ever leaves.
- **Why it is attractive:** No copies means nothing to track and no way to leak a list.
- **Why rejected:** Marketing's message tools and the agency sit outside Kloud Kart. A total block would stop campaigns, and people under sales pressure would find a way round it, leaving copies that are invisible instead of tracked. It is a good long-term aim; it is not achievable in a year with this team.

### Alternative B: Written policy plus a yearly audit

- **How it would work:** Staff are told to delete lists after use, and once a year someone checks.
- **Why it is attractive:** Free and quick to roll out.
- **Why rejected:** A policy gives no way to answer "where is this customer's data?" on the day a complaint arrives. A yearly audit would find the problem after the 90 days are up. It also relies on everyone remembering, which is the situation that caused the problem.

## Consequences

- **What this buys:** A same-day answer to "which copies hold this customer?" and an evidence file showing each step, who did it and when. Copies stop growing silently because every export has an owner and an end date. Nana can show the status page to the board.
- **What this costs:** About 5 minutes per export, about 1 week of change management to get Marketing and the agency to follow it, and a standing duty for the second hire to review the register monthly. The agency contract needs a clause requiring it to delete on request, which needs a lawyer.
- **What it costs the client if I am wrong:** The danger is false comfort. If people export without registering, the register shows fewer copies than exist, and Kloud Kart could tell the Commission something untrue in good faith. To limit that, a quarterly spot-check compares what Marketing and the agency actually hold against the register, and the first 90 days include a search for existing copies. A missed copy found later is a small breach of process; a missed copy found by the Commission is a larger problem.
- **What would make me revisit this:** Two or more unregistered copies found in any spot-check; a deletion request closed late; Marketing moving to a campaign tool that can hold customers inside Kloud Kart's control (then Alternative A becomes realistic); or a complaint received before the register is fully populated.

## What this survives

- **A deletion complaint arrives next month, before the register is complete:** Partly. The register will not know about older copies, so the first 90 days include a sweep to find them. Until then a complaint response must include a manual search of known holders; the register shortens that, not eliminates it.
- **Several requests arrive at once:** Survives. Each is its own checklist; the lookup takes well under a second at 300,000 customers.
- **The agency or a staff member holding a copy leaves or changes:** Survives if the holder is recorded and the end date is enforced. The monthly review catches lists held by people who have left.
- **The Nigeria pilot adds customers:** Nigeria has its own data protection law, which I have not reviewed. The register works the same; whether Nigerian customers need different handling must be checked.
- **The second hire is delayed:** Survives for months, because the register needs only Nana or a named delegate to run it. It does not survive indefinitely without anyone owning it.
