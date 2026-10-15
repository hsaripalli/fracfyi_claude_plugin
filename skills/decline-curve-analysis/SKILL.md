---
name: decline-curve-analysis
description: Runs and explains Arps decline curve analysis (EUR, remaining reserves, current decline) for one well. Use for "DCA", "decline curve", "EUR", "reserves", "how much will this well make", "what is it declining at", "remaining life".
---

# Decline curve analysis

## Steps
1. `run_dca(licence, series=true)`. Pass `fluid_type` only when the user specifies one, because by default the larger stream in BOE is picked.
2. If the result says there are fewer than 6 full producing months, switch to `get_formation_type_curve(formation, fluid, licence)` and present a type-curve-based outlook instead.
3. If the fit confidence is low or there are warnings, look at `get_production_history(licence)` for shut-ins, workovers or step changes.
4. If the user names a start month (for example after a refrac or a long shut-in), rerun with `decline_start=<producing month>`.

## Output
- P50 EUR with the P10-P90 range, units included (e3m3 gas, m3 oil, or the BOE equivalent if requested).
- Current rate per producing day and current annual decline.
- Remaining reserves and remaining life to the economic limit.
- Fit confidence and every warning, stated plainly.
- If charting, plot history, fit and the P10/P50/P90 forecast on one time axis, with a log-rate axis if the user wants.

## Rules
- The method is an Arps hyperbolic fit on producing-day rates with a 6%/yr terminal decline and a bootstrap P10/P50/P90. State it.
- The same well gives the same answer. Do not rerun hoping for a different result.
- This is a statistical fit on public data, not a booked reserve. Say so if the user is treating it as one.
