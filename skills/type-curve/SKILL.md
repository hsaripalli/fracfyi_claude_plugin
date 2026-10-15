---
name: type-curve
description: Builds P10/P50/P90 type curves for a formation, field or vintage and places wells on them. Use for "Montney type curve", "Duvernay oil type curve 2022 wells", "what does a typical Cardium well make", "P50 12-month cumulative", "compare vintages".
---

# Type curve

## Steps
1. If the formation name is unsure, call `resolve_entity(name, type="formation")`.
2. `get_formation_type_curve(formation, fluid, field, year_from, year_to, horizontal_only=true)`.
   - Gas is in e3m3/d. Oil is oil plus condensate in m3/d.
   - Vintage comparison: one call per `vintage_year`, then compare the P50 curves.
   - Pass `licence` to place a specific well on the curve.
3. Raise `min_wells` if the tail of the curve is noisy, and say which months were cut.

## Output
- Peer group definition: formation, field, fluid, vintage range, horizontal-only flag, and well count per month.
- P10/P50/P90 rate by month on production, and the 12-month cumulative P10/P50/P90.
- For a placed well, its ratio to the P50 at each month.

## Rules
- Use one fluid per curve and do not mix gas and oil wells on one curve.
- The x-axis is months on production (full producing months only), not calendar time.
- Peer counts fall at later months. Show the count and stop where it drops below `min_wells`.
- For a vintage comparison, keep the same months-on-production window for each vintage so the comparison is fair.
