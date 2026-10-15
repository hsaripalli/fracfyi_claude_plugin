---
name: well-search
description: Finds lists of wells matching criteria such as operator, formation, field, area, location text or frac provider. Use for "find Montney wells by Tourmaline in Kakwa", "list wells fracked by Trican", "wells near 08-18-052-11W5", "show me Duvernay slickwater wells".
---

# Well search

## Steps
1. `search_wells(query, operator, formation, field, area, limit, offset)` for a free-text search with optional filters. Page with `offset`.
2. If a filter name is unsure, call `resolve_entity` or `get_dimension_counts(kind)` to get the exact spelling.
3. For criteria the search can't express (IP above X, lateral over Y m, a date range), hand off to `custom-sql`.
4. For aggregates rather than a list, use `get_search_summary` instead.

## Output
- A compact table: licence, well name, current licensee, formation, field, surface location, frac date, lateral.
- The total match count and whether more pages exist.
- An offer to map the results or report on any one well.

## Rules
- The search covers Alberta horizontals and completions. For BC or Saskatchewan wells, use `run_sql` on `all_wells`.
- Don't dump hundreds of rows. Summarize, then offer to page.
