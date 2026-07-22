# Target Metrics

Canonical operational reference for Amazon PPC target metrics used by LEDSone.

This document defines metrics. It does not define rules. Bid and budget rule
logic lives in `context/bid-rules.md` and `context/budget-rules.md` and is
referenced here, never restated.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — recorded as `Owner` in `README.md`, `CLAUDE.md`, `context/bid-rules.md` and `context/budget-rules.md` |
| Business Owner | [VERIFY] — no governance section exists in `README.md` or `CLAUDE.md`. "MD" appears in `context/budget-rules.md` as a budget **approver**, but is nowhere defined as Business Owner. Do not assume the two are the same role. |
| Technical Reviewer | [VERIFY] — no technical reviewer role is defined anywhere in this repository |
| Queryability Reviewer | [VERIFY] — no queryability reviewer role is defined anywhere in this repository |
| Status | Active — approved values documented; outstanding items marked `[VERIFY]` |
| Version | 1.0 |
| Last Updated | 2026-07-22 |
| Source Documents | See the **Evidence** section below |

---

## Purpose

This document exists so that every person and every AI skill working in this
repository uses the **same** definition of "good performance", drawn from one
place.

It answers four questions that were previously unanswerable from this
repository:

1. What does LEDSone consider a successful PPC outcome? (Business KPI Targets)
2. At what point does a metric warrant investigation or pausing?
   (Operational Alert Thresholds)
3. How much data is required before a bid change may be recommended?
   (Decision Triggers)
4. What is the minimum operating budget for a campaign? (Budget Minimums)

Keeping these in one document prevents the four categories from being confused
with one another — which is the single most common failure mode when reading
PPC numbers.

### Critical distinction — KPI Targets vs Operational Rule Triggers

These are **different kinds of number** and must never be substituted for one
another:

| | Business KPI Target | Operational Rule Trigger |
|---|---|---|
| **What it is** | A performance goal the business wants to achieve | A condition that fires a specific mechanical action |
| **Answers** | "Are we succeeding?" | "Should I act right now, and how?" |
| **Owned by** | This document | `context/bid-rules.md` / `context/budget-rules.md` |
| **Example** | Target ACoS **<25%** | Bid-raise consideration at **20% ACoS** (`bid-rules.md`) |
| **If breached** | Business performance is off-target; review strategy | A rule condition is met; a DRAFT recommendation may be produced |

**Worked example of the distinction.**
`context/bid-rules.md` states a standard ACoS raise trigger of **20%** and an
early scaling signal of **15%**. Those are the points at which a campaign is
efficient enough to *consider a bid or budget increase*. They are deliberately
**stricter** than the business KPI target of **<25%**, because the business
requires headroom before it spends more. A campaign running at 23% ACoS is
therefore **on-target as a KPI** but **does not meet the bid-raise trigger**.
Both statements are true simultaneously. Reporting must not describe such a
campaign as "failing", and optimisation must not treat it as "clear to scale".

The same applies to `context/budget-rules.md`, whose Special Rules SR-1 to SR-4
use ACoS conditions of 20% and 25% as **entry conditions for a budget
override**. The appearance of the numeral 25 there is a rule boundary, not a
restatement of the KPI target. Do not merge them.

---

## Evidence

Every value in this document originates from one of the sources below.
Existence inside this repository was checked on 2026-07-22 by listing the
repository contents.

| Source | Location | Exists in this repository? | Used for |
|--------|----------|---------------------------|----------|
| `context/bid-rules.md` | `context/bid-rules.md` | **Yes — verified in-repo document** | Decision Triggers (15 / 25 clicks); the 20% / 15% ACoS raise triggers cited for contrast |
| `context/budget-rules.md` | `context/budget-rules.md` | **Yes — verified in-repo document** | Budget Minimums (£2/day SP, £2/day SB) |
| `Amazon_BGCT_PayPerClick.pdf` | Not in this repository | **No — referenced external source, not present in this repository.** The repository currently contains only `.md` files and `.gitattributes`; no PDF exists in `evidence/` or anywhere else. | Background source for the approved KPI set |
| Approved PPC Metrics (2026-07-22) | Not in this repository | **No — referenced external source, not present in this repository.** Supplied as an approved value set at authoring time; no corresponding file has been filed in `evidence/`. | All Business KPI Targets and all Operational Alert Thresholds |

