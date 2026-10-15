---
name: area-scout
description: Scouts the activity and results around an Alberta township, covering who is drilling, what formations, how wells are completed and how they perform. Use for a township like 52-11W5 or 042-03W5, or "what's happening around TWP 42 RGE 3 W5", "scout this area", "offsets near this section".
---

# Area scout

## Steps
1. Convert the input to MRT without leading zeros: `042-03W5` becomes `42-3W5`.
2. `get_township_offsets(mrt, radius_km)` for wells, completions, operators and distances. The default is 15 km and the maximum 50 km.
3. For the dominant formation, `get_formation_type_curve(formation, fluid, year_from=<last 3-5 years>)` gives a performance baseline.
4. For Crown land in the same township, hand off to the `township-land` skill.
5. Map: `show_wells_on_map(by="formation", value=<dominant formation>)`.

## Output
- Activity: wells by operator and formation, and the latest spud and frac dates.
- Design: median lateral, stages and proppant per metre for recent wells, compared with older vintages.
- Performance: the area P50 against the formation type curve.
- The most active current licensees and their most recent wells.

## Data rules
- Operator means the current licensee. Acquired wells show under the buyer.
- Label every metric with its date basis: spud year, frac end year, or months on production.
- The current year is partial. Never compare its total with a full year.
