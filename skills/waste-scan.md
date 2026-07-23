# Waste Scan Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews campaign
evidence to identify potential **wasted advertising spend** and prepares validated
findings — candidate waste, needs-investigation, insufficient-evidence,
conflicting-evidence, and optimisation opportunities for later review — for
downstream skills. It never optimises, never decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `waste-scan` |
| Purpose | Review campaign evidence to identify candidate wasted spend and prepare validated findings for downstream review, applying Context rules by reference |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief` and often `search-term-check`. It changes nothing. |

---

## Purpose

**Why this skill exists.** Wasted spend — clicks and cost that do not convert, or
spend on irrelevant search terms — erodes efficiency against the targets in
`context/target-metrics.md` and the budgets governed by `context/budget-rules.md`.
This skill turns campaign evidence into a structured, evidence-checked scan:
whether the evidence supports a waste investigation, which spend looks like
candidate waste, which findings need deeper investigation, and where evidence is
missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped a waste/efficiency
request, and often after `search-term-check` has surfaced irrelevant terms. It
runs once campaign performance and spend evidence (spend, clicks, conversions,
search terms) for the campaign, marketplace and date range is available. If
evidence is missing or too thin, the scan records **Insufficient Evidence** rather
than proceeding to a finding.

**What evidence it reviews.** Amazon Ads campaign/search-term/spend reporting for
the scope in question (see **Required Evidence**).

**What it deliberately does NOT do.** It does not optimise campaigns, change bids
or budgets, pause campaigns, add or remove keywords or negatives, or modify Amazon
Ads. It identifies *candidate* waste on evidence — applying the sample-size gate in
`context/bid-rules.md` so it flags waste on data, not noise — and hands validated
findings to a human/downstream skill. Deciding what to do about the waste
(negate, cut a bid, reallocate budget) belongs to the downstream skills and human
approval, not here.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Campaign Performance Report** — spend, clicks, conversions.
- **Search Term Report** — for term-level waste (irrelevant / non-converting terms).
- **Budget / spend data** — where waste relates to budget utilisation.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Ad Group** — where relevant to the scope.
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

Documents this skill consults. It **references** them; it never copies their rules
or KPIs (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/target-metrics.md` | Efficiency targets and CTR/CVR context a waste finding is framed against |
| `context/bid-rules.md` | Sample-size gate (evidence sufficiency) — waste is judged on adequate data, not noise |
| `context/budget-rules.md` | Budget context (minimums, overrides, stock gate) where waste relates to budget |
| `context/keyword-strategy.md` | Keyword classification/lifecycle relevant to term-level waste |
| `context/negative-keyword-master.md` | Negative-keyword governance where a waste term is a negation candidate; conflict handling |
| `context/campaign-list.md` | Campaign identity and type |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the scan output |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md` | An upstream skill whose term findings often feed this scan |
| `skills/bid-check.md` | A sibling review skill whose findings may interact with waste |
| `skills/acos-check.md` | A sibling review skill whose efficiency findings may prompt a waste scan |
| `skills/budget-check.md` | A sibling review skill whose unused-budget findings may prompt a waste scan |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A scan may produce candidate findings only when the relevant approved evidence is
available. Approved evidence includes:

- **Amazon Ads reports**
- **Campaign performance report**
- **Search Term Report**
- **Spend, clicks and conversion data**
- **Budget / spend data**
- **Business request** (documented)

**Manual opinion alone is insufficient.** Waste flagged on opinion, with no filed
evidence behind it, cannot become a validated finding; the scan records the gap
under **Evidence Missing** and sets **Insufficient Evidence**. All evidence must be
filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a
missing source rather than proceeding on assumption. (At authoring, all Required
Context documents exist in the repository.)

---

## Waste Review Workflow

```
Receive request
   ↓
Validate evidence            (is approved spend/performance evidence available?)
   ↓
Confirm sufficient data      (meets the sample-size gate in context/bid-rules.md?)
   ↓
Scan for candidate waste     (non-converting spend, irrelevant terms, low-efficiency spend)
   ↓
Identify candidate findings  (candidate waste / needs investigation)
   ↓
