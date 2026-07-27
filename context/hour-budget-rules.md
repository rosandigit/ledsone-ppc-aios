# Hour Budget Rules

Canonical **business-rule** document for **Hour Budget Optimisation** in the
LEDSone Amazon PPC AIOS. It is the single authoritative source for the hourly
(intraday) budget-increase rule. It documents **business decision logic only** —
not software, dashboards, schedulers, or automation.

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

> The primary evidence for this rule is a developer specification for an
> automated rule-configurator dashboard. This document deliberately extracts the
> **business rule** from that source and discards the automation/execution
> framing. Within the AIOS, this rule can only ever produce a DRAFT
> recommendation that Jathukulan (or the authorised PPC Executive) reviews and
> applies manually in Amazon Ads.

---

## Purpose

This document exists so that any person or AI skill in the repository evaluates
**intraday (hourly) budget-increase** decisions the same way, from one canonical
definition. Standard budget governance in `context/budget-rules.md` covers
daily-level budget minimums and order-volume-based overrides; it does **not**
cover the specific intraday rule that boosts a small, efficient campaign that is
about to exhaust its daily budget mid-day. This file documents that rule, and
only that rule, from its source evidence.

---

## Scope

**This document covers:**

- The single Hour Budget Optimisation rule ("Hourly Budget Boost — Low Budget
  Campaigns") as stated in the source PDF: its trigger, conditions, action,
  constraint, and the marketplace parameter values the PDF explicitly documents.
- The business inputs and decision outcomes another LLM or PPC Executive needs to
  make or validate that budget decision as a DRAFT recommendation.

**This document deliberately does NOT cover:**

- Any software implementation — dashboard layout, configurator screens,
  Create/Edit/Delete/Clone/Apply operations, the automation engine, the
  scheduling engine, audit logging, or UI behaviour (all present in the source
  PDF and intentionally excluded).
- KPI **definitions** (ACoS etc.) — owned by `context/target-metrics.md` and
  referenced, never redefined here.
- Standard daily budget rules (minimums, Special Rules SR-1…SR-4, stock gate,
  approval thresholds, rollback) — owned by `context/budget-rules.md` and
  referenced, never restated here.
- Any bid, keyword, targeting or product-pause logic.

---

## Business Question

**"When should campaign budgets be increased during the day?"**

Per the source PDF, a campaign's daily budget should be **increased (as a DRAFT
recommendation)** during the day when **all** of the following hold at the time
of evaluation:

1. the campaign has spend data for the current day (current-day ACoS > 0%),
2. the campaign is efficient (current-day ACoS ≤ 20% — UK value),
3. the campaign is close to exhausting its budget (today's spend ≥ 80% of its
   current daily budget), and
4. the campaign currently has a **small** daily budget (current daily budget
   < £10 — UK value).

If all conditions are met, the DRAFT recommendation is to increase the daily
budget by the documented amount (£3, UK). If any condition is not met, no
increase is recommended. The PDF states the rule is evaluated **hourly**. All
threshold values above are taken from the source PDF (see **Source Evidence**);
marketplace-specific values are in **Marketplace Variations**.

---

## Dependencies

| Dependency | Why it exists |
|------------|---------------|
| `context/target-metrics.md` | Owns the **definition** of ACoS as a KPI. This rule uses an ACoS threshold as a *trigger value* taken from the source PDF; the metric it refers to is defined there. This document references that definition and does not redefine ACoS. |
| `context/budget-rules.md` | Owns **Standard Budget Rules** (daily minimums, order-volume-based Special Rules SR-1…SR-4, stock gate, approval thresholds, rollback discipline). Hour Budget Rules are a **different mechanism** (see below); any budget change this rule drafts is still subject to the human-approval and rollback discipline owned there. |

**How Hour Budget Rules differ from Standard Budget Rules** (no values restated):
Standard Budget Rules in `context/budget-rules.md` set or override budgets at the
**daily** level, driven mainly by **order volume** and multi-day ACoS windows
(L30D/L7D). The Hour Budget rule instead operates **intraday**, evaluated
hourly, and is driven by **within-day budget pacing** (today's spend vs today's
budget) for **small-budget** campaigns only. It is an intraday top-up rule, not a
daily budget-setting rule. This document does not state how the two regimes rank
against each other — that precedence is not in the source evidence and is marked
`[VERIFY]` in **Known Limitations**.

---

## Guiding Principles

- **Evidence First.** Every rule value here is taken only from the source PDF.
  Anything the PDF does not state is marked `[VERIFY]`, never estimated or filled
  from Amazon knowledge, PPC best practice, or another repository file.
- **Existing Asset First.** This is a new file created only because no existing
  document owns the intraday hourly budget rule. No existing file was modified.
- **Single Source of Truth.** This document is the sole authoritative home for the
  Hour Budget Optimisation rule. KPI definitions and standard budget rules remain
  owned by their files and are referenced.
