---
name: planned-completion
description: Forecasts the expected completion design, timing and likely frac provider for a well that is licensed or drilled but not yet fracked. Use for "what will this new licence look like", "expected frac design", "when will they frac it", "who will frac this well", "upcoming completions".
---

# Planned completion

## Steps
1. `lookup_well(licence)` to confirm the well is licensed or drilled but has no frac yet. If it is already fracked, use `completion-design` instead.
2. `get_planned_design(licence)` returns the P10-P90 lateral, stages, spacing, proppant and water from offsets, the design scaled to this well's estimated lateral, the operator's own recent design, providers, timing and the pad's wells.
3. Optional: `get_proppant_logistics(licence)` for sand volume and trucking.

## Output
- Expected design: the scaled P50 with the P25-P75 range, next to the operator's own recent design.
- Expected timing: median licence-to-spud and spud-to-frac, giving a date window.
- Providers: `providers_operator` and `providers_area` as recorded history.
- Other wells on the pad, which are likely co-developed.

## Rules
- Providers are history, not a prediction. Phrase it as "the operator has used X for its last N fracs in this formation".
- A licensed group formation (e.g. MANNVILLE GRP) matches its member formations. Say which ones were used.
- Present every forecast as a range with its basis, never as a single certain number.
