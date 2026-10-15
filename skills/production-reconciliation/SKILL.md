---
name: production-reconciliation
description: Reconciles frac.fyi wellhead production for a company with its reported production and explains the gap (working interest, geography, shrinkage, plant NGLs). Use for "X's production", "does frac.fyi match their MD&A", "why is frac.fyi production different from reported", "company BOE/d", "Q3 production for Y".
---

# Production reconciliation

## Steps
1. `resolve_entity` or `get_company_profile` to confirm which entities the name covers.
2. `reconcile_company_production(company, period)`, where the period is `"2025"`, `"Q3 2025"` or `"2025-07"`.
3. If the user has reported figures (from an MD&A or press release), pass `reported_boed`, `reported_gas_mmcfd`, `reported_liquids_bpd` and `reported_source`. Don't invent reported numbers. Ask for them or leave them out.

## Output
- frac.fyi operated production: raw wellhead BOE/d, and `sales_basis_boe_d` (sales gas + oil and condensate + plant NGLs) for Alberta and BC.
- Next to reported figures, the gap in BOE/d and %, broken into the basis differences the tool returns: geography, working interest, plant shrinkage, plant NGLs.
- A clear statement of which number is comparable to the reported figure.

## Rules
- Compare reported BOE with `sales_basis_boe_d`, never with raw wellhead BOE/d.
- frac.fyi counts 100% of operated wells. Non-operated interests are missing and partner shares are included.
- Assets outside AB, BC and SK (US, international) are not in the data.
