# context

## Purpose
Reusable AI context: the stable reference facts and rules that skills read before producing any DRAFT recommendation.

## What belongs here
- Campaign, metric, keyword and reporting reference files
- Authoritative rule files (`bid-rules.md`, `budget-rules.md`)
- The canonical marketplace-routing registry (`marketplace-routing.md`)
- Files marked `[VERIFY]` until documented from a verified source

## Marketplace routing
`marketplace-routing.md` is the canonical operational marketplace-routing registry
for the approved Phase 1 architecture. **Read it first whenever marketplace routing
must be determined.** It is the authority on whether a marketplace is authorised for
routing; it holds no PPC business-rule content, and whether verified rule content
exists for a marketplace remains with that rule family's own owning file. This
README is navigation only — it is not a routing owner and states no routing rule.

## What should NOT be stored here
- Performance data or exports (use `evidence/`)
- Reports (use `reports/`)
- Decisions or approvals (use `decisions/`)
- Duplicated copies of rules stored elsewhere

## Owner
Jathukulan

## Status
Active
