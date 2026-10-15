---
name: upcoming-land-sales
description: Lists Crown land parcels posted for upcoming Alberta and Saskatchewan sales and puts them in context with nearby wells and leases. Use for "what's posted for the next land sale", "upcoming parcels", "what land is coming up near X", "posted parcels in the Montney", "withdrawn parcels".
---

# Upcoming land sales

## Steps
1. `get_upcoming_land_sales(province, sale_date)` returns each parcel's townships, hectares, rights, restriction codes, land keys and cancelled parcels.
2. For parcels the user cares about, add context:
   - `get_township_offsets(mrt)` for wells and activity around the parcel.
   - `get_township_land(township)` for current leases and past sales nearby, including past $/ha.
3. For a price guide, compare with recent `get_land_sales` results in the same townships.

## Output
- Sale date(s), parcel count, total hectares, and the split by rights and province.
- The notable parcels: township, hectares, rights, which formations are active nearby, and recent $/ha in the area.
- Withdrawn parcels (status CANCELLED), listed separately.

## Rules
- Who asked for a parcel to be posted is not public. Never guess.
- Land keys read as meridian, range, township, section, then quarter or LSD (e.g. `41401333NW`).
- Activity nearby is context, not a prediction of the sale price.
