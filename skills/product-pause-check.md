# Product Pause Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews
**product/ASIN-level** advertising evidence and prepares a validated finding on
whether a product should be **recommended for pause** — against the canonical
rules in `context/product-pause-rules.md`. It never owns the pause rules, never
decides, and never changes anything. **The AIOS never pauses a product.**

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `product-pause-check` |
| Purpose | Review product/ASIN-level evidence against `context/product-pause-rules.md` (by reference) and prepare a validated DRAFT pause finding for downstream review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); the canonical decision logic is owned by `context/product-pause-rules.md` and read by reference. Routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** A product can keep spending on advertising without
returning enough sales, and whether that warrants a pause is defined only by the
canonical rules in `context/product-pause-rules.md` (three families keyed to a
product's order activity, evaluated against a date-selected data window, with
price-tiered and exception logic). Judging it also requires **product/ASIN-level**
evidence, not campaign-level figures. This skill turns product-level evidence into
a structured, evidence-checked review: whether an applicable canonical rule can be
evaluated at all, whether the evidence satisfies it, and where evidence or a rule
parameter is missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped a product-performance /
pause request, and once product-level evidence (orders, ROAS, clicks and spend for
the windows the canonical rule requires, plus Product Price and ASIN identity) is
available. If mandatory evidence is missing or too thin, the review records
**Insufficient Evidence** rather than proceeding to a verdict.

**What evidence it reviews.** Amazon Ads **product/ASIN-level** performance
reporting for the scope in question, plus the product identity and Product Price
context needed to apply the canonical price-tier and window logic (see **Required
Evidence**).

**What it deliberately does NOT do.** It does not pause products or campaigns,
change bids, budgets, keywords or negatives, create campaigns or product master
data, or modify Amazon Ads. It does not infer a Product Price, invent an ASIN
mapping, substitute campaign-level data for product-level data, approximate a
marketplace rule, or resolve a `[VERIFY]` parameter. It evaluates verified evidence
**against** the canonical rule and hands a DRAFT finding to a human/downstream
skill. Any actual pause is drafted, approved by a human, and applied manually in
Amazon Ads — never here.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence. Field **types** only — no runtime values.

- **Evaluation date** — establishes which data window the canonical rule requires;
  the window itself is defined in `context/product-pause-rules.md`.
- **Marketplace** — selects the applicable canonical parameter set; the values are
  owned by `context/product-pause-rules.md` (some are `[VERIFY]` there).
- **Campaign Type / scope** — SP / SB / SD and campaign/ASIN scope, as defined in
  `context/campaign-list.md` (identity referenced there, not redefined here).
- **Product / ASIN identity** — the product under review. **Note:** product master
  data lives in `context/amazon-vendor-bridge.md`, currently an unpopulated stub;
  until it is populated, ASIN resolution cannot be completed — record as
  **Insufficient Evidence**, do not invent a mapping.
- **Product Price** — required to apply the canonical price-tier logic. Sourced
  from product master data (`context/amazon-vendor-bridge.md`); never inferred.
- **Product-level orders** — for the windows the canonical rule requires.
- **Product-level ROAS** — for the windows the canonical rule requires (ROAS is the
  KPI defined in `context/target-metrics.md`).
- **Product-level clicks** — for the window the canonical rule requires.
- **Product-level spend** — for the window the canonical rule requires.

Any input a request needs but does not supply, or any input type not listed above,
is **[VERIFY]**; do not assume it.

### Runtime Input Contract

