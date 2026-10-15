---
name: land-buyers
description: Ranks who is buying Crown land and unmasks broker purchases by tracing which company holds the leases today. Use for "who bought the most land this year", "top land buyers", "who is behind this broker", "which company is the broker buying for", "land spend by company".
---

# Land buyers

## Steps
1. `get_land_buyers(from_year, to_year, province, limit)` for buyers ranked by bonus, holders today, and each buyer → holder pair with its parcels.
2. For one lease, `get_land_lease(agreement)` gives the full history.
3. For one holder's whole position, hand off to `land-position`.

## Output
- Ranked buyers: bonus paid, hectares, parcels and average $/ha.
- The broker → holder map: for each broker, the companies that now hold its parcels, with parcel count and bonus.
- The real spenders: bonus re-aggregated by holder today, not by bidder.

## Rules
- A changed holder usually means a broker's client, but it can also be a company rename, a joint bid now held by one partner, or a later sale. Say "now held by", not "bought for", unless the pattern is clear.
- Saskatchewan and Alberta data start in 2015.
- The current year is partial.
