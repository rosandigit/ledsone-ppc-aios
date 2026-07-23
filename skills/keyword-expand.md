# Keyword Expansion Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews campaign and
search-term evidence to identify candidate keyword **expansion** opportunities —
new keywords, match-type expansion, and grouping — and prepares validated findings
for downstream review. It never creates a keyword, never decides, and never
changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `keyword-expand` |
| Purpose | Review evidence to identify candidate keyword expansion opportunities and prepare validated findings for downstream review, applying `context/keyword-strategy.md` by reference |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief` and often `search-term-check`. It changes nothing. |

---

## Purpose

**Why this skill exists.** Growth in Sponsored Products/Brands/Display depends on
finding new, relevant keywords and promoting proven ones — the discovery-to-exact
progression described in `context/keyword-strategy.md`. Doing that safely requires
approved evidence and the strategy's classification, match-type and lifecycle
rules. This skill turns search-term and performance evidence into a structured,
evidence-checked review: which terms are candidate new keywords, which existing
keywords are candidates for match-type expansion, which suggest grouping, and where
evidence is missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped an expansion/growth
request, and often after `search-term-check` has surfaced candidate terms. It runs
once search-term and performance evidence for the campaign, marketplace and date
range is available. If evidence is missing or too thin, the review records
**Insufficient Evidence** rather than proposing candidates.

**What evidence it reviews.** Amazon Search Term Reports, keyword/performance
reporting, and any approved keyword-research export (e.g. Helium 10, Brand
Analytics) for the scope in question (see **Required Evidence**).

**What it deliberately does NOT do.** It does not create or add keywords, does not
change match types in Amazon Ads, does not modify campaigns, bids or budgets, and
does not modify Amazon Ads. It classifies *candidate* expansion opportunities on
evidence and hands validated findings to a human/downstream skill. It also does
not negate terms — a term that is waste, not opportunity, is routed to
`search-term-check` / `waste-scan` under `context/negative-keyword-master.md`, not
proposed as a keyword.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Search Term Report** — the primary source of candidate new keywords.
- **Keyword / Performance Report** — for match-type expansion of existing keywords.
- **Approved keyword-research export** — e.g. Helium 10, Amazon Brand Analytics
  (approved discovery sources in `context/keyword-strategy.md`).
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Ad Group** — where relevant to grouping findings.
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated;
  language/marketplace keyword strategy is `[VERIFY]` in `context/keyword-strategy.md`).
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
or governance (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/keyword-strategy.md` | **Authoritative keyword strategy** — categories, match types, approved discovery sources, lifecycle (candidate→exact), validation. Applied by reference only; never restated. |
| `context/negative-keyword-master.md` | Negative-keyword governance — to ensure a waste term is routed to negation, not proposed as a keyword; conflict handling |
| `context/target-metrics.md` | Efficiency/CTR/CVR context an expansion candidate is framed against |
| `context/campaign-list.md` | Campaign/ad-group identity and type (match support may vary by type) |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md` | An upstream skill whose candidate-keyword findings feed this review |
| `skills/bid-check.md` | A sibling review skill (a new keyword will later need a bid, gated by `context/bid-rules.md`) |
| `skills/acos-check.md` | A sibling review skill whose efficiency findings may prompt expansion |
| `skills/budget-check.md` | A sibling review skill (expansion may require budget headroom) |
| `skills/waste-scan.md` | A sibling review skill separating waste (negate) from opportunity (expand) |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A review may produce candidate findings only when the relevant approved evidence
is available. Approved evidence includes:

- **Amazon Search Term Report**
- **Amazon Keyword / performance report**
- **Helium 10 export**
- **Amazon Brand Analytics**
- **Amazon Ads reports**
- **Business request** (documented)

**Manual opinion alone is insufficient.** A keyword proposed on opinion, with no
filed evidence behind it, cannot become a validated candidate; the review records
the gap under **Evidence Missing** and sets **Insufficient Evidence**. All evidence
must be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a
missing source rather than proceeding on assumption. (At authoring, all Required
Context documents exist in the repository.)

---

## Keyword Expansion Workflow

```
Receive request
   ↓
