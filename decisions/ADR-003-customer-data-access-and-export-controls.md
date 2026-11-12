# ADR-003: Restrict Customer-Data Access and Manage Exports Through the Centralised Dashboard

**Status:** Accepted  
**Decision owner:** Kloud Kart

## Context

The case states that Marketing exports a customer list of approximately 300,000 people without tracking copies. This creates a risk when Kloud Kart needs to locate and manage copies of a customer's personal data, including in response to a deletion request.

ADR-002 establishes a centralised dashboard with organisation-wide metric definitions and role-based access. The dashboard is also intended to provide a controlled point through which authorised users can view or export information relevant to their responsibilities.

## Decision

Customer-list access will be restricted to authorised persons through the centralised dashboard. Access will be governed by user roles and permissions.

The dashboard will restrict downloading or extracting customer information to other systems. Customer-list exports should only be available where the user is authorised and the export is permitted by the applicable access rules.

## Decision rationale

- Restricting access reduces the number of people who can view or export customer information.
- Using a centralised access point makes it easier to apply consistent permissions than allowing uncontrolled exports from separate working copies.
- Limiting downloads and extraction to other systems is intended to reduce the creation of untracked customer-data copies.
- This approach complements the shared dashboard and metric definitions in ADR-002.
- Keeping customer-data access within the existing reporting approach avoids introducing a separate data platform solely to manage dashboard access.

## Alternatives considered

### Alternative A: Allow users to export customer lists independently

This offers flexibility to teams that need customer information for their work.

It was not selected because independent exports can create copies in locations that are difficult to identify, monitor, and manage. This is inconsistent with the objective of reducing untracked customer-data copies.

### Alternative B: Permit broad access and rely on users to manage exported copies responsibly

This requires fewer restrictions at the point of access.

It was not selected because it relies heavily on individual practices and does not provide a consistent organisation-wide way to limit access and copying.

## Consequences

### Benefits

- Customer-list access is limited to authorised users.
- Role-based permissions provide a consistent basis for controlling access.
- Restrictions on downloads and extraction are intended to reduce uncontrolled copies.
- The approach uses the centralised dashboard rather than creating another data platform.

### Costs and risks

- Kloud Kart must define, assign, review, and maintain user roles and permissions.
- Some legitimate business activities may require an approved export process.
- Restrictions in the dashboard cannot by themselves locate or delete copies that were exported before the controls were introduced.
- The company still needs to identify existing copies and establish how deletion requests will be handled across all locations where personal data is held.
- The dashboard and its access controls must be tested; a role-based interface alone does not guarantee that data cannot be retrieved through other routes or systems.

## What this buys, what it costs, and what happens if it is wrong

This decision buys a more controlled way to view and export customer information and is intended to reduce the creation of untracked copies. It costs time to define permissions, implement restrictions, and manage legitimate exceptions.

If customer data can still be extracted through other routes, or existing copies cannot be located and managed, the dashboard controls will not be sufficient on their own. Kloud Kart will need to review the wider data-handling process and the systems and locations in which customer information is stored.

## Revisit conditions

Reconsider this decision if business operations require additional approved export routes, if users can bypass the dashboard restrictions, if access permissions are difficult to maintain, or if the approach does not allow Kloud Kart to locate and manage personal-data copies when required.

## What this decision survives

The decision establishes a controlled access approach for future dashboard use. It does not, by itself, resolve the status of historical exports or guarantee that every existing copy can be located or deleted. Those matters require a separate inventory and operational process.
