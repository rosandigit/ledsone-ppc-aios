# Product Pause Rules

Canonical **business-rule** document for **Spend Basic Product Pause** in the
LEDSone Amazon PPC AIOS. It is the single authoritative source for
product-performance pause decision logic. It documents **business decision logic
only** — not software, dashboards, schedulers, or automation.

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

> The primary evidence for these rules is a developer specification for an
> automated rule-configurator dashboard whose source action is "Pause Product
> (ASIN)" executed automatically. This document deliberately extracts the
> **business rule** and discards the automation/execution framing. Within the
> AIOS, each rule can only ever produce a **DRAFT recommendation to pause a
> product** that Jathukulan (or the authorised PPC Executive) reviews and applies
> manually in Amazon Ads. **The AIOS itself never pauses a product.**

---

## Purpose

This document exists so that any person or AI skill in the repository evaluates
**product-level advertising-performance pause** decisions the same way, from one
canonical definition. It answers a single business question — *when should a
product be recommended for pause because of advertising performance?* — using
only the logic and values stated in the source PDF.

The source defines **three distinct pause rule families**, each selected by a
different **order-activity pattern** (whether the product has orders in the last
30 days and/or the last 7 days). This document preserves those three families as
separate rules and never merges them, even though all three share the same
underlying action (pause the product).

---

## Scope

**This document covers:**

- The three Product Pause rule families as stated in the source PDF — Rule 1
  (ROAS Based Pause), Rule 2 (ROAS & Spend Based Pause), Rule 3 (Spend Based
  Pause — Zero Orders): their trigger scope, conditions, action, constraints,
  exceptions, product-price logic and the marketplace parameter values the PDF
  explicitly documents.
- The shared **date-based data-window logic** that selects which data window each
  rule evaluates.
- The business inputs and decision outcomes another LLM or PPC Executive needs to
  make or validate a pause decision as a DRAFT recommendation.

**This document deliberately does NOT cover:**

- Any software implementation — dashboard layout, configurator screens,
  Create/Edit/Delete/Apply operations, the automation engine, the scheduling
  engine, audit logging, or UI behaviour (all present in the source PDF and
  intentionally excluded).
- KPI **definitions** (ROAS, ACoS, CTR, CVR) — owned by
  `context/target-metrics.md` and referenced, never redefined here.
- Standard daily budget rules, budget minimums, the stock gate, Special Rules
  SR-1…SR-4, approval bands and rollback — owned by `context/budget-rules.md` and
  referenced, never restated here.
- Bid mechanics (floor, ceiling, multipliers, click sample sizes) — owned by
  `context/bid-rules.md` and referenced, never restated here.
- Any runtime product master data — actual ASINs, SKUs, parent/child records,
  campaign mappings, stock records or product-specific prices. Product master and
  runtime information belongs with the appropriate evidence/product-data owner,
  including `context/amazon-vendor-bridge.md` where applicable.

---

## Business Question

**"When should a product be recommended for pause because of advertising
performance?"**

Per the source PDF, a product should be **recommended for pause (as a DRAFT
recommendation)** when it matches the conditions of one of the three rule
families for its current order-activity pattern, evaluated against the correct
data window, and no documented exception applies. The three families are mutually
selected by order activity:

| Rule | Selected when | Basis of pause |
|------|---------------|----------------|
| Rule 1 — ROAS Based Pause | Last 30D Orders > 0 **AND** Last 7D Orders > 0 | ROAS bands + order counts |
| Rule 2 — ROAS & Spend Based Pause | Last 30D Orders > 0 **AND** Last 7D Orders = 0 | ROAS + (clicks) or (spend vs price tier) |
| Rule 3 — Spend Based Pause (Zero Orders) | Last 30D Orders = 0 **AND** Last 7D Orders = 0 | clicks + spend vs price tier |

If a product matches a rule's pause conditions and no exception applies, the DRAFT
recommendation is **Pause Product (ASIN)**. Otherwise, **No Action**.

---

## Dependencies