**Evidence gap (open action).** Two of the four sources above are external and
not filed in this repository. Under the evidence-first policy in `README.md`,
any recommendation citing a KPI target or alert threshold from this document is
currently resting on evidence that a future reader **cannot open**. Filing
`Amazon_BGCT_PayPerClick.pdf` and the approved metrics record into `evidence/`
would close this gap. This is recorded again in **Known Limitations**.

---

## Scope

These metrics are the shared reference for the following processes.

| Process | How these metrics are used |
|---------|---------------------------|
| Campaign optimisation | Judging whether a campaign is on-target before deciding what to change |
| Bid decisions | Supplying the KPI context around the bid mechanics in `context/bid-rules.md`; the click thresholds in section 3 gate whether a bid change may be drafted at all |
| Budget decisions | Supplying the KPI context around the budget mechanics in `context/budget-rules.md`; the minimums in section 4 define the operating floor |
| Reporting | Defining what is reported as on-target versus off-target, so weekly and monthly reports in `reports/` stay consistent month to month |
| Scaling | Establishing whether performance is strong enough to justify increased spend, in combination with the stock gate in `context/budget-rules.md` |
| AI Skills | Every skill in `skills/` reads this document for target values instead of holding its own copy — see the **Dependency Matrix** |

**Out of scope.** This document does not decide anything. It does not contain
bid mechanics, budget override tables, stock gates, approval thresholds or
rollback procedure. Those live in the two authoritative rule files.

**Safety.** Any output derived from this document that touches bids, budgets,
keywords, campaigns or targeting: outputs DRAFT recommendations only, never
applies Amazon Ads changes, human approval required before implementation. If
automation is implied, STOP and flag it.

---

## 1. Business KPI Targets

These are business performance goals. They describe success. They do **not**
fire any action on their own.

### The ACoS / ROAS relationship

ACoS and ROAS are two views of the same number, not two independent targets.

```
ACoS  = (Ad Spend ÷ Ad Sales) × 100
ROAS  =  Ad Sales ÷ Ad Spend
```

Because ROAS is the reciprocal of the spend-to-sales ratio:

```
ACoS ≈ (1 ÷ ROAS) × 100
```

Substituting the approved targets:

```
ROAS > 4×   →   ACoS < (1 ÷ 4) × 100   =   ACoS < 25%
```

So **ACoS <25%** and **ROAS >4×** are the *same target expressed two ways* and
are mathematically consistent. Hitting one means hitting the other. They are
both recorded because different reports and different stakeholders use
different conventions. Never treat them as two separate hurdles that must both
be cleared, and never report a campaign as passing one and failing the other —
if that ever occurs, the underlying data is wrong.

---

### Overall Target ACoS

- **Definition:** Advertising Cost of Sales across all Amazon PPC advertising
  types combined — the percentage of advertising-attributed revenue consumed by
  advertising spend.
- **Business Purpose:** The headline efficiency measure for the whole PPC
  account. Answers "is our advertising, as a whole, profitable enough?"
- **Calculation:** `(Ad Spend ÷ Ad Sales) × 100`
- **Target Value:** **<25%**
- **Warning Threshold:** [VERIFY] — no approved ACoS warning threshold exists.
  Do not reuse the 20% / 15% figures from `context/bid-rules.md`; those are
  bid-raise triggers, not warnings.
- **Critical Threshold:** [VERIFY] — no approved ACoS critical threshold exists
- **Primary Data Source:** Amazon Ads reporting, filed in `evidence/`.
  [VERIFY] — the exact report name and export cadence are not yet documented
