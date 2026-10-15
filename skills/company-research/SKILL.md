---
name: company-research
description: Researches an oil and gas company, especially a small, private or unfamiliar one that appears in new licences, transfers or land sales, by combining frac.fyi data with web search and public disclosures. Use for "who is B-32 Exploration", "new operator in the licence feed", "research this company", "who's behind this licensee", "is X public", "who runs X", "background on the buyer in this deal".
---

# Company research

Two halves: what the data shows the company doing, and what public sources say about who it is. Do both, then reconcile them.

## 1. What frac.fyi shows (do this first)
1. `resolve_entity(name, type="company")` for exact licensee names, BA codes and aliases. If nothing matches, try `suggest_entities` with part of the name.
2. `get_company_profile(company)` for licensees and operators by province, well counts and formations.
3. `get_activity_feed(kind="permits", operator=<exact name>)`, then `kind="drilling"` and `kind="frac"`, to find when it first appeared and what it is licensing.
4. For the new licences, `get_planned_design(licence)` and `get_township_offsets(mrt)` show what it is targeting and who its neighbours are.
5. `get_transfers(company, days=3660)` and `get_related(entity, relation="acquired_licences_from")` show whether it bought its way in, and from whom.
6. `get_land_holdings(company)` and `get_land_buyers` show whether it holds Crown land directly or is a broker's client.
7. `get_search_summary(query=company, kind="operator")` for production on wells it operates.

## 2. What public sources say
Use the client's web search and fetch tools. If none are available, say so and give the user the searches to run.

Search in this order and stop once the picture is clear:
- **The company's own website and news releases.** Search for the exact name plus "oil", "gas", "Alberta" or "exploration".
- **Securities filings.** If it's public in Canada, look on SEDAR+ (sedarplus.ca) for the annual information form, MD&A and material change reports, which show management, financing and acquisitions. Also check the TSX/TSXV and CSE listings, and EDGAR if it's US-listed.
- **Regulators.** AER and BC Energy Regulator licensee information and decisions, plus any compliance or enforcement actions. Saskatchewan Ministry of Energy and Resources notices.
- **Corporate registries.** OpenCorporates or the provincial registry summaries for incorporation date, jurisdiction and directors. Note that full Alberta registry searches are paid.
- **Trade press and deal news.** Daily Oil Bulletin, BOE Report, JWN, and press releases about financings or acquisitions.
- **People.** LinkedIn or news coverage of the founders and management, and their previous companies, which often explains the strategy (for example a team that sold a Montney company and started again).

## 3. Reconcile and report
- **Identity:** legal name, BA code, public or private (with ticker), head office, incorporation date, parent or affiliates.
- **People:** management and directors, and the companies they ran before.
- **Footprint:** wells, formations and areas from frac.fyi. Note when the first licence appeared and how activity has trended.
- **How it got there:** organic licensing, licence transfers (from whom), and land sale purchases or holdings.
- **Capital:** financings, backers and reported production if it is public.
- **Watch items:** regulatory actions, inactive-well liability signals, recent changes.
- **Sources:** a link for every public-source claim.

## Rules
- Keep data findings and web findings separate, and cite every web claim with its URL. Never state a web-sourced fact without a source.
- Name collisions are common, e.g. a numbered company or one that shares a name with a non-energy business. Confirm the match with a detail from the data, such as the BA code, area or formation, before using a web result.
- If public information is thin, as it often is for private companies, say so plainly. Never fill gaps with guesses about owners or backers.
- frac.fyi production is raw wellhead volume for 100% of operated wells, not the company's reported production.
- Report people's roles as the sources state them. Don't speculate about individuals beyond what's published.
