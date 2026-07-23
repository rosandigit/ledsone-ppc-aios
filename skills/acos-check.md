# ACoS Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews campaign
Advertising Cost of Sales (ACoS) against the targets defined in
`context/target-metrics.md` and prepares validated findings — within-target,
needs-review, insufficient-evidence, conflicting-evidence, and candidate
optimisation opportunities — for downstream review. It never judges beyond the
evidence, never decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `acos-check` |
| Purpose | Review campaign ACoS against the KPI targets in `context/target-metrics.md` (by reference) and prepare validated candidate findings for downstream review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); `context/target-metrics.md` names `acos-check` as a confirmed consumer of its ACoS targets. Routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** ACoS is the headline efficiency measure for the PPC
account (`context/target-metrics.md`, §1). Judging a campaign against it requires
enough approved evidence to be more than noise, and a clear separation between a
KPI target (is it succeeding?) and a rule trigger (should something change?). This
skill turns campaign performance evidence into a structured, evidence-checked
review: whether ACoS can be assessed at all, which campaigns are within target,
which need review, and where evidence is missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped an efficiency-related
request, and once campaign performance evidence (spend, sales, clicks,
conversions) for the campaign, marketplace and date range is available. If
evidence is missing or too thin to assess, the review records **Insufficient
Evidence** rather than proceeding to a finding.

**What evidence it reviews.** Amazon Ads campaign/advertising performance
reporting — spend, sales, clicks, conversions — for the scope in question (see
**Required Evidence**).

**What it deliberately does NOT do.** It does not optimise campaigns, change bids
or budgets, pause anything, or modify Amazon Ads. It does not decide whether to
scale or cut — it establishes, on evidence, whether ACoS is within target and
whether a review is warranted, then hands validated findings to a human/downstream
skill. It does not substitute a rule trigger for a KPI target: a campaign can be
on-target as a KPI yet not meet a bid-raise trigger, and both statements can be
true (`context/target-metrics.md`, Purpose). This skill reports the KPI position;
it does not fire rule actions.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Campaign Performance Report** — campaign performance evidence.
- **Advertising Report** — Amazon Ads spend/sales reporting.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated).
- **Date Range** — the reporting window (source, date and date range required per
  `README.md`).