- **Queryability First.** Values, conditions and exclusions are stated plainly so
  another LLM can apply or validate the rule without verbal explanation (see the
  **Queryability Test**).
- **No Duplicate Truth.** ACoS as a KPI is referenced from
  `context/target-metrics.md`; standard budget rules are referenced from
  `context/budget-rules.md`. Neither is restated here.

---

# Rule Family

## Hour Budget Optimisation

Source rule identity (from the PDF): **Rule 001 — Hourly Budget Boost (Low Budget
Campaigns)**, Rule ID `UK-SP,SB,SD-BUDGET-001`, Rule Type "Budget Optimization —
Sponsored Product, Sponsored Brand, Sponsored Display". Base marketplace: Amazon
UK (Currency GBP £). Status in source: Active.

---

### Business Purpose

Per the source PDF: the rule targets **small campaigns that are performing well
(low ACoS) but risk running out of budget mid-day**. The daily-budget-cap
constraint (< £10, UK) exists so that **already well-funded campaigns are not
repeatedly boosted**. In business terms, it protects efficient, budget-limited
small campaigns from losing intraday sales to premature budget exhaustion.

---

### Business Scenario

The rule is intended to apply during the trading day to a Sponsored Products,
Sponsored Brands or Sponsored Display campaign that: has current-day spend data,
is running efficiently against the ACoS trigger, has already spent most of its
current daily budget, and still has only a small daily budget allocated. In that
situation the rule proposes a small intraday budget increase (DRAFT).

---

### Trigger

Taken only from the PDF:

- **Trigger / Schedule:** **Hourly** — the rule is evaluated every hour
  throughout the day.

> AIOS boundary: within this repository the hourly trigger describes the
> **cadence at which the DRAFT recommendation would be re-evaluated**, not an
> automatic action. The AIOS never executes the increase; a human applies any
> approved change manually. The scheduling/automation engine in the source PDF is
> out of scope for this document.

---

### Conditions

All conditions must be true before the action is proposed (the source states
conditions are logical checks that must **ALL** be true before the action fires).
Values below are the UK base values from the PDF; marketplace variants are in
**Marketplace Variations**.

- **Condition A:** ACoS for the current day **> 0%** (i.e. the campaign has spend
  data for the current day). Source parameter: "ACOS Lower Limit: > 0%".
- **Condition B:** ACoS for the current day **≤ 20%** (UK). Source parameter:
  "ACOS Upper Limit: 20%".
- **Condition C:** Today's Spend **≥ 80%** of the current Daily Budget. Source
  parameter: "Spend Trigger %: 80%".

(ACoS is the KPI defined in `context/target-metrics.md`; the numeric thresholds
above are the rule-specific trigger values from the PDF.)

---

### Action

Taken only from the PDF:

- **Action:** Increase the campaign's **Daily Budget by £3** (UK base value).

Within the AIOS this is issued as a **DRAFT recommendation** to increase the daily
budget by the documented amount; it is never applied automatically.

---

### Constraints

Taken only from the PDF:

- **Constraint:** the rule **only applies to campaigns where the current Daily
  Budget < £10** (UK) — i.e. campaigns with a very small daily budget allocation.
  Source parameter: "Daily Budget Cap (Constraint): £10". Per the PDF note, this
  cap ensures already well-funded campaigns are not repeatedly boosted (a campaign
  whose current daily budget is £10 or more does not qualify).
- **Scope (from the PDF):** applies to all SP / SB / SD campaigns, or to specific
  Campaign IDs. Which specific campaigns are in scope for LEDSone is not a rule
  value and is not asserted here.

---

### Marketplace Variations

The source PDF documents the following per-marketplace parameter values for this
rule. The **rule logic (conditions, action type, constraint logic) is identical
across marketplaces**; only the values below differ. Currency: UK = GBP £; DE /
FR / IT / NL / ES = EUR €.

| Parameter | UK (£) | DE (€) | FR (€) | IT (€) | NL (€) | ES (€) |
|-----------|--------|--------|--------|--------|--------|--------|
| Daily Budget Threshold (constraint) | £10 | €10 | €10 | €10 | €10 | €10 |
| Spend % Trigger | 80% | 80% | 80% | 80% | 80% | 80% |
| Budget Increase Amount | £3 | €2 | €2 | €2 | €2 | €2 |
| ACoS Upper Limit | 20% | 16% | 16% | 16% | 16% | 16% |
| ACoS Lower Limit | > 0% | > 0% | > 0% | > 0% | > 0% | > 0% |

- **US and CA values: [VERIFY].** The source PDF's marketplace adaptation table
  covers only UK, DE, FR, IT, NL and ES. It documents **no** values for US or CA.
  These must be verified from an approved source before the rule is applied to US
  or CA campaigns; they must not be inferred from the UK or EU values.

---

### Required Runtime Inputs

