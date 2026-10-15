---
name: identify-entity
description: Routes Western Canadian oil and gas identifiers to the right frac.fyi tool without asking what they are. Use whenever the user gives a bare 5-7 digit number (Alberta licence or BC WA number), a UWI like 100/05-18-042-03W5/0 or 100051804203W500, a 16-character Saskatchewan UWI, a DLS location like 05-18-042-03W5, a township like 042-03W5 or TWP 42 RGE 3 W5, a Crown lease number, or an operator, formation, field, frac provider or chemical name.
---

# Identify the entity, then act

Never ask what a number or location is. Recognize it and call the tool.

| Input | Meaning | First call |
|---|---|---|
| 5-7 digits, e.g. `0514937` | Alberta licence (5 digits may be a BC WA number) | `lookup_well(licence=...)` |
| `AB:04278`, `BC:53134` | Province-prefixed licence | `lookup_well(licence=...)` |
| `100/05-18-042-03W5/0`, `100051804203W500` | Alberta/BC UWI | `search_wells(query=...)`, then `lookup_well` |
| 16 chars, e.g. `141022701328W303` | Saskatchewan UWI | `lookup_well(licence=..., province="SK")` |
| `05-18-042-03W5` | Surface location (pad) | `get_pad(location=...)` |
| `042-03W5`, `42-3-W5`, `TWP 42 RGE 3 W5` | Township | Wells: `get_township_offsets(mrt="42-3W5")`. Land: `get_township_land(township=...)` |
| 6-10 digit lease number with a land question | Crown lease | `get_land_lease(agreement=...)` |
| Company, formation, field, provider, product, chemical, CAS number | Named entity | `resolve_entity(name=...)` |
| Partial text | Unknown | `suggest_entities(query=...)` |

## Rules
- A 5-digit number is read as a BC WA number. If the result says an Alberta licence with that number also exists, and context points to Alberta, retry with `province="AB"`.
- `get_township_offsets` takes `mrt` without leading zeros: `042-03W5` becomes `42-3W5`.
- Resolve names before filtering. Use the exact `operator_names` that `resolve_entity` returns. Never use a LIKE on what the user typed.
- After identifying the entity, hand off to the matching skill: `well-report`, `pad-analysis`, `area-scout`, `company-profile`, `township-land`.
