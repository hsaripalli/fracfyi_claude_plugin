---
name: play-profile
description: Profiles a formation, field, area or play, covering well counts by year, operators, completion design, providers, status mix and production. Use for "tell me about the Duvernay", "Clearwater overview", "who is active in Kakwa", "Pembina Cardium summary", "how big is the Charlie Lake play".
---

# Play profile

## Steps
1. `resolve_entity(name, type="formation" or "field")` for the standard name. Fields are per province, e.g. 'Kakwa (AB)'.
2. `get_search_summary(query, kind="formation" or "field" or "area")` for counts by year, design by year, top operators, fields, providers, status mix and latest-month production.
3. Performance: `get_formation_type_curve(formation, fluid, year_from=<recent>)`.
4. Activity now: `get_activity_breakdown(kind="frac", by="operator", formation=<exact>)`.
5. Map: `show_wells_on_map(by="formation", value=...)`.

## Output
- Size and activity: total wells, wells per year (licensed, spud, completed), and recent pace.
- Who: the top operators by recent completions.
- Design: the current median lateral, stages and intensity, against five years ago.
- Results: the type curve P50 and 12-month cumulative.
- Map link.

## Rules
- `get_search_summary` returns totals, not a well list. For wells, use `search_wells`.
- Production is Alberta raw wellhead for 100% of each well.
- Label each metric with its date basis.
