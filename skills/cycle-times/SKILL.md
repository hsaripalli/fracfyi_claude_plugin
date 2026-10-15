---
name: cycle-times
description: Measures drilling and completion cycle times (licence to spud, spud to rig release, rig release to frac, frac duration) for an operator, formation or field. Use for "how long from licence to spud", "drilling days", "time to frac", "is X getting faster", "spud to on-stream", "cycle time benchmarks".
---

# Cycle times

## Steps
1. `get_cycle_times(operator, formation, field)` for medians, percentiles and the per-year trend. Pass `interval` for one interval's distribution.
2. With no scope, the result also includes `year_to_date`: this year against the same months last year.
3. To compare operators, call once per operator with the same formation.

## Output
- The median and P25-P75 for each step, in days.
- The trend by year.
- For comparisons, a table with one row per operator and one column per step.

## Rules
- Values are trimmed to the 5th-95th percentile. Say so.
- The per-year trend groups by the year a step started, so the current year looks fast. For this year against last year, use `year_to_date`.
- Resolve operator and formation names first with `resolve_entity`.