Input **types** an AIOS skill would need to evaluate this rule (no runtime values
included):

- Current Daily Budget (for the < £10 constraint and the 80%-of-budget comparison)
- Today's Spend (current-day spend, for the ≥ 80% comparison)
- Current-day ACoS (for the > 0% and ≤ 20% conditions)
- Marketplace (to select the correct parameter set, and to flag US/CA as `[VERIFY]`)
- Campaign Type — SP / SB / SD (scope)
- Campaign identity / scope — all campaigns or specific Campaign IDs (scope)

---

### Decision Outputs

Outcomes supported by the source PDF:

- **Increase Budget (DRAFT)** — when Conditions A, B and C are all met **and** the
  daily-budget constraint is satisfied (current daily budget below the threshold):
  recommend increasing the daily budget by the documented Budget Increase Amount
  for the marketplace. Requires human approval before it is applied.
- **No Action** — when any condition is not met, or the daily budget is at/above
  the threshold: no increase is recommended.

No other outcome (e.g. a budget decrease) is stated in the source PDF, so none is
documented here.

---

### Rule Notes

- The PDF states the rule is designed for **small, well-performing campaigns**
  (low ACoS) at risk of exhausting budget mid-day; the < £10 constraint prevents
  repeatedly boosting already well-funded campaigns.
- The constraint itself acts as the effective ceiling: once a campaign's current
  daily budget reaches the threshold, it no longer qualifies for a further boost.
  Any additional cumulative-boost cap beyond this is not stated in the source and
  is `[VERIFY]`.
- ACoS is the only efficiency metric this rule uses; the source rule does **not**
  reference ROAS, so no ROAS value appears in this document.

---

## Source Evidence

**Primary Source:** `AMZ_Hour Basic_Budget_Optimization_Rule_Configurator.pdf`
(developer specification, "HOUR BASIC BUDGET OPTIMIZATION — Rule Configurator
Dashboard", Amazon SP · SB · SD). All rule values in this document are extracted
from that PDF — specifically its "Rule 001 — Hourly Budget Boost (Low Budget
Campaigns)" definition and its "Marketplace Adaptation Table".

**Evidence-filing status: [VERIFY].** At the time of writing, this source PDF is
not confirmed as filed in `evidence/` with its source, date and date range per
`README.md`. It must be filed there (with a metadata record) before this rule is
relied upon operationally.

**Repository references (context only, values not copied):**
`context/target-metrics.md` (ACoS KPI definition), `context/budget-rules.md`
(Standard Budget Rules), `CLAUDE.md` (governance — DRAFT only, never modify Amazon
Ads, evidence-first, no duplicate truth).

---

## Known Limitations

Unresolved items. None is worked around by inventing data.

1. **US and CA marketplace values undocumented.** The source PDF's adaptation
   table omits US and CA; LEDSone operates in both per the PDF's own Seller
   Accounts Reference. Values `[VERIFY]` — do not infer from UK/EU. [VERIFY]
2. **Rule precedence vs Standard Budget Rules.** How this intraday rule interacts
   with or ranks against the daily minimums and Special Rules SR-1…SR-4 in
   `context/budget-rules.md` is not stated in the source. [VERIFY]
3. **Approval workflow for the intraday increase.** The source states no
   approval path; the repository's own budget-approval bands are themselves
   `[VERIFY]` in `context/budget-rules.md`. Any increase remains DRAFT pending
   human approval. [VERIFY]
4. **Cumulative boost cap.** Beyond the < £10 daily-budget constraint acting as a
   ceiling, no explicit limit on how many times per day the increase may be
   proposed is stated. [VERIFY]
5. **Evidence not confirmed filed.** The primary PDF is not confirmed filed in
   `evidence/`; required before operational use. [VERIFY]
6. **Interaction with product-pause and stock gate.** Whether an increase should
   be suppressed for stock-constrained products (stock gate owned by
   `context/budget-rules.md`) is not addressed by the source. [VERIFY]

---

## Ownership

- **Owner:** Amazon PPC AIOS
- **Reviewer:** Jathukulan
- **Status:** Draft

---

## Queryability Test

Using only this document, can another LLM answer:

| Question | Answerable? | Where |
|----------|-------------|-------|
| Why does this rule exist? | Yes | Business Purpose; Purpose |
| When should it be used? | Yes | Business Scenario; Business Question; Trigger |
| What conditions must be satisfied? | Yes | Conditions (A, B, C) + Constraints |
| What business action does it recommend? | Yes | Action; Decision Outputs |
| Which runtime inputs are required? | Yes | Required Runtime Inputs |
| What information is intentionally excluded? | Yes | Scope (software/UI/automation excluded) |
| Which document owns KPI definitions? | Yes | Dependencies — `context/target-metrics.md` |
| Which evidence supports this rule? | Yes | Source Evidence |

**Result: PASS**
