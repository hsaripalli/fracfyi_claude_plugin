---
name: frac-supply-chain
description: Explores the frac supply chain knowledge graph, covering which products, chemicals, suppliers, sand sources and providers operators use, and what is in a product. Use for "who uses CalVisc", "what's in this friction reducer", "which operators use glutaraldehyde", "Trican's customers", "who supplies X's sand", or a CAS number like 7647-01-0.
---

# Frac supply chain

## Steps
1. `resolve_entity(name, type=...)`, where the type is product, supplier, purpose, chemical or company. Chemicals match by CAS number or name.
2. `explain_entity(name)` for what it is, its aliases and its top links.
3. `get_related(entity, relation, direction)` to go deeper:
   - Operator → products / suppliers: `used_product`, `used_supplier` (out)
   - Product → chemicals: `contains` (out). Chemical → products: `contains` (in)
   - Product → supplier: `supplied_by`. Product → purpose: `has_purpose`
   - Operator → frac provider / sand: `fracked_by`, `sand_from` (out). Provider → customers: `fracked_by` (in)

## Output
- What the entity is and its aliases.
- The strongest links, each with its weight (frac jobs or licences), first and last date, and source.
- A clear chain when the question spans hops (operator → product → chemical).

## Rules
- Link weight is a count of frac jobs or licences, not a volume.
- Disclosure is per frac job. A missing link means not disclosed, not "not used".
- Don't make health or safety claims about chemicals beyond what the data shows.