| Dependency | Why it exists |
|------------|---------------|
| `context/target-metrics.md` | Owns the **definitions** of ROAS and ACoS as KPIs (`ROAS = Ad Sales ÷ Ad Spend`). These rules use ROAS values as *trigger thresholds*; the metric they refer to is defined there. This document references that definition and does not redefine ROAS. |
| `context/budget-rules.md` | Owns **Standard Budget Rules**, the **stock gate**, approval bands and rollback discipline. It already records (Non-UK marketplace values section) that non-UK values for "Spend Pause Rules 2–3" are blank in all source documents — the same rules documented here. Any pause this rule drafts remains subject to the human-approval and rollback discipline owned there. |
| `context/bid-rules.md` | Owns **bid mechanics** and the bid-action **click sample sizes** (15 / 25 clicks). The "> 9 clicks" trigger used in Rules 2 and 3 here is a **different** value with a **different purpose** (a pause condition, not a bid-confidence sample size) and must not be conflated with the bid-rules click thresholds. |
| `context/amazon-vendor-bridge.md` | Intended owner of product master / vendor-bridge runtime data (currently `[VERIFY]` — not yet documented). Actual ASINs, SKUs and product prices needed to evaluate these rules at runtime belong there / in `evidence/`, not in this file. |

---

## Guiding Principles

- **Evidence First.** Every rule value here is taken only from the source PDF.
  Anything the PDF does not state is marked `[VERIFY]`, never estimated or filled
  from Amazon knowledge, PPC best practice, or another repository file.
- **Existing Asset First.** This is a new file created only because no existing
  document owns product-performance pause decision logic. No existing file was
  modified.
- **Single Source of Truth.** This document is the sole authoritative home for
  Product Pause decision logic. KPI definitions, standard budget rules, the stock
  gate and bid mechanics remain owned by their files and are referenced.
- **Queryability First.** Conditions, values and exclusions are stated plainly so
  another LLM can apply or validate a rule without verbal explanation (see the
  **Queryability Test**).
- **No Duplicate Truth.** ROAS/ACoS as KPIs are referenced from
  `context/target-metrics.md`; budget rules and the stock gate from
  `context/budget-rules.md`; bid mechanics from `context/bid-rules.md`. None is
  restated here. No runtime product data is stored here.
- **DRAFT recommendations only.** Every decision output below is a DRAFT
  recommendation.
- **Human approval and manual execution.** The AIOS never pauses a product;
  Jathukulan (or the authorised PPC Executive) reviews and applies every pause
  manually in Amazon Ads.

---

## Shared Logic — Date-Based Data Window

All three rules use the same **fixed** date-based logic to decide which data
window to evaluate. The source states this logic must **not** be changed per
marketplace; only the thresholds inside each condition are configurable.

| Day of month (evaluation date) | Data window used | Source example |
|-------------------------------|------------------|----------------|
| 1st – 20th | **Last 30 Days** | Today = 10 Apr → data from 11 Mar to 10 Apr |
| 21st – 31st | **This Month** | Today = 21 Apr → data from 1 Apr to 21 Apr |

Where a rule condition below refers to "Last 30D / This Month", the correct one of
the two is selected by this table according to the evaluation date. The **Last 7
Days** window is always the trailing 7 days regardless of the day of month.

---

# Rule Families

## Rule 1 — ROAS Based Pause

Source rule identity: **Rule 1 — ROAS Based Pause**. Applies to Amazon SP / SB /
SD. Base marketplace: Amazon UK (GBP £).

### Business Purpose

Per the source PDF, this rule evaluates products that **still have recent orders**
(orders in both the last 30 days and the last 7 days) but whose **ROAS is weak or
inconsistent** across the 30-day/monthly and 7-day windows. It recommends pausing
products whose return on ad spend is below the stated bands, unless a documented
"Improving" trajectory exempts them.

### Evaluation Window / Trigger

- **Trigger Scope:** Last 30 Days Orders **> 0** AND Last 7 Days Orders **> 0**.
- **Data window:** selected by the shared **Date-Based Data Window** table
  (Last 30D for the 1st–20th; This Month for the 21st–31st), with the Last 7 Days
  window used alongside it.
- **Evaluation cadence:** the source does not state how often the rule is run.
  `[VERIFY]` — evaluation cadence is not documented in the source.

### Conditions

