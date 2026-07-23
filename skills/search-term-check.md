# Search Term Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews Amazon Ads
Search Term data and prepares validated findings — candidate keywords, candidate
negatives, irrelevant terms, and evidence gaps — for downstream skills. It never
analyses beyond the evidence, never decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `search-term-check` |
| Purpose | Perform an evidence-based review of Search Term data and prepare validated candidate findings for downstream skills |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** The Search Term Report is the primary source of new
keyword opportunities and of wasted spend to exclude (`context/keyword-strategy.md`,
`context/negative-keyword-master.md`). This skill turns that raw report into a
structured, evidence-checked review: which terms look like keyword candidates,
which look like negative candidates, which are irrelevant, and where the evidence
is insufficient to say. It standardises that review so downstream skills act on
validated findings rather than raw data.

**When it should be used.** After `ppc-brief` has scoped a request that concerns
search terms, and once a Search Term Report (or equivalent approved evidence) is
available. If no report is available, this skill records **Insufficient Evidence**
rather than proceeding.

**What evidence it reviews.** Amazon Search Term Reports and related Amazon Ads
reporting for the campaign, ad group, marketplace and date range in scope (see
**Required Evidence**).

**What it deliberately does NOT do.** It does not make optimisation decisions. It
does not add keywords or negatives, does not calculate or change bids or budgets,
does not pause anything, and does not judge campaign performance against KPI
targets. It classifies and validates search-term findings and hands them to the
correct downstream skill. Customer intent is inferred by no one here — a term is
classified only on the evidence, and anything uncertain is left under review or
marked `[VERIFY]`.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Search Term Report** — the core evidence (Amazon Ads search-term export).
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
  **Insufficient Evidence**, do not invent a mapping.

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their
contents (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/keyword-strategy.md` | Keyword categories, match types, discovery sources and lifecycle used to classify candidate keywords |
| `context/negative-keyword-master.md` | Negative-keyword categories, evidence and lifecycle used to classify candidate negatives; conflict handling |
| `context/campaign-list.md` | Campaign/ad-group identity for the terms in scope |
| `context/target-metrics.md` | KPI/threshold context a downstream skill will judge against (referenced only; this skill does not judge performance) |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output |
| `context/bid-rules.md` | Sample-size gate (15 / 25 clicks) that governs whether a term has enough data to be acted on downstream |
| `context/budget-rules.md` | Budget governance context relevant to any waste finding |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness); `skills/ppc-brief.md` (the upstream skill that scopes the request).

---

## Required Evidence

A review may produce candidate findings only when the relevant approved evidence
is available. Approved evidence includes:

- **Amazon Search Term Report**
- **Amazon Ads reports**
- **Campaign export**
- **Business request** (documented)
- **Approved operational evidence**

**Manual opinion alone is insufficient.** A term flagged on opinion, with no
filed evidence behind it, cannot become a validated candidate; the review records
the gap under **Evidence Missing** and sets **Insufficient Evidence**. All
evidence must be filed per `README.md` with its source, date and date range.

---

## Review Workflow

```
Receive request
   ↓
Validate evidence            (is an approved Search Term Report available?)
   ↓
Identify search terms        (terms in scope for the campaign/ad group/date range)
   ↓
Check evidence quality       (sample size per context/bid-rules.md; data completeness)
   ↓
Identify candidate findings  (candidate keywords / candidate negatives / irrelevant)
   ↓
Flag insufficient evidence   (where data is missing or below the sample-size gate)
   ↓
Prepare structured review    (complete the Output Template)
   ↓
Recommend downstream skill   (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- A term with too little data to judge (below the sample-size gate in
  `context/bid-rules.md`) is **not** classified as a decision; it is recorded as
  under review / insufficient evidence.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty review template. All fields are blank; they are filled per request from
the actual Search Term Report and filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Search Term Findings | *(empty)* |
| Candidate Keywords | *(empty)* |
| Candidate Negative Keywords | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed review is evidence-review output, not a recommendation to act and
> not a report. Candidate keywords and candidate negatives are **candidates for
> downstream skills to evaluate** — they are not approved keywords or negatives.
> Store review output per repository convention (not as business rules in
> `context/`).

---

## Decision Rules

This skill:

- Does **NOT** optimise bids.
- Does **NOT** pause campaigns.
- Does **NOT** add keywords.
- Does **NOT** add negatives.
- Does **NOT** change budgets.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If evidence is missing or below the sample-size gate in
`context/bid-rules.md`, the skill does not produce a validated finding. It states
**Insufficient Evidence** and records what is missing under **Evidence Missing**.

**Conflict.** If evidence sources disagree on a term's classification, match type
or status, do not choose one source without justification. Set **Validation
Status = Conflict**, record every conflicting source, and require **business
review** before the finding is used (consistent with
`context/negative-keyword-master.md` and `context/keyword-strategy.md`).

**Candidates, not decisions.** Every keyword or negative this skill surfaces is a
*candidate* for a downstream skill; it is never an approved change.

Any operational rule governing how findings are prioritised, escalated or
approved is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `keyword-expand` | Candidate keywords identified — new targeting terms to evaluate for addition (`context/keyword-strategy.md`) |
| `waste-scan` | Terms show spend without return — candidates for negation or deeper waste review |
| `bid-check` | A term is an existing keyword whose bid may need review, once the sample-size gate in `context/bid-rules.md` is met |
| `budget-check` | Findings indicate a budget constraint or waste affecting daily budget (`context/budget-rules.md`) |
| `campaign-audit` | Findings suggest a broader structural issue warranting a full campaign review (`context/campaign-list.md`) |
| `report-draft` | The review is to be captured in a report under `context/reporting-schedule.md` |

Where the correct downstream skill is ambiguous or the findings span several, the
review records the options under **Recommended Next Skill** and flags the
ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

- **Never duplicate KPIs** — reference `context/target-metrics.md`.
- **Never duplicate keyword strategy** — reference `context/keyword-strategy.md`.
- **Never duplicate negative keyword governance** — reference
  `context/negative-keyword-master.md`.
- **Never duplicate reporting governance** — reference
  `context/reporting-schedule.md`.
- **Never duplicate bid or budget rules** — reference `context/bid-rules.md` and
  `context/budget-rules.md`.
- **Never duplicate campaign records** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rules a
downstream skill will apply, but it must not restate those rules or values. If a
value is needed, link to its owning document.

---

## Known Limitations

- **Cannot analyse missing Search Term Reports.** With no filed report, the skill
  records the gap only; it cannot review terms that are not present.
- **Cannot infer customer intent.** Terms are classified on evidence, not assumed
  intent; uncertain terms stay under review.
- **Cannot invent keywords.** Candidate keywords come only from terms present in
  the evidence.
- **Cannot invent negative keywords.** Candidate negatives come only from terms
  present in the evidence.
- **Cannot recommend optimisation without evidence.** Missing or sub-threshold
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign mapping cannot be completed. [VERIFY]
- **Unknown approval workflow.** How a review is reviewed/approved before
  downstream action is undocumented. [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based review of Search Term data |
| When should it be used? | Yes | Purpose — after `ppc-brief`, when a Search Term Report is available |
| What evidence is required? | Yes | Required Evidence |
| What Context documents does it consume? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills may follow? | Yes | Dependency Matrix |

**Result: PASS**
