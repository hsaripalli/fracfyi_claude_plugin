---
name: township-land
description: Gives the full Crown land picture for one township, covering active leases, holders, expiries and every parcel posted or sold since 2015. Use for "who holds the land in 72-11W6", "land in TWP 42 RGE 3 W5", "is there open Crown land here", "what sold in this township".
---

# Township land

## Steps
1. `get_township_land(township)`. It accepts `72-11W6`, `TWP 72 RGE 11 W6` or `(6-11-072)`.
2. For the leases ending soon (Alberta), `get_expiring_leases(township, months=24)`.
3. For drilling context, `get_township_offsets(mrt)`.

## Output
- Active leases: holder, participants, rights, area, expiry or continued status.
- The top holders by area in the township.
- Sale history: date, bonus, $/ha, buyer, and holder today.
- Leases expiring in the next 12-24 months, which may come back to sale.

## Rules
- The buyer at a sale is often a broker. The holder is the current owner. Show both.
- Saskatchewan township outlines are estimates (`outline_estimated = true`), and Saskatchewan publishes no lease expiry dates.
- Freehold (non-Crown) mineral rights are not in this data. Say so if the user asks who owns "all" the land.