Three independent conditions (Cond 1, Cond 2, Cond 3). A product matches Rule 1 if
**any one** condition's logic is fully satisfied (all clauses within that
condition must match) **and** the corresponding exception does not apply. Values
are UK base values from the PDF. ROAS is the KPI defined in
`context/target-metrics.md`; the numeric bands below are the rule-specific trigger
values from the PDF.

**Condition 1** — *(no exception)*

- 1st–20th: Last 30D `0 < ROAS < 3` AND Last 7D `0 < ROAS < 4` AND Last 30D
  Orders `≥ 1`.
- 21st–31st: This Month `0 < ROAS < 3` AND Last 7D `0 < ROAS < 4` AND This Month
  Orders `≥ 1`.

**Condition 2**

- 1st–20th: Last 30D `0 < ROAS < 2` AND Last 7D `ROAS ≥ 4` AND Last 30D Orders
  `≥ 1`.
- 21st–31st: This Month `0 < ROAS < 2` AND Last 7D `ROAS ≥ 4` AND This Month
  Orders `≥ 1`.

**Condition 3**

- 1st–20th: Last 30D `ROAS ≥ 3` AND Last 7D `0 < ROAS < 4` AND Last 30D Orders
  `≥ 1`.
- 21st–31st: This Month `ROAS ≥ 3` AND Last 7D `0 < ROAS < 4` AND This Month
  Orders `≥ 1`.

### Action

- **Source automation action:** Pause Product (ASIN).
- **AIOS decision output:** **DRAFT recommendation — Pause Product (ASIN).**
  Requires human approval; applied manually in Amazon Ads.

### Constraints

- Applies only within the trigger scope above (orders in both the last 30 days and
  the last 7 days). Products outside that order pattern are handled by Rule 2 or
  Rule 3, not Rule 1.
- Scope: SP / SB / SD campaigns, or specific Campaign IDs / ASINs. Which specific
  products are in scope for LEDSone is runtime data, not a rule value, and is not
  asserted here.

### Exceptions

The source defines an **Exception ("Do NOT Pause If")** representing an *Improving*
trajectory. Condition 1 has **no** exception. Conditions 2 and 3 each have one:

- **Condition 2 exception (Improving — do NOT pause):**
  - 1st–20th: Last 30D `0 < ROAS < 2` AND Last 7D `ROAS ≥ 5` AND Last 7D Orders
    `≥ 2`.
  - 21st–31st: This Month `0 < ROAS < 2` AND Last 7D `ROAS ≥ 5` AND Last 7D
    Orders `≥ 2`.
- **Condition 3 exception (Improving — do NOT pause):**
  - 1st–20th: Last 30D `ROAS ≥ 3` AND Last 7D `ROAS ≥ 3` AND Last 7D Orders
    `≥ 3`.
  - 21st–31st: This Month `ROAS ≥ 3` AND Last 7D `ROAS ≥ 3` AND Last 7D Orders
    `≥ 3`.

When a condition's pause logic matches **and** its exception also holds, the DRAFT
recommendation is **No Action** (do not pause).

### Product Price Logic

Not applicable. Rule 1 uses only ROAS bands and order counts; the source states no
product-price tier for Rule 1.

### Marketplace Variations

The source states the **logic is identical across marketplaces**; only configurable
thresholds change. For Rule 1 the source provides explicit numeric bands for the
**UK base** only (above). Per-marketplace overrides of these ROAS bands and order
counts for DE/FR/IT/NL/ES are not enumerated in the source. `[VERIFY]` — non-UK
Rule 1 threshold values are not documented in the source.

### Required Runtime Inputs

Input **types** needed (no runtime values included):

- Evaluation date (to select the data window: 1st–20th vs 21st–31st)
- Marketplace (to select the correct parameter set; to flag US/CA as `[VERIFY]`)
- Campaign Type — SP / SB / SD (scope)
- Product / ASIN identity (scope)
- Last 30 Days Orders; This Month Orders (per window); Last 7 Days Orders
- Last 30 Days ROAS; This Month ROAS (per window); Last 7 Days ROAS

### Decision Outputs

- **DRAFT recommendation — Pause Product (ASIN)** — a condition's pause logic is
  fully met and its exception (if any) does not apply.
