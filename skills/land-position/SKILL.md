---
name: land-position
description: Summarizes a company's Crown land position in Alberta and Saskatchewan, covering leases, area, townships, expiries, continued leases and land sale purchases. Use for "Tourmaline's land position", "how much land does X hold", "where is X buying land", "what leases does X have expiring", "biggest land holders".
---

# Company land position

## Steps
1. `resolve_entity(name, type="company")` if the name is uncertain.
2. `get_land_holdings(company, province)` for lease count, area, townships, leases expiring within 12 months, continued count, the lease list and purchases from land sales.
3. Alberta expiries further out: `get_expiring_leases(company, months=24)`.
4. To rank against peers, `get_land_holders(province, limit=25)`.
5. To compare land with drilling, `get_search_summary(company, kind="operator")` shows where the company actually drills.

## Output
- Total leases and hectares by province and rights type.
- The core areas: the top townships by area.
- The expiry profile: what expires in 12 and 24 months versus what is continued.
- Recent acquisitions from land sales, with dates and $/ha.
- The company's rank among the largest holders.

## Rules
- Holdings count the company as designated representative or as participant. Say which, since participant area is not a net working interest.
- Continued leases have no end date and are not "expiring".
- Saskatchewan has no lease expiry dates.
