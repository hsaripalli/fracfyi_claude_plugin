---
name: proppant-logistics
description: Estimates sand volume, truckloads, frac pace and the nearest transloaders for a pad. Use for "how much sand will this pad need", "truck count", "proppant logistics", "nearest transload", "sand haul distance", "stages per day".
---

# Proppant logistics

## Steps
1. `get_proppant_logistics(licence, radius_km=25, years=5)` for wells on the pad, offset P10/P50/P90 proppant per well and per metre, stages per well, stages per day, nearest transloaders and default truck assumptions.
2. If the pad isn't fracked yet, `get_planned_design(licence)` gives a better per-well lateral estimate.
3. To place transloaders in context, `get_related(entity=<field>, relation="nearest_transload")`.

## Calculation
- Pad sand = wells on pad × P50 proppant per well. Give the P10 and P90 bounds as well.
- Truckloads = pad sand ÷ payload per truck (use the tool's default and state it).
- Frac days = (wells × stages per well) ÷ stages per day.
- Trucks per day = truckloads ÷ frac days.
- Haul distance: straight-line km to the nearest transloader, flagged as straight-line, since road distance will be longer.

## Rules
- Show every assumption and its basis, and let the user override payload, pace or design.
- Round to sensible precision (whole trucks, tonnes to the nearest 100).
