---
name: completion-trends
description: Shows how completions have evolved over the years (well counts, lateral length, stages, proppant and water intensity), basin-wide or for a formation or operator. Use for "are laterals getting longer", "proppant intensity trend", "Montney completion evolution", "how has X's design changed since 2016", "completed wells per year".
---

# Completion trends

## Steps
1. `get_macro_trends(formation, operator, from_year, to_year)` for annual and monthly completed wells, proppant, water, average stages and average lateral.
2. For per-well medians or per-metre intensity, run `run_sql` on `frac_wells` grouped by frac end year. Check `get_database_schema` for the columns and lateral rules first.
3. For operators side by side over time, `get_frac_timeline(group_by="operator")`.

## Output
- A table or line chart by year: wells, median lateral, median stages, median kg/m and m3/m.
- Percent change from the start of the window to the latest full year.
- One or two sentences on what changed.

## Rules
- A frac belongs to the year of its end date. Label the x-axis "frac end year".
- The current year is partial. Mark it, or exclude it from the trend line.
- Prefer medians per well and per metre to basin totals when describing design.
- Alberta only.