- **No Action** — no condition is fully met, or a matched condition's Improving
  exception applies.

### Rule Notes

- No unpause / reinstatement output is stated in the source; none is documented
  here. `[VERIFY]`.
- The exception column is labelled "Improving" in the source; the interpretation
  above ("do NOT pause when the exception holds") follows the source column
  heading "Exception: Do NOT Pause If".

---

## Rule 2 — ROAS & Spend Based Pause

Source rule identity: **Rule 2 — ROAS & Spend Based Pause**. Applies to Amazon
SP / SB / SD. Base marketplace: Amazon UK (GBP £).

### Business Purpose

Per the source PDF, this rule evaluates products that **had orders in the last 30
days but have gone quiet in the last 7 days** (zero orders in the last 7 days). It
distinguishes weak-ROAS products with continued click activity from
efficient-ROAS products that are nonetheless spending a disproportionate share of
their price without converting.

### Evaluation Window / Trigger

- **Trigger Scope:** Last 30 Days Orders **> 0** AND Last 7 Days Orders **= 0**.
- **ROAS reference:** the source states Last 30D ROAS `≥ 3` for all conditions
  **except** Condition 1, which uses Last 30D ROAS `< 3`.
- **Evaluation cadence:** not stated in the source. `[VERIFY]`.

### Conditions

The source defines Condition 1 as price-independent and Conditions 2–16 as
price-tiered:

- **Condition 1 (price-independent):** Pause if Last 30D `ROAS < 3` AND Last 7D
  Orders `= 0` AND Last 7D Clicks `> 9`.
- **Conditions 2–16 (price-tiered):** Pause if Last 30D `ROAS ≥ 3` AND Last 7D
  Orders `= 0` AND Last 7D Spend `≥ X%` of Product Price, where `X%` is the
  spend-percentage threshold for the product's price tier (table below).

### Action

- **Source automation action:** Pause Product (ASIN).
- **AIOS decision output:** **DRAFT recommendation — Pause Product (ASIN).**
  Requires human approval; applied manually.

### Constraints

- Applies only within the trigger scope (orders in the last 30 days, zero orders
  in the last 7 days).
- Condition 1 requires Last 7 Days Clicks `> 9`; without that click volume,
  Condition 1 does not fire (the source lists Condition 1 as
  "ROAS < 3, 7D Clicks > 9").
- Scope: SP / SB / SD campaigns, or specific Campaign IDs / ASINs — runtime data,
  not asserted here.

### Exceptions

The source states **no** "Do NOT Pause" exception for Rule 2. `[VERIFY]` — no
exception is documented; do not import Rule 1's Improving exception into Rule 2.

### Product Price Logic

Conditions 2–16 compare **Last 7 Days Spend** against a percentage of **Product
Price**, where the percentage is set by the product's price tier. UK base values:

| Tier | Price range (UK £) | UK Spend % of Product Price |
|------|--------------------|-----------------------------|
| 1 | Any price — *Condition 1 path* (ROAS < 3, 7D Clicks > 9) | N/A — click-based, not a spend % |
| 2 | ≤ £15 | 22% |
| 3 | £15 < Price ≤ £25 | 20% |
| 4 | £25 < Price ≤ £35 | 18% |
| 5 | £35 < Price ≤ £50 | 16% |
| 6 | £50 < Price ≤ £60 | 15% |
| 7 | £60 < Price ≤ £65 | 13% |
| 8 | £65 < Price ≤ £80 | 11% |
| 9 | £80 < Price ≤ £90 | 10% |
| 10 | £90 < Price ≤ £100 | 9% |
| 11 | £100 < Price ≤ £115 | 8% |
| 12 | £115 < Price ≤ £135 | 7% |
| 13 | £135 < Price ≤ £160 | 6% |
| 14 | £160 < Price ≤ £200 | 5% |
| 15 | £200 < Price ≤ £270 | 4% |
| 16 | Price > £270 | 3% |

Higher-priced products carry a **lower** spend-% threshold (they are recommended
for pause after spending a smaller share of their price without a 7-day order).

### Marketplace Variations