| Field | Purpose | Expected Source | Validation Requirement |
|-------|---------|-----------------|------------------------|
| Evaluation date | Selects the canonical data window to evaluate | Request / filed evidence date | Must be present to determine the applicable window by reference |
| Marketplace | Selects the canonical parameter set | Request / `context/campaign-list.md` | Must map to a marketplace whose values are defined in `context/product-pause-rules.md`; otherwise `[VERIFY]` |
| Campaign type / scope | Confirms SP/SB/SD applicability and scope | `context/campaign-list.md` | Must be identified; unresolved scope → Insufficient Evidence |
| Product / ASIN identity | Anchors evaluation to one product | `context/amazon-vendor-bridge.md` | Must be resolved from filed master data; never invented |
| Product Price | Applies the canonical price-tier logic | `context/amazon-vendor-bridge.md` | Must come from filed master data; never inferred or estimated |
| Order counts (required windows) | Feed the canonical order conditions | Amazon Ads product-level export → `evidence/` | Must be present for each window the applicable rule requires |
| ROAS (required windows) | Feed the canonical ROAS conditions | Amazon Ads product-level export → `evidence/` | Must be present for each window the applicable rule requires |
| Clicks (required window) | Feed the canonical click condition | Amazon Ads product-level export → `evidence/` | Must be present where the applicable rule requires it |
| Spend (required window) | Feeds the canonical spend-vs-price condition | Amazon Ads product-level export → `evidence/` | Must be present where the applicable rule requires it |

