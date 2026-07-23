# Bid Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews Amazon Ads bid
performance and prepares validated findings — candidate increases, candidate
decreases, bids to keep observing, and evidence gaps — for downstream review. It
never calculates a bid, never decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `bid-check` |
| Purpose | Review bid performance evidence and prepare validated candidate findings for downstream review, applying the gates in `context/bid-rules.md` by reference |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); `context/bid-rules.md` explicitly names `/bid-check` as the consumer of its bid logic. Routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** Bid decisions must rest on enough approved evidence to
be more than noise (`context/bid-rules.md`, "Sample size before acting";
`context/target-metrics.md`, §3). This skill turns bid-performance evidence into
a structured, gated review: whether there is enough data to judge a bid at all,
which bids look like candidate increases or decreases, which need continued
observation, and where evidence is missing or conflicting. It standardises that
review so a human — and any downstream skill — starts from validated findings.

**When it should be used.** After `ppc-brief` has scoped a bid-related request,
and once bid-performance evidence (clicks, conversions, spend) for the campaign,
ad group, marketplace and date range is available. If evidence is missing or
below the sample-size gate in `context/bid-rules.md`, the review records
**Insufficient Evidence** rather than proceeding to a finding.

**What evidence it reviews.** Amazon Ads campaign/bid performance reporting —
click history, conversion evidence and spend — for the scope in question (see
**Required Evidence**).

**What it deliberately does NOT do.** It does not optimise or calculate bids, does
not apply the multiplier or floor/ceiling from `context/bid-rules.md` as an
action, does not change budgets, pause campaigns, create keywords, or modify
Amazon Ads. It evaluates whether the evidence *supports reviewing* current bids
and hands validated findings to a human/downstream skill. Any actual bid change
is drafted, approved by a human, and applied manually — never here.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Campaign Performance Report** — campaign/ad-group performance evidence.
- **Bid Report** — current bids and their performance.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Ad Group** — the ad group in scope.
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated).
- **Date Range** — the reporting window (source, date and date range required per
  `README.md`).
- **Business Request** — the plain-language ask/objective.
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, currently an unpopulated stub; until it is
  populated, ASIN/SKU-to-campaign resolution cannot be completed — record as
  **Insufficient Evidence**, do not invent a mapping. (Relevant because
  `context/bid-rules.md` treats Hero SKU campaigns with a higher confidence bar.)

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their
contents or thresholds (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/bid-rules.md` | **Authoritative bid logic** — the sample-size gate, ACoS raise trigger, bid floor/ceiling, multiplier method, placement cap, CPC derivation and rollback. Applied by reference only; never restated. |
| `context/target-metrics.md` | KPI/threshold context (ACoS/ROAS/CTR/CVR) and the §3 decision triggers a finding is framed against |
| `context/campaign-list.md` | Campaign/ad-group identity and the campaign type (bid logic is type-aware) |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md` | An upstream skill that may surface a keyword whose bid then warrants review |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A review may produce candidate findings only when the relevant approved evidence
is available. Approved evidence includes:

- **Amazon Ads reports**
- **Campaign export**
- **Bid performance data**
- **Click history**
- **Conversion evidence**
- **Business request** (documented)

**Manual opinion alone is insufficient.** A bid flagged on opinion, with no filed
evidence behind it, cannot become a validated finding; the review records the gap
under **Evidence Missing** and sets **Insufficient Evidence**. All evidence must
be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a
missing source rather than proceeding on assumption. (At authoring, all Required
Context documents exist in the repository.)

---

## Bid Review Workflow

```
Receive request
   ↓
Validate evidence            (is approved bid-performance evidence available?)
   ↓
Confirm sample size          (meets the click gate in context/bid-rules.md?)
   ↓
Review bid performance       (against KPI/trigger context in context/target-metrics.md)
   ↓
Identify candidate findings  (candidate increase / decrease / continue observing)
   ↓
Check for conflicting evidence (do sources disagree?)
   ↓
Prepare structured review    (complete the Output Template)
   ↓
Recommend downstream skill   (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- A bid with too little data to judge (below the sample-size gate in
  `context/bid-rules.md`) is recorded as **Insufficient Evidence / continue
  observing**, never as a change candidate.
- The skill applies `context/bid-rules.md` gates **by reference** — it reads the
  thresholds from that file; it does not copy them here.
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
| Bid Findings | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed review is evidence-review output, not a bid change and not a
> report. Any `Recommended Action` is a DRAFT for human review — never an applied
> change. Store review output per repository convention (not as business rules in
> `context/`).

---

## Decision Rules

This skill:

- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** pause campaigns.
- Does **NOT** create keywords.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If evidence is missing or below the sample-size gate in
`context/bid-rules.md`, set **Validation Status = Insufficient Evidence**, record
what is missing under **Evidence Missing**, and do not produce a change finding.

**Conflict.** If evidence sources disagree (e.g. on performance, or on whether a
bid should move), do not choose one source without justification. Set
**Validation Status = Conflict**, record every conflicting source, and require
**business review**.

**Thresholds by reference only.** All bid thresholds — sample size, ACoS raise
trigger, floor, ceiling, multiplier, placement cap, CPC derivation — are read
from `context/bid-rules.md`. **Never duplicate them in this file.** If they
change, they change in `context/bid-rules.md` only.

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or applied bid change.

Any operational rule governing how findings are prioritised, escalated or
approved beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `acos-check` | Bid findings need framing against the ACoS/ROAS efficiency targets in `context/target-metrics.md` |
| `budget-check` | A bid finding implies a budget constraint or interacts with the minimums/overrides in `context/budget-rules.md` |
| `campaign-audit` | Findings suggest a broader structural issue warranting a full campaign review (`context/campaign-list.md`) |
| `report-draft` | The review is to be captured in a report under `context/reporting-schedule.md` |
| `scale-check` | Strong efficiency suggests scaling, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Where the correct downstream skill is ambiguous or the findings span several, the
review records the options under **Recommended Next Skill** and flags the
ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill reviews evidence only. Business rules remain in `context/`.**

Never duplicate:

- **KPIs** — reference `context/target-metrics.md`.
- **Bid rules** (sample size, triggers, floor/ceiling, multiplier, placement cap,
  CPC, rollback) — reference `context/bid-rules.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rules it applies,
but it must not restate those rules or values. If a value is needed, link to its
owning document. `context/bid-rules.md` is the single source of every bid
threshold.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed bid-performance evidence, the
  skill records the gap only; it cannot review bids that are not evidenced.
- **Cannot infer future performance.** It reviews historical evidence; it does not
  predict outcomes.
- **Cannot change bids.** It produces DRAFT candidate findings only; any change is
  applied manually after human approval.
- **Cannot invent optimisation decisions.** Findings come only from the evidence
  and the gates in `context/bid-rules.md`.
- **Cannot recommend bid changes without evidence.** Missing or sub-threshold
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU (incl. Hero SKU) resolution cannot be completed.
  [VERIFY]
- **Unknown approval workflow.** How a review is approved before a bid change is
  drafted/applied is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based review of bid performance |
| When should it be used? | Yes | Purpose — after `ppc-brief`, when bid-performance evidence is available |
| What evidence is required? | Yes | Required Evidence |
| Which Context documents are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**