Validate evidence            (is approved search-term/keyword evidence available?)
   ↓
Confirm sufficient data      (enough evidence to judge relevance/performance?)
   ↓
Identify expansion candidates (new keywords / match-type expansion / grouping)
   ↓
Classify per strategy         (categories, match types, lifecycle — by reference)
   ↓
Check for conflicting evidence (do sources disagree? is a term a negation candidate instead?)
   ↓
Prepare structured review     (complete the Output Template)
   ↓
Recommend downstream skill    (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- It reads keyword categories, match types, discovery sources and lifecycle from
  `context/keyword-strategy.md` **by reference** — it does not copy them here.
- A candidate with too little data to judge is recorded as **Insufficient
  Evidence**, never as a proposed keyword.
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
| Keyword Expansion Findings | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed review is evidence-review output, not a keyword addition and not a
> report. Candidate keywords, match-type expansions and groupings are *candidates
> for downstream review and human approval* — they are not added keywords. Any
> `Recommended Action` is a DRAFT. Store review output per repository convention
> (not as business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** create keywords.
- Does **NOT** modify campaigns.
- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If evidence is missing or too thin to judge a candidate,
set **Validation Status = Insufficient Evidence**, record what is missing under
**Evidence Missing**, and do not propose the candidate.

**Conflict.** If evidence sources disagree on a term's classification, match type
or whether it is an opportunity versus waste, do not choose one source without
justification. Set **Validation Status = Conflict**, record every conflicting
source, and require **business review** (consistent with
`context/keyword-strategy.md` and `context/negative-keyword-master.md`).

**Governance by reference only.** All keyword categories, match types, discovery
sources, lifecycle and negative-keyword governance are read from
`context/keyword-strategy.md` and `context/negative-keyword-master.md`. **Never
duplicate them in this file.**

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or added keyword.

Any operational rule governing how findings are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `campaign-audit` | Expansion findings suggest a broader structural review of the campaign is warranted (`context/campaign-list.md`) |
| `report-draft` | The review is to be captured in a report under `context/reporting-schedule.md` |
| `scale-check` | Strong expansion opportunity implies scaling spend, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Related sibling skills (not strictly downstream): `search-term-check` (source of
candidate terms and of negation candidates), `bid-check` (a new keyword will need
a bid, gated by `context/bid-rules.md`), `budget-check` (expansion may need
budget headroom). Where the correct downstream skill is ambiguous or the findings
span several, the review records the options under **Recommended Next Skill** and
flags the ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

Never duplicate:

- **Keyword strategy** (categories, match types, discovery sources, lifecycle) —
  reference `context/keyword-strategy.md`.
- **Negative keyword governance** — reference `context/negative-keyword-master.md`.
- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rules it applies,
but it must not restate those rules or values. If a value is needed, link to its
owning document. `context/keyword-strategy.md` is the single source of keyword
strategy.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed search-term/keyword evidence,
  the skill records the gap only; it cannot propose candidates that are not
  evidenced.
- **Cannot infer future performance.** It reviews historical/approved evidence; it
  does not predict outcomes.
- **Cannot create keywords.** It produces DRAFT candidate findings only; any
  addition is applied manually after human approval.
- **Cannot recommend expansion without evidence.** Missing or insufficient
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign resolution cannot be completed. [VERIFY]
- **Exact-match promotion criteria undefined.** `context/keyword-strategy.md`
  implies a "proven" threshold for promoting a keyword to the exact-match library
  but does not define it; promotion findings are limited accordingly. [VERIFY]
- **Search-intent taxonomy / language & marketplace strategy undefined.**
  `context/keyword-strategy.md` marks these `[VERIFY]`; classification is limited
  accordingly. [VERIFY]
- **Unknown approval workflow.** How a review is approved before keywords are
  added is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based review for keyword expansion candidates |
| When should it be used? | Yes | Purpose — after `ppc-brief`, often after `search-term-check` |
| What evidence is required? | Yes | Required Evidence |
| Which Context documents are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/keyword-expand.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or keyword governance duplicated — all referenced to their
  owning `context/` documents
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