- **Used By:** `acos-check`; wider usage [VERIFY] — see Dependency Matrix
- **Review Frequency:** [VERIFY] — `context/reporting-schedule.md` is still an
  undocumented placeholder
- **Status:** Approved value

### Overall Target ROAS

- **Definition:** Return on Ad Spend across all Amazon PPC advertising types
  combined — revenue returned per £1 of advertising spend.
- **Business Purpose:** The same efficiency measure as Overall ACoS, expressed
  as a multiple rather than a percentage.
- **Calculation:** `Ad Sales ÷ Ad Spend`
- **Target Value:** **>4×**
- **Warning Threshold:** [VERIFY] — no approved ROAS warning threshold exists
- **Critical Threshold:** [VERIFY] — no approved ROAS critical threshold exists
- **Primary Data Source:** Amazon Ads reporting, filed in `evidence/`.
  [VERIFY] — exact report name and export cadence not yet documented
- **Used By:** [VERIFY] — no skill in `skills/` is named for ROAS; see
  Dependency Matrix
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value. Mathematically equivalent to Overall Target ACoS

### Sponsored Products Target ACoS

- **Definition:** ACoS for Sponsored Products campaigns only.
- **Business Purpose:** Sponsored Products is the primary conversion-driving ad
  type; this isolates its efficiency from brand and display activity.
