---
name: map-it
description: Shows wells, operators or formations on frac.fyi's map. Use whenever the user asks to map, plot, visualize or "show me where" wells are, or when a well, pad or company answer would benefit from a map.
---

# Map it

## Steps
- One well or pad: `show_well_on_map(licence, zoom)`. Use zoom 15 for a pad, 13 by default, and 8-10 for regional context.
- An operator's or formation's wells: `show_wells_on_map(by="operator" or "formation", value, colour_by)`, where `colour_by` is operator, formation, field, status, year or frac.
- Present the returned `map_url` as a link (or embed it if the client supports that).

## Choosing colour_by
- Operator map → colour by `formation` or `year`.
- Formation map → colour by `operator`.
- "When was it developed" → `year`. "What's producing" → `status`. "What's fracked" → `frac`.

## Rules
- Never write standalone HTML, Leaflet or Folium map files, and never use `tile.openstreetmap.org` tiles. Use these tools only.
- One question per map. Pick the colouring that answers the question asked.
