# Bid Rules — LEDSone PPC AIOS
Last updated: 22.07.2026
Owner: Jathukulan

## Safety rule (applies to every bid decision below)
`/bid-check` always outputs a DRAFT recommendation with the calculation shown.
No bid is ever changed automatically in Amazon Ads. Jathukulan reviews and
applies every change manually.

## Hard limits
- **Bid floor (minimum allowed bid):** £0.05
- **Bid ceiling (maximum allowed bid):** £1.00
- Any calculated recommendation outside this range is capped at the floor/ceiling
  and flagged as "capped — review manually" rather than shown as-is.

## Bid change mechanism
- **Standard method: multiplier-based** — ×1.125 (increase) / ×0.825 (decrease)
- Absolute increments (▲0.01 / ▼0.04 etc., as they appear in the Amazon rule
  configurators) are for fixed small manual fine-tuning only — not the default
  mechanism for `/bid-check` output.

## Sample size before acting
- **Default action threshold:** 15 clicks minimum
- **High-confidence threshold:** 25 clicks minimum — use for larger bid moves
  or when recommending a change on a Hero SKU campaign

## ACoS raise trigger
- **Standard trigger:** 20% ACoS — campaign is efficient enough to consider a
  bid/budget increase
- **Early scaling signal:** 15% ACoS — can support a smaller, earlier increase
  on strong performers, but is not the default threshold

## Sponsored Products placement adjustment cap (from Amazon configurator)
- Maximum: 35% | Minimum: 0%
- This is a separate lever from the base bid — it adjusts bid by placement
  (Top of Search, Rest of Search, Product Pages), not the keyword bid itself.

## Brand-term / competitor-term bids [PARTIALLY VERIFIED — needs one more number]
- **Brand-term bid/threshold:** [VERIFY]
- **Competitor-term bids:** strategy confirmed — start lower than standard bid,
  increase only after proven performance. Still needs:
  - [VERIFY] starting bid or % below standard bid
  - [VERIFY] definition of "proven" (recommend: matches the 15-click sample
    size threshold above + at least 1 order, pending confirmation)

## CPC guidance
- No fixed target CPC range exists in source documents.
- CPC should be derived from: max CPA (25% of sale price) and minimum True
  Margin (10%) — not set as a flat number. `/bid-check` should calculate an
  implied max CPC per-SKU from these two constraints rather than reference
  a static figure.

## Rollback procedure
- No automatic undo exists in Amazon Ads.
- If a bid change performs badly: open **Change History** in Amazon Ads,
  find the previous bid value, restore it manually.
- Log the rollback in `decisions/` the same day: campaign, keyword, old bid,
  new bid, reverted bid, reason.

## Still open — do not let these block Tier 1 build
- [VERIFY] Section B11 evidence naming standard (referenced 20+ times in
  handbook, not defined anywhere)
