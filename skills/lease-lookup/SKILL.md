---
name: lease-lookup
description: Looks up one Crown lease (agreement) by number, covering its holder, participants, term, expiry, rights and the land sale that created it. Use when the user gives a lease or agreement number like 5426100052 or 108975, or asks "who holds lease X", "when does this lease expire".
---

# Lease lookup

## Steps
1. `get_land_lease(agreement)`.
2. For context on the lease's township, `get_township_land(township)`.

## Output
- Holder today, participants, rights (zones), area (ha).
- Term start, continuation date, expiry, and whether a transfer is pending.
- Originating sale: date, bonus, $/ha, buyer, parcel.

## Rules
- A lease sold before 2015 has no sale on record, only its lease dates. Say so rather than reporting "no sale".
- The buyer is often a broker. The holder is the current owner.
- A continued lease has no expiry date. Report it as "continued", not as an unknown expiry.
