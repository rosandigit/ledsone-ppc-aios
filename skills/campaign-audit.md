# Campaign Audit Skill

An evidence-based consolidation skill for LEDSone Amazon PPC. It brings together
the **validated findings** produced by the upstream review skills into a single
structured campaign audit — overall health, validated strengths, validated risks,
unresolved evidence gaps, conflicts, and follow-up recommendations. It never
re-decides, never optimises, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `campaign-audit` |
| Purpose | Consolidate validated findings from the PPC Skills layer into one structured campaign audit for reporting and review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents and the outputs of upstream review skills (see **Required Context** / **Required Evidence**); routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief` and the individual review skills. It changes nothing. |

---

## Purpose

**Why this skill exists.** The review skills (`search-term-check`, `bid-check`,
`acos-check`, `budget-check`, `waste-scan`, `keyword-expand`) each produce validated
findings for one dimension. A campaign owner needs those brought together into one
coherent picture — what is healthy, what is at risk, what is unresolved — rather
than reading six separate reviews. This skill performs that consolidation into a
single structured audit.

**When it should be used.** After the relevant upstream review skills have run and
produced validated findings for the campaign in scope, and once `ppc-brief` has
established the objective. It can also be used to scope a full review, recommending
which review skills to run first where findings are missing.

**What evidence it reviews.** The **validated outputs of the upstream review
skills** (each an evidence-review record), plus the underlying Amazon Ads evidence
those reviews cite. It does not re-derive findings from raw data where a review
skill already owns that dimension; it consolidates and cross-checks them.

**What it deliberately does NOT do.** It does not optimise campaigns, change bids,
budgets or keywords, pause campaigns, or modify Amazon Ads. It does not overturn a
review skill's finding without evidence, and it does not invent findings for
dimensions that were never reviewed — a missing dimension is recorded as an
evidence gap, not assumed healthy. It consolidates validated evidence and hands a
structured audit to reporting and human review.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes from
the request, from filed evidence, or from upstream review outputs.

- **Upstream review outputs** — completed records from `search-term-check`,
  `bid-check`, `acos-check`, `budget-check`, `waste-scan`, `keyword-expand`.
- **Campaign Performance Report** and supporting Amazon Ads evidence the reviews
  cite.
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

Documents and skills this audit consults. It **references** them; it never copies
their rules or KPIs (see **Duplicate Truth Prevention**).

| Source | Consulted for |
|--------|---------------|
| `context/target-metrics.md` | KPI/threshold context to frame strengths/risks (by reference; `acos-check` owns the ACoS judgement) |
| `context/campaign-list.md` | Campaign identity, type and the register fields a complete audit expects |
| `context/keyword-strategy.md` | Keyword-dimension context for consolidating `search-term-check` / `keyword-expand` findings |
| `context/negative-keyword-master.md` | Negative-keyword context for consolidating waste/negation findings |
| `context/bid-rules.md` | Bid-dimension context (sample-size gate) for consolidating `bid-check` findings |
| `context/budget-rules.md` | Budget-dimension context for consolidating `budget-check` findings |
| `context/reporting-schedule.md` | Reporting governance — the audit is a report input |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md`, `skills/bid-check.md`, `skills/acos-check.md`, `skills/budget-check.md`, `skills/waste-scan.md`, `skills/keyword-expand.md` | The review skills whose validated findings this audit consolidates |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

An audit may consolidate findings only where the underlying reviews rest on approved
evidence. Approved evidence includes:

- **Validated upstream review outputs** (each citing its own approved evidence)
- **Amazon Ads reports** underlying those reviews
- **Campaign export / performance report**
- **Business request** (documented)

**Manual opinion alone is insufficient.** An audit judgement not backed by a
validated review or filed evidence cannot stand; it is recorded under **Evidence
Missing** and set to **Insufficient Evidence**. All evidence must be filed per
`README.md` with its source, date and date range.

If any Required Context document or upstream review is missing at run time, record
it here as a missing source rather than proceeding on assumption. (At authoring,
all Required Context documents and review skills exist in the repository; upstream
*review outputs* are produced per run and may be absent — that is an evidence gap,
not a defect.)

---

## Campaign Audit Workflow

