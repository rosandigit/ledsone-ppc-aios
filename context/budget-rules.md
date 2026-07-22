# Budget Rules — LEDSone PPC AIOS
Last updated: 22.07.2026
Owner: Jathukulan

## Safety rule (applies to every budget decision below)
`/budget-check` always outputs a DRAFT recommendation. No budget is ever
changed automatically in Amazon Ads. Jathukulan reviews and applies every
change manually.

## Daily budget minimums
- **Sponsored Products — starting minimum:** £2/day
- **Sponsored Brands — minimum:** £2/day

## Special Rule budget overrides (Sponsored Products — order-volume based)
These override standard budget calculation when conditions are met:

| Rule | Condition | Orders (L30D) | Apply Budget |
|------|-----------|----------------|--------------|
| SR-1 | L30D ACoS ≤ 20% AND L7D ACoS ≤ 20% | 25–49 | £20 |
| SR-2 | L30D ACoS ≤ 20% AND L7D ACoS ≤ 20% | ≥50 | £25 |
| SR-3 | L30D ACoS ≤ 20% AND 20% < L7D ACoS ≤ 25% | 25–49 | £15 |
| SR-4 | L30D ACoS ≤ 20% AND 20% < L7D ACoS ≤ 25% | >50 | £20 |

**Tiebreaker (Orders = 50, matches both SR-3 and SR-4):** apply the
higher-priority rule based on rule objective. [Confirm exact priority order
if this comes up in practice — currently resolved conceptually, not numerically.]

## Stock gate
- Only actively scale PPC campaigns when stock is **≥21 units**.
- Below 21 units: monitor or reduce aggressive spend rather than scale.
- Below this same threshold, Operations Manager approval is required to add
  a product to a campaign at all.

## Stock Pause vs Product Re-Activation conflict
- If a SKU trips both rules in the same cycle: **apply the highest-priority
  rule and ignore the other until the next cycle.**
- [VERIFY] Which of the two is actually higher priority — Stock Pause
  (safety-first) or Re-Activation (revenue-first)? Needed before this can
  run unattended in a skill.

## Budget approval thresholds
| Increase amount | Who approves |
|------------------|-------------|
| Up to £[VERIFY]/day | Jathukulan can approve |
| £[VERIFY]–£[VERIFY]/day | MD approval required |
| Above £[VERIFY]/day | MD written approval required |

## Rollback procedure
- No automatic undo exists in Amazon Ads.
- If a budget change performs badly: open **Change History** in Amazon Ads,
  find the previous budget value, restore it manually.
- Log the rollback in `decisions/` the same day: campaign, old budget, new
  budget, reverted budget, reason.

## Non-UK marketplace values
- [VERIFY] Non-UK values for Spend Pause Rules 2–3 — currently blank in all
  source documents.

## Naming
- Campaign structure: **Campaign Type → Product Name → Target**
  e.g. `SP | Lamp Shade | Auto`
- Personal/team tag: **JD**