The *which windows / which conditions apply* are determined **only** by
`context/product-pause-rules.md` at evaluation time; this table names field types,
never rule values.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their rules
or values (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/product-pause-rules.md` | **Authoritative Product Pause decision logic** — the rule families, evaluation windows, conditions, price tiers, exceptions and marketplace values. Applied by reference only; never restated. |
| `context/target-metrics.md` | **Authoritative metric definition** — the ROAS definition the canonical rule triggers on. Referenced, never redefined. |
| `context/amazon-vendor-bridge.md` | **Product identity / Product Price** master data required to resolve the ASIN and its price. Currently an unpopulated stub — see **Known Limitations**. |
| `context/campaign-list.md` | Campaign identity, type (SP/SB/SD) and scope for the product in question. |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output. |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

**Adjacent owners (referenced for boundary clarity, not consumed as decision
rules):** `context/budget-rules.md` owns the stock gate and standard budget rules;
its interaction with a pause finding is `[VERIFY]` (see **Known Limitations**) and
is **not** used to decide a pause here. `context/bid-rules.md` owns bid mechanics
and the bid-action click sample sizes, which are **distinct** from any click
condition in the canonical pause rule and must not be conflated; it is **not**
consulted for this skill's decision.

---

## Required Evidence

A review may produce a pause verdict only when **all** evidence the applicable
canonical rule requires is available. Approved evidence includes:

- **Amazon Ads product/ASIN-level performance report** (orders, ROAS, clicks,
  spend for the required windows)
- **Product identity / Product Price** from filed product master data
- **Campaign / scope** context
- **Business request** (documented)

**Manual opinion alone is insufficient.** A pause flagged on opinion, with no filed
product-level evidence behind it, cannot become a validated finding; the review
records the gap under **Evidence Missing** and sets **Insufficient Evidence**. All
evidence must be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a missing
source rather than proceeding on assumption. (At authoring, all Required Context
documents exist in the repository; `context/amazon-vendor-bridge.md` exists but is
an unpopulated stub.)

---

## Product Pause Review Workflow

```
Receive request
   ↓
Validate product / ASIN identity        (resolved from filed master data? — else Insufficient Evidence)
   ↓
Validate marketplace & campaign scope   (identified and in-scope? — else Insufficient Evidence)
   ↓
Determine required evidence fields       (by reference to context/product-pause-rules.md)
   ↓
Validate evidence completeness           (are all required product-level fields present?)
   ↓
If mandatory evidence missing            → Insufficient Evidence (identify what is missing)
   ↓
If an applicable canonical parameter is unresolved  → [VERIFY] (identify the parameter)
   ↓
Identify applicable rule family & window (strictly by reference to the canonical file)
   ↓
Evaluate verified evidence against the canonical rule (and apply any canonical exception by reference)
   ↓
Check for conflicting evidence           (do verified sources disagree? → Conflict)
   ↓
Prepare structured review                (complete the Output Template)
   ↓
Recommend downstream skill               (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- It reads the rule families, evaluation windows, conditions, price tiers and
  exceptions from `context/product-pause-rules.md` **by reference** — it does not
  copy them here.
- A product with too little data to evaluate is recorded as **Insufficient
  Evidence**, never as **No Action** and never as a pause candidate.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty review template. All fields are blank; they are filled per request from
filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Business Question | *(empty)* |
| Product / ASIN Scope | *(empty)* |
| Marketplace | *(empty)* |
| Campaign Scope | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Source References | *(empty)* |
| Applicable Canonical Rule Reference | *(empty)* |
| Product Pause Findings | *(empty)* |
| Validation Status | *(empty)* |
| Recommended Action | *(empty)* |
| Reason / Evidence Basis | *(empty)* |
| Outstanding Questions | *(empty)* |
| [VERIFY] Items | *(empty)* |
| Recommended Next Skill | *(empty)* |
| Reviewer | *(empty)* |
| Status | *(empty)* |

> The completed review is evidence-review output, not a pause and not a report. Any
> `Recommended Action` is a DRAFT for human review — never an applied change. The
> `Applicable Canonical Rule Reference` points to `context/product-pause-rules.md`;
> it does not restate the rule. Store review output per repository convention (not
> as business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** pause products.
- Does **NOT** pause campaigns.
- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** change keywords or negatives.
- Does **NOT** modify Amazon Ads.
- Does **NOT** own or duplicate Product Pause rules.

**Allowed outcomes.**

- **DRAFT — Pause Product (ASIN):** all evidence the applicable canonical rule
  requires is present and verified, the rule's conditions are satisfied, and no
  canonical exception applies. Cites the applicable rule reference and the evidence
  basis. Requires human approval; applied manually.
- **No Action:** the evaluation **was completed** on sufficient evidence and no
  canonical pause recommendation resulted (including where a canonical exception
  applies).
- **Insufficient Evidence:** the evaluation **could not be completed** because
  mandatory runtime evidence is missing or unresolved.

**Insufficient Evidence ≠ No Action.** *No Action* means sufficient evidence was
evaluated and no pause resulted. *Insufficient Evidence* means the evaluation could
not be completed. Never report one as the other.

**[VERIFY].** Where evidence exists but the **canonical rule itself** does not
define the required parameter or relationship for the case (e.g. an undefined
marketplace parameter, unresolved rule precedence, or stock-gate interaction), set
the affected item to **[VERIFY]** and identify the parameter. Do **not** convert a
`[VERIFY]` into a guessed rule.

**Conflict.** If two **verified** evidence sources disagree on a required runtime
value, do not select the more likely value. Set **Validation Status = Conflict**,
record every conflicting source, and require **business review**.

**Never guess or substitute.** The skill never guesses missing values, infers
Product Price, invents ASIN mappings, substitutes campaign-level evidence for
required product-level evidence, approximates a marketplace rule, or silently
resolves conflicting evidence.

**Canonical rule by reference only.** All rule families, windows, conditions, price
tiers, exceptions and marketplace values are read from
`context/product-pause-rules.md`. **Never duplicate them in this file.** If they
change, they change in `context/product-pause-rules.md` only.

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or applied pause.

Any operational rule governing how findings are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `campaign-audit` | The validated product-pause finding is to be consolidated with other validated findings into a campaign audit (`context/campaign-list.md`) |
| `report-draft` | The validated finding is to be captured in a report under `context/reporting-schedule.md` |

Upstream, this skill typically follows `ppc-brief` (which scopes the request).
Where the correct downstream skill is ambiguous or the findings span several, the
review records the options under **Recommended Next Skill** and flags the ambiguity
as an **Outstanding Question** rather than guessing.

> **Routing integration status.** As at authoring, `skills/ppc-brief.md` and
> `skills/campaign-audit.md` do **not** yet name `product-pause-check` in their own
> Dependency Matrices / input lists. This skill routes *to* `campaign-audit` and
> `report-draft` by the existing convention, but the reciprocal references have not
> been added to those files (no existing file is modified by this task). Recorded
> under **Known Limitations**.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

- **`context/product-pause-rules.md` owns the Product Pause decision logic** — the
  rule families, evaluation windows, conditions, price tiers, exceptions and
  marketplace values.
- **This skill owns** only the **evaluation procedure** and the **structured DRAFT
  review output**. It does **not** own the underlying thresholds, price bands, date
  windows, exceptions or marketplace values.

Never duplicate:

- **Product Pause rules / thresholds / price bands / windows / exceptions /
  marketplace values** — reference `context/product-pause-rules.md`.
- **Metric definitions** (ROAS/ACoS/CTR/CVR) — reference `context/target-metrics.md`.
- **Product master data** (ASIN, Product Price) — reference
  `context/amazon-vendor-bridge.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rule it applies,
but it must not restate those rules or values. If a value is needed, link to its
owning document. `context/product-pause-rules.md` is the single source of Product
Pause decision logic.

---

## Known Limitations

- **Cannot analyse missing product-level reports.** With no filed product/ASIN-level
  evidence, the skill records the gap only; it cannot evaluate a product that is not
  evidenced.
- **Product master data unpopulated.** `context/amazon-vendor-bridge.md` is an
  unpopulated stub (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-C08), so ASIN
  identity and Product Price cannot be resolved; affected reviews return
  **Insufficient Evidence**. [VERIFY]
- **Unresolved marketplace / rule parameters.** `context/product-pause-rules.md`
  records certain marketplace values and rule relationships as `[VERIFY]` (see
  `validation/REPOSITORY_GAP_REGISTER.md` → GAP-C10 and the owning file's Known
  Limitations); cases depending on them return **[VERIFY]**, not a guessed rule.
- **Stock-gate / rule-precedence interaction undefined.** How a pause finding
  interacts with the stock gate and standard rules owned by
  `context/budget-rules.md`, and any precedence between pause rules, is not
  established in the source; treated as **[VERIFY]**. [VERIFY]
- **Downstream routing not yet reciprocated.** `skills/ppc-brief.md` and
  `skills/campaign-audit.md` do not yet reference `product-pause-check`; that
  integration has not been made (no existing file modified here). [VERIFY]
- **Cannot infer future performance.** It reviews historical/filed evidence; it does
  not predict outcomes.
- **Cannot pause a product.** It produces DRAFT candidate findings only; any pause is
  applied manually after human approval.
- **Unknown approval workflow.** How a review is approved before a pause is drafted
  is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document and its explicit references.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What business question does this skill answer? | Yes | Header; Purpose — "when should a product be recommended for pause because of advertising performance?" |
| What evidence does it require? | Yes | Inputs; Runtime Input Contract; Required Evidence |
| Which Context file owns the Product Pause rules? | Yes | Required Context; Duplicate Truth Prevention — `context/product-pause-rules.md` |
| What happens if runtime evidence is missing? | Yes | Decision Rules — Insufficient Evidence |
| What happens if a rule parameter is unresolved? | Yes | Decision Rules — [VERIFY] |
| What happens when evidence conflicts? | Yes | Decision Rules — Conflict |
| What outcomes can it produce? | Yes | Decision Rules — DRAFT Pause / No Action / Insufficient Evidence / [VERIFY] / Conflict |
| Where do validated findings go next? | Yes | Dependency Matrix — `campaign-audit`, then `report-draft` |
| May the AIOS pause a product? | Yes | Header; Decision Rules — **No; DRAFT only, human applies manually** |
| Are the rule thresholds owned by this skill? | Yes | Duplicate Truth Prevention — **No; owned by `context/product-pause-rules.md`** |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/product-pause-check.md` created
- ✓ Repository structure unchanged; existing skill structure followed
- ✓ No Product Pause rules, thresholds, price bands, windows, exceptions or
  marketplace values duplicated — all referenced to `context/product-pause-rules.md`
- ✓ No Product Price or ASIN invented; no marketplace parameter approximated
- ✓ Missing runtime evidence → Insufficient Evidence; unresolved canonical
  parameter → [VERIFY]; conflicting verified sources → Conflict
- ✓ Insufficient Evidence and No Action kept distinct
- ✓ All outputs remain DRAFT / manual; the AIOS never pauses a product
- ✓ Downstream routing described without falsely claiming existing integration
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