- **Calculation:** `(SP Ad Spend ÷ SP Ad Sales) × 100`
- **Target Value:** **<25%**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Products reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** `acos-check`; wider usage [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value

### Sponsored Products Target ROAS

- **Definition:** ROAS for Sponsored Products campaigns only.
- **Business Purpose:** Sponsored Products efficiency expressed as a return
  multiple.
- **Calculation:** `SP Ad Sales ÷ SP Ad Spend`
- **Target Value:** **>4×**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Products reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value. Equivalent to Sponsored Products Target ACoS

### Sponsored Brands Target ACoS

- **Definition:** ACoS for Sponsored Brands campaigns only.
- **Business Purpose:** Measures efficiency of brand-level advertising against
  the same standard applied to the rest of the account.
- **Calculation:** `(SB Ad Spend ÷ SB Ad Sales) × 100`
- **Target Value:** **<25%**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Brands reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** `acos-check`; wider usage [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value

### Sponsored Brands Target ROAS

- **Definition:** ROAS for Sponsored Brands campaigns only.
- **Business Purpose:** Sponsored Brands efficiency expressed as a return
  multiple.
- **Calculation:** `SB Ad Sales ÷ SB Ad Spend`
- **Target Value:** **>4×**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Brands reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value. Equivalent to Sponsored Brands Target ACoS

### Sponsored Display Target ACoS

- **Definition:** ACoS for Sponsored Display campaigns only.
- **Business Purpose:** Holds display advertising to the same efficiency
  standard as the rest of the account.
- **Calculation:** `(SD Ad Spend ÷ SD Ad Sales) × 100`
- **Target Value:** **<25%**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Display reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** `acos-check`; wider usage [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value

### Sponsored Display Target ROAS

- **Definition:** ROAS for Sponsored Display campaigns only.
- **Business Purpose:** Sponsored Display efficiency expressed as a return
  multiple.
- **Calculation:** `SD Ad Sales ÷ SD Ad Spend`
- **Target Value:** **>4×**
- **Warning Threshold:** [VERIFY]
- **Critical Threshold:** [VERIFY]
- **Primary Data Source:** Amazon Ads Sponsored Display reporting, filed in
  `evidence/`. [VERIFY] — exact report name not yet documented
- **Used By:** [VERIFY]
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value. Equivalent to Sponsored Display Target ACoS

### CTR — Click-Through Rate (Healthy Target)

- **Definition:** The percentage of ad impressions that result in a click.
- **Business Purpose:** Measures whether the ad is relevant and appealing to the
  shoppers it is being shown to. Low CTR indicates a targeting or creative
  problem — the ad is reaching the wrong audience or failing to attract it.
- **Calculation:** `(Clicks ÷ Impressions) × 100`
- **Target Value:** **>0.5%** (healthy)
- **Warning Threshold:** **0.3%** — CTR Review (see section 2)
- **Critical Threshold:** **0.2%** — CTR Pause (see section 2)
- **Primary Data Source:** Amazon Ads reporting, filed in `evidence/`.
  [VERIFY] — exact report name not yet documented
- **Used By:** [VERIFY] — see Dependency Matrix
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value

### CVR — Conversion Rate (Healthy Target)

- **Definition:** The percentage of ad clicks that result in an order.
- **Business Purpose:** Measures whether traffic converts once it arrives. Low
  CVR indicates a listing, price, stock or search-intent problem rather than an
  advertising-reach problem.
- **Calculation:** `(Orders ÷ Clicks) × 100`
- **Target Value:** **>10%** (healthy)
- **Warning Threshold:** **7%** — CVR Review (see section 2)
- **Critical Threshold:** **5%** — CVR Critical (see section 2)
- **Primary Data Source:** Amazon Ads reporting, filed in `evidence/`.
  [VERIFY] — exact report name not yet documented
- **Used By:** [VERIFY] — see Dependency Matrix
- **Review Frequency:** [VERIFY] — pending `context/reporting-schedule.md`
- **Status:** Approved value

---

## 2. Operational Alert Thresholds

These are **not** targets. They are the points at which a metric stops being
acceptable and requires attention. They describe escalation, moving from
healthy performance downward through review to a critical state.

Reaching a threshold produces a DRAFT recommendation for human review. Nothing
is paused automatically — this repository never changes anything in Amazon Ads.

### CTR escalation ladder

```
Healthy      >0.5%      Performing normally — no action
   ↓
Review        0.3%      Investigate targeting and creative; draft a recommendation
   ↓
Pause         0.2%      Draft a pause recommendation for human approval
```

- **CTR Review — 0.3%:** CTR has fallen materially below healthy. The ad is
  being shown but not attracting clicks. Investigate relevance of targeting and
  the listing's main image, title and price.
- **CTR Pause — 0.2%:** CTR is low enough that continued spend is unlikely to be
  productive. Draft a pause recommendation. **The pause is applied manually in
  Amazon Ads by Jathukulan after approval — never automatically.**

The band between 0.5% and 0.3% is a monitoring zone: below target, above the
review threshold. [VERIFY] — no approved action is defined for this band.

### CVR escalation ladder

```
Healthy      >10%       Performing normally — no action
   ↓
Review         7%       Investigate listing, price, stock and search intent
   ↓
Critical       5%       Escalate; draft corrective recommendation for approval
```

- **CVR Review — 7%:** Conversion has fallen materially below healthy. Traffic
  is arriving but not converting. Investigate the listing, price, stock
  availability and whether the matched search terms reflect real purchase
  intent.
- **CVR Critical — 5%:** Conversion is failing. Escalate and draft a corrective
  recommendation for human approval.

The band between 10% and 7% is a monitoring zone. [VERIFY] — no approved action
is defined for this band.

**Note on the CVR ladder.** The CVR critical threshold is named *Critical*, not
*Pause*. No approved automatic-pause equivalent exists for CVR. Do not infer one
from the CTR ladder — the two ladders are not symmetrical, and any pause
decision arising from low CVR is [VERIFY].

---

## 3. Decision Triggers

These are **statistical confidence thresholds**: the minimum amount of data
required before a bid change may be recommended at all. They are **not KPI
targets** and they are **not alert thresholds**. Nothing about them describes
good or bad performance — they describe whether there is *enough evidence to
form a view*.

**Authoritative source: `context/bid-rules.md`, section "Sample size before
acting".** The values are repeated here for reference only. If the two ever
disagree, `context/bid-rules.md` wins.

| Trigger | Value | Meaning |
|---------|-------|---------|
| Bid Action Minimum Clicks | **15** | The default minimum click volume before any bid change may be drafted |
| High Confidence Clicks | **25** | The higher bar required for larger bid moves, and for changes on Hero SKU campaigns |

**How to apply this.** A keyword sitting at 40% ACoS with 6 clicks has not
failed the KPI target — it has not yet produced enough data to be judged at
all. Recommending a bid cut on 6 clicks is acting on noise. Wait for 15 clicks.

Bid mechanics — floor, ceiling, multipliers, placement adjustment and rollback —
are deliberately **not** reproduced in this document. See
`context/bid-rules.md`.

---

## 4. Budget Minimums

These are **operational minimums**: the floor at which a campaign can function
at all. They are **not optimisation targets**. Nothing is "achieved" by
spending £2/day, and a campaign is not performing well because it meets the
minimum.

**Authoritative source: `context/budget-rules.md`, section "Daily budget
minimums".** The values are repeated here for reference only. If the two ever
disagree, `context/budget-rules.md` wins.

| Campaign type | Minimum daily budget |
|---------------|---------------------|
| Sponsored Products | **£2/day** (starting minimum) |
| Sponsored Brands | **£2/day** |
| Sponsored Display | [VERIFY] — no approved minimum daily budget is documented for Sponsored Display, although Sponsored Display KPI targets are defined in section 1 |

Budget override rules (SR-1 to SR-4), the stock gate, approval thresholds and
rollback procedure are deliberately **not** reproduced here. See
`context/budget-rules.md`.

---

## Dependency Matrix

Which skills consume which metrics. Only skills that exist in `skills/` are
listed.

**Read this table with care.** All ten skill files are currently stubs at
`Status: Not started` and none of them yet declares what it consumes.
Dependencies are therefore only recorded as confirmed where a source document
names the skill explicitly, or where the skill's own name states the metric.
Everything else is `[VERIFY]` — assumed-obvious mappings have deliberately not
been guessed.

| Metric | Used By |
|--------|---------|
| Overall Target ACoS | `acos-check` (skill named for the metric); all other consumers [VERIFY] |
| Overall Target ROAS | [VERIFY] — no skill names ROAS and no source document assigns it |
| Sponsored Products Target ACoS | `acos-check`; all others [VERIFY] |
| Sponsored Products Target ROAS | [VERIFY] |
| Sponsored Brands Target ACoS | `acos-check`; all others [VERIFY] |
| Sponsored Brands Target ROAS | [VERIFY] |
| Sponsored Display Target ACoS | `acos-check`; all others [VERIFY] |
| Sponsored Display Target ROAS | [VERIFY] |
| CTR Healthy Target (>0.5%) | [VERIFY] |
| CTR Review (0.3%) / CTR Pause (0.2%) | [VERIFY] |
| CVR Healthy Target (>10%) | [VERIFY] |
| CVR Review (7%) / CVR Critical (5%) | [VERIFY] |
| Bid Action Minimum Clicks (15) | `bid-check` — **confirmed**: `context/bid-rules.md` explicitly names `/bid-check` as the consumer of its bid logic |
| High Confidence Clicks (25) | `bid-check` — **confirmed**, same source |
| Budget Minimums (£2/day SP, £2/day SB) | `budget-check` — **confirmed**: `context/budget-rules.md` explicitly names `/budget-check` as the consumer of its budget logic |

Skills existing in `skills/` with no confirmed dependency on this document:
`ppc-brief`, `search-term-check`, `waste-scan`, `keyword-expand`,
`campaign-audit`, `report-draft`, `scale-check`. Each is [VERIFY] and should be
filled in as that skill is defined, not before.

---

## Known Limitations

Genuine unresolved items. Each blocks a specific downstream use.

1. **Two of four evidence sources are not in this repository.**
   `Amazon_BGCT_PayPerClick.pdf` and the Approved PPC Metrics record
   (2026-07-22) are external. Until they are filed in `evidence/`, no reader can
   independently verify any KPI target or alert threshold in this document.
2. **Governance roles undefined.** Business Owner, Technical Reviewer and
   Queryability Reviewer have no definition anywhere in this repository. Until
   defined, this document has an owner but no approver.
3. **ACoS and ROAS have no warning or critical thresholds.** Only CTR and CVR
   have a full healthy → review → critical ladder. There is currently no
   approved answer to "at what ACoS do we escalate?"
4. **No CPC target range.** `context/bid-rules.md` states explicitly that no
   fixed target CPC exists and that CPC must be derived per-SKU from max CPA and
   minimum True Margin. No CPC figure belongs in this document.
5. **No TACoS target.** Total Advertising Cost of Sales (advertising spend
   against *total* sales, not just advertising-attributed sales) is not defined
   anywhere in this repository. Without it, the effect of PPC on overall
   business performance cannot be measured.
6. **Marketplace-specific KPI overrides.** All values here are unlabelled by
   marketplace, and both rule files are denominated in GBP (£), implying UK.
   Whether these targets apply unchanged to other marketplaces is undocumented.
7. **Non-UK values missing.** `context/budget-rules.md` already records that
   non-UK values for Spend Pause Rules 2–3 are blank in all source documents.
   The same gap applies to the KPI targets here.
8. **No Sponsored Display budget minimum.** Sponsored Display has KPI targets in
   section 1 but no documented minimum daily budget.
9. **Campaign-specific and SKU-specific KPI overrides.** Both rule files refer
   to "Hero SKU" campaigns as warranting a higher confidence bar, implying some
   campaigns are treated differently. Whether Hero SKUs or any other campaign
   class carry different KPI targets is undocumented.
10. **Review frequency undefined for every metric.**
    `context/reporting-schedule.md` remains an undocumented placeholder, so no
    metric in this document has an approved review cadence.
11. **No defined action for the monitoring bands.** CTR between 0.5% and 0.3%,
    and CVR between 10% and 7%, are below target but above the review threshold.
    No approved action exists for either band.

---

## Duplicate Truth Check

Performed 2026-07-22 across all `.md` files in this repository, searching for
`Target ACoS`, `Target ROAS`, `CTR`, `CVR`, `ROAS` and `ACoS`.

| Term | Found elsewhere? | Location | Values match? | Duplicate truth? |
|------|-----------------|----------|---------------|------------------|
| Target ACoS | No | — | — | No |
| Target ROAS | No | — | — | No |
| ROAS | No | — | — | No |
| CTR | No | — | — | No |
| CVR | No | — | — | No |
| ACoS (as a rule condition) | Yes | `context/bid-rules.md` (20% raise trigger, 15% early scaling signal); `context/budget-rules.md` (SR-1 to SR-4 conditions using 20% and 25%) | Not applicable — different purpose | **No.** Those are operational rule triggers and rule-entry conditions, not KPI targets. See the distinction table under **Purpose**. |

**No conflicting KPI definition exists anywhere in this repository.** The
numeral 25 appearing in `context/budget-rules.md` SR-3/SR-4 is a rule boundary
for a budget override, not a restatement of the <25% KPI target; the two are
independent and neither should be edited to match the other.

**target-metrics.md is now the canonical operational source for PPC target metrics.**

Any future document needing a target ACoS, ROAS, CTR or CVR value must link to
this file rather than restate the value.

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What metrics exist? | Yes | Sections 1–4 |
| Why are they used? | Yes | Purpose; Scope; Business Purpose field on each metric |
| Which are KPI targets? | Yes | Section 1, plus the distinction table under Purpose |
| Which are alert thresholds? | Yes | Section 2, with full escalation ladders |
| Which are decision triggers? | Yes | Section 3, explicitly labelled "not KPI targets" |
| Where did each value originate? | Yes | Evidence, with in-repo existence stated per source |
| Which files depend on these metrics? | Yes | Dependency Matrix, with unconfirmed links marked [VERIFY] |
| Which values still require verification? | Yes | Every `[VERIFY]` marker, consolidated in Known Limitations |

**Result: PASS**
