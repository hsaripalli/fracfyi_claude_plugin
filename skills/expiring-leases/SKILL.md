---
name: expiring-leases
description: Finds Alberta Crown leases reaching the end of their term, by company, township or basin-wide, which is land that may return to sale. Use for "what leases are expiring", "land coming off lease", "X's expiring leases", "expiries in 72-11W6 next year", "land likely to come back to sale".
---

# Expiring leases

## Steps
1. `get_expiring_leases(company, township, months, limit)`. `months` runs from 1 to 60 and defaults to 12.
2. To see whether a holder is likely to drill to continue its leases, check recent activity with `get_activity_feed(kind="permits", operator=<exact name>)` and `get_township_offsets` around the townships.

## Output
- Expiring leases, soonest first: lease, holder, township, rights, area, expiry.
- Totals by holder and by month or quarter of expiry.
- A flag for leases near recent permits or drilling by the same holder, since those are likely to be continued.

## Rules
- Alberta only. Saskatchewan publishes no lease expiry dates.
- Continued leases have no end date and are excluded. Say so.
- An expiring lease may be continued by drilling or production before expiry. "Expiring" is not "will be posted".
