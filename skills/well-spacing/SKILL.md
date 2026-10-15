---
name: well-spacing
description: Analyzes lateral-to-lateral spacing, parent/child relationships and stacked benches for an Alberta horizontal from directional surveys. Use for "well spacing", "inter-well distance", "parent child", "is this a child well", "how many wells per section", "stacked development", "frac hits".
---

# Well spacing

## Steps
1. `get_well_spacing(licence)` returns the nearest same-bench lateral on each side, up to 40 neighbours within 1 km, and their offsets and timing.
2. For a 3D picture, `get_wellbore(licence)` returns the trajectory and nearby wellbores.
3. To see whether a child well underperforms, call `get_formation_type_curve(formation, fluid, licence)` for the child and for its parent, then compare the ratios to P50.

## Output
- Same-bench spacing to the left and right (m, looking from heel to toe).
- Neighbours grouped as same pad / other pad, and as parent (fracked 90+ days earlier) / child (90+ days later) / co-developed (within 90 days).
- Stacked benches: neighbours more than 75 m above or below, listed separately as other zones.
- Overlap length for each close neighbour.

## Rules
- Only same-bench neighbours (within 75 m vertically) count as zone spacing.
- Alberta only. For BC or Saskatchewan wells, say the survey data isn't available.
- Spacing shows correlation, not cause. Present parent/child performance gaps as evidence, not proof.
