---
name: offset-benchmarking
description: Benchmarks one well's completion design and production against offset wells in the same formation and field. Use for "how does this well compare to its offsets", "is this well good", "offset analysis", "above or below average".
---

# Offset benchmarking

## Steps
1. `lookup_well(licence)` for formation, field, lateral and vintage.
2. `get_offset_wells(licence, limit=25)` for same-formation, same-field offsets with the target's completion intensity.
3. `get_formation_type_curve(formation, fluid, licence=<target>, field=<field>)` for the target's ratio to the P50 curve.
4. Optional: `run_well_comparison(licence_a=<target>, licence_b=<best offset>)` for a head-to-head.

## Output
- One line on where the well sits, e.g. "1.3x the P50 type curve at month 6; top quartile of 25 offsets."
- A design table comparing the target with the offset P25/P50/P75: lateral, stages, stage spacing, kg/m, m3/m.
- Production: the target's IP90 and 12-month cumulative against the offset distribution.
- Likely drivers: more or less intensity, longer lateral, vintage, parent/child status.

## Fair-comparison rules
- Compare the same formation and fluid only. Normalize by lateral length (per 1000 m) when laterals differ by more than 20%.
- Use full producing months, and rates per producing day.
- State the peer count and vintage range. Fewer than 5 peers is anecdotal, so say so.
- Missing completion data is not zero. Drop those peers from intensity statistics and report how many were dropped.
