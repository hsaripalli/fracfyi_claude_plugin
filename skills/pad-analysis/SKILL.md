---
name: pad-analysis
description: Analyzes every well on one surface location (pad), including completions, production, spacing and how the pad compares with its offsets. Use when the user gives a DLS surface location like 06-21-031-17W4 or asks "what's on this pad", "how did this pad perform", "pad summary".
---

# Pad analysis

## Steps
1. `get_pad(location)` returns the wells on the pad, frac totals, pad production and offset benchmarking.
2. Pick one horizontal on the pad and call `get_well_spacing(licence)` to get inter-well spacing, parent/child timing and stacked benches.
3. For design detail on a representative well, call `get_perf_clusters(licence)`.
4. `show_well_on_map(licence, zoom=15)` for one pad well.

## Output
- Pad overview: well count, formations, current licensee, frac dates (co-developed or staggered).
- Design table, one row per well: lateral (m), stages, stage spacing, proppant (t and kg/m), water (m3/m), provider.
- Production: pad total, per-well IP90 and 12-month cumulative.
- Versus offsets: pad P50 against the offset P50, with the ratio stated.
- Spacing: same-bench lateral spacing (m), and any wells more than 75 m above or below listed as separate benches.

## Data rules
- Compare per metre (kg/m, m3/m, BOE/d per 1000 m) whenever lateral lengths differ.
- Rates are per producing day, and production is 100% raw wellhead.
- A child well (fracked 90+ days after its neighbour) usually underperforms its parent. Name that as a cause before blaming the design.
- `get_well_spacing` is Alberta only.
