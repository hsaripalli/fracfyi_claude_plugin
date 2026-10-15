---
name: well-comparison
description: Compares two or more wells side by side on geometry, completion intensity, frac provider, production and EUR. Use for "compare 0514937 and 0498765", "which well is better", "A vs B", "why did this well outperform that one".
---

# Well comparison

## Steps
1. For two wells, call `run_well_comparison(licence_a, licence_b, fluid="auto")`.
2. For three or more, call `lookup_well` and `run_dca` for each, plus a `run_sql` on `well_ip` for IP rates, then build the same table yourself.
3. If both wells are in Alberta, `get_well_spacing` on each tells you whether either one is a child well.

## Output
A table with one column per well and these rows: current licensee, formation, spud and frac year, lateral (m), stages, stage spacing (m), proppant (kg/m), water (m3/m), provider, IP90, 12-month cumulative, P50 EUR. Then two or three sentences on what explains the difference.

## Rules
- If the wells are in different formations or produce different fluids, warn that the comparison is not like for like.
- Normalize production per 1000 m of lateral when laterals differ by more than 20%.
- When vintages differ, compare the same months on production.
- Missing data is "not reported", never zero, and is never a reason to call a well worse.