Check for conflicting evidence (do sources disagree?)
   ↓
Prepare structured review    (complete the Output Template)
   ↓
Recommend downstream skill   (route per the Dependency Matrix)
```

- The skill produces a scan review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- It reads all thresholds and rules from the relevant `context/` documents **by
  reference** — it does not copy them here.
- Spend with too little data to judge (below the sample-size gate in
  `context/bid-rules.md`) is recorded as **Insufficient Evidence / needs
  observation**, never as confirmed waste.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty scan template. All fields are blank; they are filled per request from
filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Waste Scan Findings | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed scan is evidence-review output, not an optimisation and not a
> report. Any `Recommended Action` is a DRAFT for human review — never an applied
> change. Candidate waste is a *candidate for downstream skills to evaluate*, not
> an approved negation, bid cut or budget change. Store scan output per repository
> convention (not as business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** change budgets.
- Does **NOT** change bids.
- Does **NOT** pause campaigns.
- Does **NOT** add or remove keywords.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If evidence is missing or below the sample-size gate in
`context/bid-rules.md`, set **Validation Status = Insufficient Evidence**, record
what is missing under **Evidence Missing**, and do not produce a confirmed-waste
finding.

**Conflict.** If evidence sources disagree (e.g. spend/conversion figures differ
between sources, or a term's classification is disputed), do not choose one source
without justification. Set **Validation Status = Conflict**, record every
conflicting source, and require **business review** (consistent with
`context/negative-keyword-master.md` and `context/keyword-strategy.md`).

**Rules by reference only.** All thresholds and rules — KPI targets, sample-size
gate, budget rules, keyword and negative-keyword governance — are read from the
relevant `context/` documents. **Never duplicate them in this file.**

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or applied change.

Any operational rule governing how findings are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this scan may route to. **Only skills that exist in `skills/` are
listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `keyword-expand` | Waste review reveals gaps where new, better-targeted keywords should be evaluated (`context/keyword-strategy.md`) |
| `campaign-audit` | Findings suggest a broader structural problem warranting a full campaign review (`context/campaign-list.md`) |
| `report-draft` | The scan is to be captured in a report under `context/reporting-schedule.md` |
| `scale-check` | Removing waste frees efficient headroom that may support scaling, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Related sibling skills (not strictly downstream): `search-term-check` (for
term-level negation candidates), `bid-check` and `budget-check` (where waste points
to a bid or budget review). Where the correct downstream skill is ambiguous or the
findings span several, the scan records the options under **Recommended Next
Skill** and flags the ambiguity as an **Outstanding Question** rather than
guessing.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Bid rules** (incl. the sample-size gate) — reference `context/bid-rules.md`.
- **Budget rules** — reference `context/budget-rules.md`.
- **Keyword strategy** — reference `context/keyword-strategy.md`.
- **Negative keyword governance** — reference `context/negative-keyword-master.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The scan may *name* the relevant documents and *point to* the rules it applies, but
it must not restate those rules or values. If a value is needed, link to its owning
document.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed spend/performance evidence, the
  skill records the gap only; it cannot scan spend that is not evidenced.
- **Cannot infer future waste.** It reviews historical evidence; it does not
  predict outcomes.
- **Cannot optimise campaigns.** It produces DRAFT candidate findings only; any
  change is applied manually after human approval.
- **Cannot recommend optimisation without evidence.** Missing or sub-threshold
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign resolution cannot be completed. [VERIFY]
- **Waste thresholds not centrally defined.** No approved numeric "waste" threshold
  (e.g. clicks-without-order cut-off) exists in `context/`; the scan relies on the
  sample-size gate and evidence, and flags any threshold judgement as [VERIFY]
  until an approved rule exists. [VERIFY]
- **Unknown approval workflow.** How a scan is approved before optimisation is
  drafted is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based scan for wasted spend |
| When should it be used? | Yes | Purpose — after `ppc-brief`, often after `search-term-check` |
| What evidence is required? | Yes | Required Evidence |
| Which Context documents are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/waste-scan.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or KPI targets duplicated — all referenced to their owning
  `context/` documents
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