- **Business Request** — the plain-language ask/objective.
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, currently an unpopulated stub; until it is
  populated, ASIN/SKU-to-campaign resolution cannot be completed — record as
  **Insufficient Evidence**, do not invent a mapping.

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their KPIs
or rules (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/target-metrics.md` | **Authoritative KPI targets** — ACoS/ROAS targets (overall and per ad type), CTR/CVR context, the decision triggers (§3), and the critical KPI-vs-rule-trigger distinction. Applied by reference only; never restated. |
| `context/bid-rules.md` | Sample-size gate (evidence sufficiency) and the ACoS raise trigger context, referenced when framing a finding for a downstream bid review |
| `context/budget-rules.md` | Budget minimums, overrides and stock gate, referenced when a finding implies a budget interaction |
| `context/campaign-list.md` | Campaign identity and type (ACoS targets are defined per ad type) |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md` | An upstream skill whose findings may prompt an ACoS review |
| `skills/bid-check.md` | A sibling review skill that may run before/after on the same campaign |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A review may produce candidate findings only when the relevant approved evidence
is available. Approved evidence includes:

- **Amazon Ads reports**
- **Campaign performance report**
- **Spend**
- **Sales**
- **Clicks**
- **Conversions**
- **Business request** (documented)

**Manual opinion alone is insufficient.** A performance claim made on opinion,
with no filed evidence behind it, cannot become a validated finding; the review
records the gap under **Evidence Missing** and sets **Insufficient Evidence**. All
evidence must be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a
missing source rather than proceeding on assumption. (At authoring, all Required
Context documents exist in the repository.)

---

## ACoS Review Workflow

```
Receive request
   ↓
Validate evidence                 (is approved performance evidence available?)
   ↓
Confirm sufficient performance data (enough spend/sales/clicks/conversions to assess?)
   ↓
Review ACoS against referenced Context (targets in context/target-metrics.md)
   ↓
Identify candidate findings        (within target / needs review / candidate opportunity)
   ↓
Check conflicting evidence         (do sources disagree?)
   ↓
Prepare structured review          (complete the Output Template)
   ↓
Recommend downstream skill         (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- It reads KPI targets from `context/target-metrics.md` **by reference** — it does
  not copy the target values here.
- A campaign with too little data to assess is recorded as **Insufficient
  Evidence**, never as a within-target or failing verdict.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty review template. All fields are blank; they are filled per request from
filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| ACoS Findings | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed review is evidence-review output, not an optimisation and not a
> report. Any `Recommended Action` is a DRAFT for human review — never an applied
> change. Store review output per repository convention (not as business rules in
> `context/`).

---

## Decision Rules

This skill:

- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** pause campaigns.
- Does **NOT** modify Amazon Ads.
- Does **NOT** duplicate KPI thresholds.

**Insufficient Evidence.** If evidence is missing or too thin to assess ACoS, set
**Validation Status = Insufficient Evidence**, record what is missing under
**Evidence Missing**, and do not produce a performance verdict.

**Conflict.** If evidence sources disagree (e.g. spend/sales figures differ
between sources), do not choose one source without justification. Set
**Validation Status = Conflict**, record every conflicting source, and require
**business review**.

**KPI targets by reference only.** All ACoS/ROAS/CTR/CVR targets and thresholds
are read from `context/target-metrics.md`. **Never duplicate them in this file.**
If they change, they change in `context/target-metrics.md` only. Do not treat a
bid-raise trigger or a budget rule boundary as a KPI target (see the distinction
in `context/target-metrics.md`).

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or applied change.

Any operational rule governing how findings are prioritised, escalated or
approved beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `budget-check` | ACoS findings interact with daily budgets, minimums, overrides or the stock gate (`context/budget-rules.md`) |
| `campaign-audit` | Findings suggest a broader structural issue warranting a full campaign review (`context/campaign-list.md`) |
| `report-draft` | The review is to be captured in a report under `context/reporting-schedule.md` |
| `scale-check` | Efficiency is strong enough to consider scaling, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Related sibling skill (not strictly downstream): `bid-check` — where an ACoS
finding points to a bid-level review, gated by the sample size in
`context/bid-rules.md`. Where the correct downstream skill is ambiguous or the
findings span several, the review records the options under **Recommended Next
Skill** and flags the ambiguity as an **Outstanding Question** rather than
guessing.

---

## Duplicate Truth Prevention

**This skill reviews evidence only. Business KPIs remain inside `context/`.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Bid rules** — reference `context/bid-rules.md`.
- **Budget rules** — reference `context/budget-rules.md`.
- **Campaign governance** — reference `context/campaign-list.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.

The review may *name* the relevant documents and *point to* the targets it
assesses against, but it must not restate those targets or values. If a value is
needed, link to its owning document. `context/target-metrics.md` is the single
source of every KPI target.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed performance evidence, the
  skill records the gap only; it cannot assess a campaign that is not evidenced.
- **Cannot infer future profitability.** It reviews historical evidence; it does
  not predict outcomes.
- **Cannot modify campaigns.** It produces DRAFT candidate findings only; any
  change is applied manually after human approval.
- **Cannot recommend optimisation without evidence.** Missing or insufficient
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign resolution cannot be completed. [VERIFY]
- **No approved ACoS warning/critical thresholds.** `context/target-metrics.md`
  records that ACoS/ROAS have target values but no approved warning or critical
  escalation thresholds; findings are limited accordingly. [VERIFY]
- **Unknown approval workflow.** How a review is approved before optimisation is
  drafted is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based review of campaign ACoS |
| When should it be used? | Yes | Purpose — after `ppc-brief`, when performance evidence is available |
| What evidence is required? | Yes | Required Evidence |
| Which Context documents are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**