The source's Rule 2 table provides explicit values for the **UK (£)** column only.
The DE / FR / IT / NL / ES columns are blank ("fill →") in the source, and the
source note states the currency symbol and price-range boundaries may also differ
per marketplace. `[VERIFY]` — non-UK spend-% thresholds and non-UK price-range
boundaries for Rule 2 are not documented in the source. This matches the open item
already recorded in `context/budget-rules.md` (non-UK values for Spend Pause Rules
2–3 blank in all source documents).

### Required Runtime Inputs

- Evaluation date (window selection)
- Marketplace
- Campaign Type — SP / SB / SD
- Product / ASIN identity
- Product Price (for price-tier selection; `[VERIFY]` — the exact price basis, e.g.
  list vs sale price, is not defined in the source)
- Last 30 Days Orders; Last 7 Days Orders
- Last 30 Days ROAS
- Last 7 Days Clicks (Condition 1)
- Last 7 Days Spend (Conditions 2–16)

### Decision Outputs

- **DRAFT recommendation — Pause Product (ASIN)** — Condition 1 met, or any of
  Conditions 2–16 met for the product's price tier.
- **No Action** — no condition met.

### Rule Notes

- Rule 2 measures **Last 7 Days Spend** against Product Price — this is stated
  explicitly in the source ("7D Spend ≥ X% of Product Price") and differs from
  Rule 3's spend window (see Rule 3). Do not substitute one for the other.
- No unpause / reinstatement logic is stated. `[VERIFY]`.

---

## Rule 3 — Spend Based Pause (Zero Orders)

Source rule identity: **Rule 3 — Spend Based Pause (Zero Orders)**. Applies to
Amazon SP / SB / SD. Base marketplace: Amazon UK (GBP £).

### Business Purpose

Per the source PDF, this rule evaluates products with **no orders at all** (zero
orders in both the last 30 days and the last 7 days) that are still **attracting
clicks and spending**. It recommends pausing products whose spend has exceeded a
price-tiered percentage of their price without producing any order.

### Evaluation Window / Trigger

- **Trigger Scope:** Last 30 Days Orders **= 0** AND Last 7 Days Orders **= 0**.
- **Required for all conditions:** Last 7 Days Clicks `> 9`.
- **Spend window:** the source states spend is measured "in the relevant window
  (Last 30D or This Month)" — i.e. selected by the shared **Date-Based Data
  Window** table, unlike Rule 2 which uses Last 7 Days Spend.
- **Evaluation cadence:** not stated in the source. `[VERIFY]`.

### Conditions

Pause if **all** of the following hold:

- Last 30 Days Orders `= 0` AND Last 7 Days Orders `= 0`, and
- Last 7 Days Clicks `> 9`, and
- Spend in the relevant window (Last 30D or This Month, per the date-window table)
  `≥ X%` of Product Price, where `X%` is the spend-percentage threshold for the
  product's price tier (table below).

### Action

- **Source automation action:** Pause Product (ASIN).
- **AIOS decision output:** **DRAFT recommendation — Pause Product (ASIN).**
  Requires human approval; applied manually.

### Constraints

- Applies only within the trigger scope (zero orders in both windows).
- The `> 9` clicks requirement applies to **all** conditions; without it, no Rule
  3 pause fires.
- Scope: SP / SB / SD campaigns, or specific Campaign IDs / ASINs — runtime data,
  not asserted here.

### Exceptions

The source states **no** "Do NOT Pause" exception for Rule 3. `[VERIFY]` — no
exception is documented.

### Product Price Logic

Spend in the relevant window is compared against a percentage of **Product Price**
set by the product's price tier. UK base values:

| Tier | Price range (UK £) | UK Spend % of Product Price |
|------|--------------------|-----------------------------|
| 1 | ≤ £15 | 20% |
| 2 | £15 < Price ≤ £25 | 19% |
| 3 | £25 < Price ≤ £35 | 17% |
| 4 | £35 < Price ≤ £50 | 15% |
| 5 | £50 < Price ≤ £60 | 14% |
| 6 | £60 < Price ≤ £65 | 12% |
| 7 | £65 < Price ≤ £80 | 10% |
| 8 | £80 < Price ≤ £90 | 9% |
| 9 | £90 < Price ≤ £100 | 8% |
| 10 | £100 < Price ≤ £115 | 7% |
| 11 | £115 < Price ≤ £135 | 6% |
| 12 | £135 < Price ≤ £160 | 5% |
| 13 | £160 < Price ≤ £200 | 4% |
| 14 | £200 < Price ≤ £270 | 3% |
| 15 | Price > £270 | 2% |