```
Receive request
   ↓
Validate evidence            (which upstream review outputs / evidence are available?)
   ↓
Identify coverage gaps       (which review dimensions have NOT been run?)
   ↓
Consolidate validated findings (strengths, risks, per dimension — by reference)
   ↓
Cross-check for conflicts    (do dimensions or sources disagree?)
   ↓
Assess evidence quality      (sufficient? sub-threshold? missing?)
   ↓
Prepare structured audit     (complete the Output Template)
   ↓
Recommend downstream skill   (route per the Dependency Matrix)
```

- The skill produces a consolidated audit and a routing recommendation only. It
  does not execute any skill and it does not act on Amazon Ads.
- It reads all rules and KPIs from the relevant `context/` documents **by
  reference** — it does not copy them here.
- A dimension with no validated review is recorded as a **coverage gap /
  Insufficient Evidence**, never assumed healthy or failing. The audit may
  recommend running the missing review skill first.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty audit template. All fields are blank; they are filled per request from
validated upstream findings and filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Audit Findings | *(empty)* |
| Strengths | *(empty)* |
| Risks | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed audit is consolidated evidence-review output, not an optimisation
> and not a final report. Any `Recommended Action` is a DRAFT for human review —
> never an applied change. Store audit output per repository convention (not as
> business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** modify campaigns.
- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** create keywords.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If required review outputs or evidence are missing, set
**Validation Status = Insufficient Evidence**, record what is missing under
**Evidence Missing**, and record the affected dimensions as coverage gaps rather
than producing a verdict for them.

**Conflict.** If dimensions or evidence sources disagree (e.g. a bid finding and a
budget finding imply opposite actions, or two sources report different figures), do
not choose one without justification. Set **Validation Status = Conflict**, record
every conflicting source/finding, and require **business review**.

**Rules by reference only.** All KPI targets, bid rules, budget rules, keyword and
reporting governance are read from the relevant `context/` documents. **Never
duplicate them in this file.**

**Consolidates, does not overturn.** The audit reflects the validated findings of
the review skills; it does not silently override them. A disagreement with a review
finding is raised as a **Conflict** for human review, not resolved unilaterally.

Any operational rule governing how audits are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this audit may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `report-draft` | The consolidated audit is to be turned into a report under `context/reporting-schedule.md` |
| `scale-check` | The audit shows validated strength and headroom, making the campaign a scaling candidate, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Upstream review skills (`search-term-check`, `bid-check`, `acos-check`,
`budget-check`, `waste-scan`, `keyword-expand`) are **inputs** to this audit — where
a dimension has not been reviewed, the audit may recommend running the relevant
review skill first. Where the correct downstream skill is ambiguous or the findings
span several, the audit records the options under **Recommended Next Skill** and
flags the ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill consolidates evidence only. Business rules remain inside `context/`.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Bid rules** — reference `context/bid-rules.md`.
- **Budget rules** — reference `context/budget-rules.md`.
- **Keyword governance** — reference `context/keyword-strategy.md` and
  `context/negative-keyword-master.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The audit may *name* the relevant documents and *point to* the rules a review
applied, but it must not restate those rules or values, and it must not restate the
full content of the upstream reviews — it consolidates and links to them. If a value
is needed, link to its owning document.

---

## Known Limitations

- **Cannot audit un-reviewed dimensions.** A dimension with no validated review is
  a coverage gap; the audit records it, it does not fill it by assumption.
- **Cannot analyse missing reports.** With no filed evidence or review outputs, the
  audit records the gap only.
- **Cannot infer future performance.** It consolidates historical/validated
  evidence; it does not predict outcomes.
- **Cannot modify campaigns.** It produces a DRAFT consolidated audit only; any
  change is applied manually after human approval.
- **Cannot recommend optimisation without evidence.** Missing or insufficient
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign resolution cannot be completed. [VERIFY]
- **Inherits upstream `[VERIFY]` gaps.** Any dimension whose governing document has
  open `[VERIFY]` items (e.g. no ACoS warning/critical thresholds, undefined
  approval workflow) carries those limits into the audit. [VERIFY]
- **Unknown approval workflow.** How an audit is approved before action is
  undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — consolidates validated findings into a campaign audit |
| When should it be used? | Yes | Purpose — after the review skills have produced findings |
| What evidence is required? | Yes | Required Evidence |
| Which Context and Skills are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/campaign-audit.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or KPI targets duplicated — all referenced to their owning
  `context/` documents; upstream reviews consolidated by reference, not restated
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
