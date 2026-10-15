---
name: frac-market-share
description: Reports pressure pumper, sand supplier and fluid system market share and operator league tables for completions. Use for "frac market share", "who is the biggest pressure pumper", "Trican vs Calfrac", "sand supplier volumes", "top operators by wells fracked", "provider rankings".
---

# Frac market share

## Steps
1. One calendar year: `get_ytd_benchmarks(year)` for operator, formation, pressure pumper, sand supplier and fluid system rankings.
2. A custom window or filters: `get_activity_breakdown(kind="frac", by="provider", metric=..., formation=..., month=...)`. The metric is wells, stages, proppant or water.
3. Over time: `get_frac_timeline(group_by="provider", days=730)`.
4. A provider's customers: `get_related(entity=<provider>, relation="fracked_by", direction="in")`.

## Output
- Share by wells, plus share by stages or proppant if asked, since the rankings differ.
- The change versus last year over the same months.
- For one provider: its top customers and formations.

## Rules
- State the metric. Share by wells and share by proppant tonnes can rank providers differently.
- The current year is partial. Use year-to-date against the same months last year.
- 'Unknown' provider means not disclosed. Show it as its own row and don't spread it across providers.
- Frac data is Alberta only.
