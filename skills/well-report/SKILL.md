---
name: well-report
description: Builds a complete one-well report (header, completion, production, IP rates, map) from frac.fyi. Use when the user asks about a single well by licence, UWI or well name, e.g. "tell me about 0514937", "well report for this UWI", "what is this well producing".
---

# Well report

## Steps
1. `lookup_well(licence)` returns the header, the Alberta frac jobs and the monthly production.
2. Alberta horizontals only: `get_perf_clusters(licence)` for stages, stage spacing and clusters per stage.
3. IP rates: run `run_sql` on `well_ip` (`IP30`, `IP90`, `IP180`, 12-month cumulative). Call `get_database_schema` first if the column names are unknown.
4. If the well has 6 or more full producing months, run `run_dca(licence)` for EUR and current decline.
5. `show_well_on_map(licence)` and include the `map_url`.

## Report layout
- **Header:** name, current licensee, surface and bottom-hole location, formation, fluid, status, spud and rig release dates, TD, lateral length.
- **Completion:** frac dates, provider, stages, proppant (t, kg/m), water (m3, m3/m), fluid system.
- **Production:** IP30/IP90/IP180, 12-month cumulative, latest month, cumulative to date.
- **Outlook:** DCA P50 EUR, P10-P90 range and fit confidence (only if step 4 ran).
- Map link.

## Data rules
- `operator` is the current licensee, not the operator at drilling or completion. Say "current licensee".
- Rates are per producing day (hours / 24). The first month is usually partial, so never divide by calendar days.
- Production is raw wellhead volume for 100% of the well, not a company's share.
- Missing values are `''` or NULL, and 'Unknown' means not disclosed. Report them as "not reported", never as 0.
- BC and Saskatchewan wells have no frac data yet, and Saskatchewan has no coordinates. Say so instead of leaving a gap.
