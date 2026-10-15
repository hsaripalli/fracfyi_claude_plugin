---
name: company-profile
description: Profiles an oil and gas operator across Alberta, BC and Saskatchewan, covering entities, well counts, formations, completion design, activity, production, land and acquisitions. Use for "tell me about Whitecap", "Tourmaline overview", "what does ARC do", "company profile", "where does X operate".
---

# Company profile

## Steps
1. `resolve_entity(name, type="company")` for the exact `operator_names` per province and aliases (BA codes, BC short codes).
2. `get_company_profile(company)` for licensees, operators, well counts and top formations by province.
3. `get_search_summary(query=company, kind="operator")` for counts by year, completion design by year, fields, providers and latest-month production.
4. Recent activity: `get_activity_feed(kind="frac", operator=<exact name>)` and `kind="permits"`.
5. Land: `get_land_holdings(company)`.
6. Deals: `get_transfers(company, days=365)`.
7. `explain_entity(name)` for knowledge-graph links: providers, sand suppliers, products.
8. Map: `show_wells_on_map(by="operator", value=company)`.

## Output
Sections for identity and entities, footprint (wells and formations by province), activity trend, completion design, production, land, deals and service providers. Include the map link.

## Rules
- Production is raw wellhead volume for 100% of each operated well, not the company's reported production. For reported-basis numbers, use `production-reconciliation`.
- Operator means the current licensee, so acquired wells count under the buyer for their whole history.
- `get_company_profile` matches by name prefix. Check that it didn't sweep in an unrelated company with the same prefix.