As with Rule 2, higher-priced products carry a **lower** spend-% threshold. The
Rule 3 percentages are stated separately from Rule 2's and are **not**
interchangeable with them.

### Marketplace Variations

The source's Rule 3 table provides explicit values for the **UK (£)** column only;
DE / FR / IT / NL / ES columns are blank ("fill →"), and the source note states
currency symbol and price-range boundaries may differ per marketplace. `[VERIFY]`
— non-UK spend-% thresholds and non-UK price-range boundaries for Rule 3 are not
documented in the source (matches the open item in `context/budget-rules.md`).

### Required Runtime Inputs

- Evaluation date (window selection)
- Marketplace
- Campaign Type — SP / SB / SD
- Product / ASIN identity
- Product Price (for price-tier selection; price basis `[VERIFY]` as in Rule 2)
- Last 30 Days Orders; Last 7 Days Orders
- Last 7 Days Clicks
- Spend in the relevant window — Last 30 Days or This Month

### Decision Outputs

- **DRAFT recommendation — Pause Product (ASIN)** — zero orders in both windows,
  `> 9` clicks in the last 7 days, and window spend `≥` the price-tier threshold.
- **No Action** — any of those is not met.

### Rule Notes

- Rule 3's spend window is the **date-selected** window (Last 30D or This Month),
  which differs from Rule 2's **Last 7 Days** spend window. This distinction is
  explicit in the source.
- No unpause / reinstatement logic is stated. `[VERIFY]`.

---

## Rule Interaction

- **Selection between the three rules is mutually exclusive by order pattern.** The
  three trigger scopes partition products by (Last 30D Orders, Last 7D Orders):
  both > 0 → Rule 1; 30D > 0 and 7D = 0 → Rule 2; both = 0 → Rule 3. The source
  presents them as three separate rules keyed to these patterns.
- **Precedence / sequencing beyond that selection is not stated.** `[VERIFY]` —
  the source does not establish an explicit precedence, sequencing or
  conflict-resolution order between these pause rules, nor between them and any
  other repository rule (budget rules, the stock gate in
  `context/budget-rules.md`, or bid rules). Do not invent precedence.
- **Interaction with the stock gate and product re-activation** (owned by
  `context/budget-rules.md`) is not addressed by this source. `[VERIFY]` — whether
  a pause recommendation should be suppressed or overridden by stock-driven rules
  is undocumented.

---

## Source Evidence

