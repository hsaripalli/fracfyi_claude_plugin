---
name: market-pulse
description: Gives a weekly or monthly snapshot of WCSB activity, covering active rigs, new licences, rig releases, frac disclosures, top operators and formations. Use for "what happened this week", "basin activity", "market update", "weekly frac report", "how busy is the basin", "rig count".
---

# Market pulse

## Steps
1. `get_activity_summary(days=7)`, or the window the user asked for.
2. Trend context: `get_activity_trend(kind="frac", months=24)` and `kind="drilling"` / `"permits"`.
3. Leaders this window: `get_activity_breakdown(kind="frac", by="operator")` and `by="formation"`.
4. Notable events: `get_activity_feed(kind="frac", limit=20)` and `kind="transfers"`.

## Output
A short brief with:
- Headline numbers for the window, compared with the prior window or the same period last year.
- Top operators and formations.
- Three to five notable events (large pads, new entrants, deals).
- One line on the trend direction.

## Rules
- Compare like windows: a week with a week, a partial month with the same days last year.
- Disclosure lags activity, so recent weeks fill in over time. Say so when the latest week looks low.
- Keep it short. This is a pulse, not a report.
