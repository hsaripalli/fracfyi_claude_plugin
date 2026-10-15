# frac.fyi plugin for Claude

Western Canadian (Alberta, British Columbia, Saskatchewan) oil and gas intelligence from [frac.fyi](https://frac.fyi): wells, frac completions, production and decline curves, licence transfers and Crown land.

The plugin connects the frac.fyi MCP server (`https://mcp.frac.fyi/mcp`) and adds skills that turn its tools into analyst workflows.

## Install (Claude Code)

```
/plugin marketplace add hsaripalli/fracfyi_claude_plugin
/plugin install fracfyi@fracfyi
```

## Skills

| Area | Skills |
|---|---|
| Wells | identify-entity, well-report, well-search, well-comparison, map-it |
| Pads and offsets | pad-analysis, offset-benchmarking, area-scout, well-spacing |
| Production | decline-curve-analysis, type-curve, production-reconciliation |
| Completions | completion-design, planned-completion, proppant-logistics, completion-trends, cycle-times, frac-market-share, frac-supply-chain |
| Market | market-pulse, play-profile, company-profile, company-research, licence-transfers |
| Crown land | crown-land-sales, upcoming-land-sales, township-land, land-position, land-buyers, lease-lookup, expiring-leases |
| Power users | custom-sql |

## Example prompts

- `0514937`
- `Pad summary for 06-21-031-17W4`
- `Montney gas type curve for 2023 wells in Kakwa`
- `Who bought the most Crown land this year, and who holds it now?`
- `What did InPlay buy from Sifton?`

## Data and privacy

The skills send requests only to the frac.fyi MCP server, with one exception. The `company-research` skill uses the client's own web search and fetch tools, when they're enabled, to look up companies in public sources: company websites and news releases, SEDAR+ and EDGAR filings, regulator sites (AER, BC Energy Regulator, Saskatchewan Ministry of Energy and Resources), corporate registries such as OpenCorporates, trade press, and public profiles of company management. Those searches contain company names and the people named in public sources. No skill stores data.

frac.fyi logs each connector request (account ID, tool, time, duration and status) for about 7 days and does not log request contents. See the [privacy policy](https://frac.fyi/privacy).

## Data notes

Production is raw wellhead volume for 100% of each well, not a company's reported production. Rates are per producing day. `operator` is the current licensee. Missing values are not zero.
