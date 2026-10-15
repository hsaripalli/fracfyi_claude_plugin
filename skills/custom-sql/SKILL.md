---
name: custom-sql
description: Answers frac.fyi questions that no dedicated tool covers by using verified queries first and then read-only DuckDB SQL. Use for custom filters, rankings, joins or statistics, e.g. "top 20 Montney wells by IP90 since 2023", "median proppant per metre by operator", "wells with lateral over 4000 m".
---

# Custom SQL

## Order of preference
1. A dedicated tool, if one fits. Check the other skills first.
2. A verified query: `list_verified_queries(category)`, then `execute_verified_query(query_id, params)`. A `query_id` is not a tool name.
3. `run_sql(query, limit)`, only when nothing above fits.

## Before writing SQL
- Call `get_database_schema` once per session and follow its querying rules, column formats and lateral-length rules.
- Resolve names with `resolve_entity` and filter with the exact `operator_names` (`operator IN (...)`), never `LIKE '%user text%'`.

## DuckDB rules
- Write DuckDB SQL, not SQLite.
- Months are 'YYYY-MM' strings. Convert them with `strptime(month, '%Y-%m')` before date math.
- Filter wells first, then join `production`. Never scan all of `production`.
- `all_wells` covers AB, BC and SK, so filter by `jurisdiction`. Join `production` on `jurisdiction` and `well_key`.
- Use `well_ip` for any initial-rate question (IP30/IP90/IP180 on producing hours).
- `frac_jobs.frac_service_provider` is the provider column.
- Missing values are `''` or NULL. Use `NULLIF(col, '')` and exclude them from averages, never coalesce them to 0.

## Output
Show the result as a table, then the SQL in a collapsed or code block so the user can reuse it. State the filters and row count.
