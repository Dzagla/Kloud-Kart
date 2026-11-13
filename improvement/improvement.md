# Improvement beyond the brief: Customer Data Protection Register and Deletion Protocol

## The problem it solves

Marketing periodically exports lists of roughly 300,000 customers for SMS and email campaigns, but Kloud Kart keeps no central record of where these files end up or who retains them. Under Ghana's Data Protection Act, 2012 (Act 843), customers hold statutory rights regarding personal data retention and erasure. If the Data Protection Commission (DPC) forwards a complaint regarding a customer who requested to be forgotten, the company faces a strict 90-day statutory window to prove full deletion.

Today, Nana cannot state how many copies exist, where they reside, or whether an external marketing agency still holds them on local drives. Simply purging the customer record from the primary MySQL database leaves duplicate personal records active across employee laptops, cloud storage, and agency systems. 

When board members or prospective investors review Kloud Kart's data governance, the acid test is straightforward: *if a customer demands their data be erased, can leadership verify with evidence that every copy was destroyed?*

## The operational governance model

To resolve this without procuring expensive compliance software or waiting for technical hires, this improvement establishes a structured, operational Customer Data Register and Deletion Protocol. It functions across four core operational controls:

1. **Mandatory Export Logging:** Whenever a customer list is exported from the reporting system, the custodian must log the operational purpose, exact storage destination, named custodian/holder, and an explicit retention end date (defaulting to 90 days for campaign lists). Exports with open-ended retention are strictly prohibited. To prevent the register itself from becoming a personal data risk, it logs only internal Customer IDs—never customer names, phone numbers, or email addresses.
2. **Standardized Deletion Protocol:** Receiving a formal erasure or DPC complaint triggers an immediate 30-day internal resolution cycle (comfortably within the 90-day legal limit). The register cross-references the customer ID to produce an exhaustive checklist: the primary transactional database plus every active, unexpired export copy containing that customer.
3. **Multi-Party Destruction Certification:** A deletion ticket cannot be closed based on informal assumptions. Every identified holder (internal marketing staff, database administrators, external marketing agencies) must confirm in writing that the target record has been purged from their system, logging the date, time, and specific action taken.
4. **Executive Compliance Review:** The protocol provides a monthly status review for Nana and executive leadership, highlighting active deletion requests, days remaining against statutory deadlines, and any distributed lists approaching or exceeding their retention expiry date.

Because the system tracks internal account identifiers rather than raw personal details, operational summaries can be reviewed across departments without privacy exposure.

## Procedural verification and stress-testing

The protocol rules were verified against eight operational scenarios:
- Ensuring every active list containing the subject customer appears on the mandatory checklist;
- Verifying that previously certified destroyed files are excluded from active tasks;
- Validating calculation of the 30-day internal operational SLA and 90-day legal deadline;
- Enforcing that a deletion case cannot be marked resolved while any custodian action remains unverified;
- Identifying and escalating cases exceeding statutory deadlines;
- Flagging any distributed marketing list that has passed its authorized retention window;
- Ensuring that management compliance reports expose no identifiable customer personal data;
- Rejecting any new data extraction request that lacks a binding future destruction date.

## Strategic value for operations

- **Reduces regulatory response from weeks to minutes:** Identifying all locations holding a customer's record becomes an immediate lookup rather than an uncertain cross-departmental hunt.
- **Provides defensible proof for regulators:** Produces a concrete, step-by-step evidence audit trail showing exactly who deleted what and when, satisfying Data Protection Commission inquiries.
- **Halts unmonitored data sprawl:** By tying every data export to an owner and an expiration deadline, customer data ceases to accumulate indefinitely on unmanaged machines.
- **Immediate implementation:** The process relies on operational discipline and clear oversight rather than complex engineering, meaning Operations can enforce it immediately while the technical hires are recruited.

## Constraints and operational boundaries

- **Historical copies:** The register systematically tracks lists exported from its inception forward. Uncovering legacy lists distributed over the past year requires the dedicated Q1 discovery inventory outlined in the roadmap.
- **Enforcement mechanisms:** A register documents declared data movements; it does not replace technical access controls. Restricting extraction permissions on the read replica remains the essential technical safeguard.
- **Legal and contractual boundaries:** While designed around the 90-day response window, Kloud Kart's management should have qualified Ghanaian legal counsel review the protocol alongside marketing agency contract clauses to guarantee full statutory alignment.
