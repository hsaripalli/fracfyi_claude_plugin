---
name: crown-land-sales
description: Reports Alberta and Saskatchewan Crown land sale results and trends, covering bonus paid, hectares, $/ha, top parcels, and who bought and who holds the land now. Use for "last land sale", "October land sale results", "how much was spent on land this year", "$/ha trend", "biggest parcels", "PNG vs oil sands".
---

# Crown land sales

## Steps
- Totals and trend since 2015: `get_land_sale_trends(province)`. This also returns the latest sale and the next posted one.
- One month or year's parcels: `get_land_sales(month="YYYY-MM")` or `get_land_sales(year=...)`, with optional `province` and `stream` (PNG, OS, OSH).
- Who bought: hand off to the `land-buyers` skill.

## Output
- Headline: total bonus, hectares sold, parcels sold of parcels offered, and average $/ha, compared with the same sale or period last year.
- Top parcels by bonus: township, hectares, rights (zone), $/ha, bidder, and holder today.
- Where the money went: the most active townships or areas.

## Rules
- The winning bidder is often a land broker. The holder is who holds the lease now. Always show both, and never call a broker the acquirer.
- Keep PNG and oil sands separate. Their $/ha are not comparable.
- The current year is partial, so compare year-to-date with the same months last year.
- Data starts in 2015.
