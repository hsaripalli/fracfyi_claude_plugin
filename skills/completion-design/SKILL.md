---
name: completion-design
description: Explains how a well, operator or formation is being completed, covering stages, stage spacing, clusters, proppant and water intensity, fluid systems and providers. Use for "how is this well fracked", "completion design", "stage spacing", "clusters per stage", "proppant per metre", "how does Tourmaline complete Montney wells".
---

# Completion design

## One well
1. `lookup_well(licence)` for frac jobs: provider, proppant, water, fluid system.
2. `get_perf_clusters(licence)` for the completion method, stage count, stage spacing, clusters per stage, shot density and treatment dates. Add `include_events=true` only when the user wants interval-level detail.

## An operator or formation
1. `resolve_entity` for the exact name.
2. `get_search_summary(query, kind="operator" or "formation", frac_only=true)` for completion design by year.
3. `get_macro_trends(formation=..., operator=...)` for the annual trend in lateral, stages, proppant and water.
4. For medians and percentiles, run `run_sql` on `frac_wells` and `perf_wells` (check `get_database_schema` first).

## Output
- Intensity metrics, always per metre: kg/m proppant, m3/m water, stage spacing (m), clusters per stage.
- The trend over vintages, with the year basis labelled as frac end year.
- The providers and fluid systems used.

## Rules
- A frac belongs to the year of its end date, and the current year is partial.
- Use medians for "typical" values, since averages are skewed by outliers.
- 'Unknown' means not disclosed. Exclude those wells from statistics and report the count excluded.
- Frac data is Alberta only.
