---
name: licence-transfers
description: Tracks well licence transfers between companies (acquisitions, divestitures, asset deals) and summarizes what moved. Use for "recent acquisitions", "who bought whose wells", "licence transfers this week", "what did InPlay buy from Sifton", "deal summary", "M&A activity".
---

# Licence transfers

## Steps
1. List deals with `get_transfers(days, company)`. The default window is 7 days and the maximum 3660.
2. For one daily deal, `get_transfer_summary(from_operator, to_operator, date)` gives licences by formation, field and status, the deal wells' production, and each company's footprint before and after.
3. For the well list, `get_transfer_wells(from_operator, to_operator, date=...)` for a daily deal or `month=...` for a monthly one.
4. For a company's acquisition history, `get_related(entity=<company>, relation="acquired_licences_from")`.

## Output
- Deals, largest first: seller → buyer, licence count, date or month, and source (daily or monthly).
- Per deal: what moved (formations, fields, active vs inactive), production moved (latest month and trailing 12 months, BOE/d), and the buyer's footprint change.

## Rules
- Daily transfers are licensee changes detected in Petrinex since 2026-09-09. They are not official AER approvals and are dated when first seen.
- Monthly transfers come from production reporting and run about a month behind. Monthly deals have no summary, only a well list.
- Report `coverage.unavailable` gaps when they exist. Never present a gap as "no deals".
- Production is 100% raw wellhead, Alberta only, not the buyer's net share.