**Primary Source:** `AMZ_Spend Basic_Product Pause_Rule_Configurator.pdf`
(developer specification, "SPEND BASIC PRODUCT PAUSE — Rule Configurator
Dashboard", Amazon SP · SB · SD, v1.0). All rule values in this document are
extracted from that PDF — specifically its "Rule 1 — ROAS Based Pause", "Rule 2 —
ROAS & Spend Based Pause" (and Rule 2 Spend % Thresholds table), "Rule 3 — Spend
Based Pause (Zero Orders)" (and Rule 3 Spend % Thresholds table), and the
"Date-Based Data Window Logic" section.

**Evidence-filing status: [VERIFY].** At the time of writing, this source PDF is
**not** confirmed as filed in `evidence/` with its source, date and date range per
`evidence/README.md`. Repository inspection on creation found no PDF in `evidence/`
(only `README.md` and `TEMPLATE_EVIDENCE_RECORD.md`). It must be filed there (with
a metadata record) before these rules are relied upon operationally.

**Repository references (context only, values not copied):**
`context/target-metrics.md` (ROAS / ACoS KPI definitions),
`context/budget-rules.md` (Standard Budget Rules, stock gate, and its existing
"Spend Pause Rules 2–3" non-UK note), `context/bid-rules.md` (bid mechanics and
click sample sizes), `context/amazon-vendor-bridge.md` (intended product-master
owner, currently `[VERIFY]`), `CLAUDE.md` (governance — DRAFT only, never modify
Amazon Ads, evidence-first, no duplicate truth).

---

## Known Limitations

Unresolved items. None is worked around by inventing data.

1. **Non-UK spend-% thresholds undocumented (Rules 2 & 3).** The DE/FR/IT/NL/ES
   columns are blank ("fill →") in both spend-% tables. Values `[VERIFY]` — do not
   infer from UK. This matches the existing open item in
   `context/budget-rules.md`. [VERIFY]
2. **Non-UK price-range boundaries undocumented.** The source note states price
   ranges "may also differ" per marketplace but gives no non-UK boundaries.
   [VERIFY]
3. **US and CA marketplace values undocumented.** The Core Entities list names
   "UK, US, DE, FR, IT, NL, ES…" but no table provides US values, and CA appears
   nowhere. Do not infer US/CA values from UK/EU. [VERIFY]
4. **Non-UK Rule 1 ROAS bands / order counts undocumented.** The source gives Rule
   1's numeric bands for the UK base only; per-marketplace overrides are not
   enumerated. [VERIFY]
5. **Evaluation cadence undocumented.** The source does not state how frequently
   any of the three rules is evaluated (only the date-based window selection).
   [VERIFY]
6. **Product Price basis undefined.** "Product Price" is used in Rules 2 and 3 but
   the source does not define which price (e.g. list price vs current sale price).
   [VERIFY]
7. **No reinstatement / unpause logic.** The source states only a Pause action; no
   condition, window or trigger for un-pausing a product is documented. [VERIFY]
8. **Rule precedence / interaction not established.** Beyond the mutually-exclusive
   order-pattern selection, no precedence or conflict-resolution order is stated
   between these rules or against budget/stock/bid rules. [VERIFY]
9. **Interaction with the stock gate / re-activation.** Whether a pause should be
   suppressed for stock-constrained or re-activating products (owned by
   `context/budget-rules.md`) is not addressed by the source. [VERIFY]
10. **Approval workflow for a pause.** The source states no approval path (it is an
    automation spec); the repository's own approval bands are themselves `[VERIFY]`
    in `context/budget-rules.md`. Any pause remains DRAFT pending human approval.
    [VERIFY]
11. **"Paused Day / Week Days" entity undefined.** The Core Entities table lists a
    "Paused Day" entity with value "Week Days"; the source does not define its
    business meaning (e.g. whether pauses are restricted to weekdays). [VERIFY]
12. **Evidence not confirmed filed.** The primary PDF is not confirmed filed in
    `evidence/`; required before operational use. [VERIFY]

---

## Ownership

- **Owner:** Amazon PPC AIOS
- **Reviewer:** Jathukulan
- **Business Owner / Technical Reviewer / Approver:** `[VERIFY]` — no governance
  role for approving pause decisions is defined anywhere in this repository (see
  the same gap recorded in `context/target-metrics.md`).
- **Status:** Draft

---

## Queryability Test

Using only this document and its explicit references, can another LLM answer:

| Question | Answerable? | Where |
|----------|-------------|-------|
| What Product Pause rules exist? | Yes | Rule Families (Rules 1, 2, 3) |
| Why does each rule exist? | Yes | Business Purpose per rule |
| When is each rule evaluated? | Yes | Evaluation Window / Trigger; Shared Date-Based Data Window |
| What conditions apply? | Yes | Conditions + Constraints + Exceptions per rule |
| What DRAFT action is recommended? | Yes | Action; Decision Outputs per rule |
| What runtime inputs are required? | Yes | Required Runtime Inputs per rule |
| What exceptions exist? | Yes | Exceptions per rule (Rule 1 Improving; Rules 2/3 none stated) |
| Which values are unresolved? | Yes | `[VERIFY]` markers; Known Limitations |
| Which source supports the rules? | Yes | Source Evidence |
| Which other Context documents own related truth? | Yes | Dependencies |
| Is the AIOS permitted to pause a product? | Yes | Purpose / Guiding Principles — **No; DRAFT only, human applies manually** |

**Result: PASS**
