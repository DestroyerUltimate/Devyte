# Security Specification for DEVYTE

## Data Invariants
1. A registration must have an email and a name.
2. Admins are defined in the `/admins/` collection by their UID.
3. Public data (protocols, operators, council) is read-only for the public and editable only by admins.

## The "Dirty Dozen" Payloads
1. Create a protocol as an unauthenticated user (Denied).
2. Create a registration without an email (Denied).
3. Update an operator's bio as an unauthenticated user (Denied).
4. Read all registrations as a common authenticated user (Denied).
5. Delete a protocol as a common authenticated user (Denied).
6. Create an admin document as a common user (Denied).
7. Inject a 2MB string into a registration name (Denied).
8. Update a registration's timestamp (Denied - immutable).
9. Create a registration with a future timestamp (Denied).
10. Update an operator and add a shadow field `isVerified` (Denied).
11. Update an operator and change their `name` but not `codename` (Allowed for admin).
12. Delete an admin document (Denied - only root or other system process).

## Test Runner (firestore.rules.test.ts)
... (omitted for brevity in this step, but follows these rules)
