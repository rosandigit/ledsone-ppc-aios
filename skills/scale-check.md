# Scale Check Skill

The **terminal** evidence-based review skill in the LEDSone Amazon PPC Skills
layer. It evaluates whether validated findings and approved Context support
considering a campaign for **scaling**, and prepares an evidence-backed scale
recommendation — candidate, ready, blocked, or conflicting. It never scales, never
decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `scale-check` |
| Purpose | Evaluate whether validated evidence supports considering a campaign for scaling, and prepare a DRAFT scale recommendation for reporting and human review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes validated outputs of upstream skills (esp. `campaign-audit`, `acos-check`, `budget-check`) and `context/` documents (see **Required Context**). **Terminal skill** — no downstream skill in this layer (see **Dependency Matrix**). It changes nothing. |

---

## Purpose

**Why this skill exists.** Scaling spend is only safe when a campaign is efficient
enough *and* the operational conditions (chiefly the stock gate in
`context/budget-rules.md`) allow it. Deciding that requires validated evidence, not
optimism. This skill turns the validated upstream findings into a structured scale
assessment: whether the campaign is a scaling candidate, what evidence supports
readiness, what gaps or conflicts block it, and whether business review is required.

**When it should be used.** Last in the review chain — after the review skills and
`campaign-audit` (and often `report-draft`) have produced validated findings for the
campaign in scope. It is the point at which "is this efficient?" becomes "is this a
candidate to scale?".

**What evidence it reviews.** The **validated outputs of upstream skills** — chiefly
`campaign-audit`, `acos-check` (efficiency vs targets) and `budget-check`
(budget-limited status and the stock gate) — plus the Amazon Ads evidence those
reviews cite (see **Required Evidence**).

**What it deliberately does NOT do.** It does not scale campaigns, change bids,
budgets or keywords, or modify Amazon Ads. It does not decide to scale — it
establishes, on validated evidence, whether scaling *should be considered*, and
hands a DRAFT recommendation to reporting and human review. It applies the stock
gate and efficiency gates **by reference** to `context/budget-rules.md` and
`context/target-metrics.md`; it does not restate their values, and it never
overrides a gate the evidence does not clear.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes from
the request or from validated upstream outputs.

- **Campaign Audit output** — the consolidated `campaign-audit` record (primary
  input).
- **Efficiency findings** — validated `acos-check` output (ACoS/ROAS vs targets).
- **Budget findings** — validated `budget-check` output (budget-limited status; the
  stock-gate assessment).
- **Stock / inventory evidence** — required for the stock gate in
  `context/budget-rules.md`.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated).
- **Date Range** — the reporting window (source, date and date range required per
  `README.md`).
- **Business Request** — the plain-language ask/objective.
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, currently an unpopulated stub; until it is
  populated, ASIN/SKU-to-campaign resolution — and the stock-unit count the stock
  gate needs — cannot be completed. Record as **Insufficient Evidence**, do not
  invent a mapping or a stock figure.

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents and skills this assessment consults. It **references** them; it never
copies their rules or KPIs (see **Duplicate Truth Prevention**).

| Source | Consulted for |
|--------|---------------|
| `context/budget-rules.md` | **Authoritative scaling gate** — the stock gate that governs when a campaign may actively scale, plus minimums, Special Rule overrides and approval thresholds. Applied by reference only; never restated. |
| `context/target-metrics.md` | Efficiency targets (ACoS/ROAS) a scaling candidate must clear; the KPI-vs-rule-trigger distinction |
| `context/bid-rules.md` | Sample-size gate and the early-scaling ACoS signal context (evidence sufficiency) |
| `context/campaign-list.md` | Campaign identity and type |
| `context/keyword-strategy.md`, `context/negative-keyword-master.md` | Keyword-health context where scaling depends on clean targeting |
| `context/reporting-schedule.md` | Reporting governance — the scale assessment is a report/review input |
| `skills/campaign-audit.md` | The primary upstream skill whose consolidated findings gate scaling |
| `skills/acos-check.md`, `skills/budget-check.md` | The efficiency and budget/stock findings central to scale readiness |
| `skills/ppc-brief.md`, `skills/search-term-check.md`, `skills/bid-check.md`, `skills/waste-scan.md`, `skills/keyword-expand.md`, `skills/report-draft.md` | Upstream scoping, review and reporting skills whose validated outputs inform the assessment |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A scale assessment may be produced only from validated upstream findings resting on
approved evidence. Approved evidence includes:

- **Validated `campaign-audit` output**
- **Validated `acos-check` output** (efficiency vs targets)
- **Validated `budget-check` output** (budget-limited status; stock gate)
- **Stock / inventory evidence** (required for the stock gate)
- **Amazon Ads reports** underlying those reviews
- **Business request** (documented)

**Manual opinion alone is insufficient.** A scale judgement not backed by validated
findings and the required stock evidence cannot stand; it is recorded under
**Evidence Missing** and set to **Insufficient Evidence**. All evidence must be filed
per `README.md` with its source, date and date range.

If any Required Context document or upstream output is missing at run time, record it
here as a missing source rather than proceeding on assumption. (At authoring, all
Required Context documents and skills exist; upstream *outputs* and stock evidence
are produced per run and may be absent — that is an evidence gap, not a defect.)

---

## Scale Check Workflow

```
Receive request
   ↓
Validate evidence            (are validated audit/efficiency/budget outputs available?)
   ↓
Confirm efficiency gate       (does validated evidence clear the targets in context/target-metrics.md?)
   ↓
Confirm stock gate            (does stock evidence clear the gate in context/budget-rules.md?)
   ↓
Assess scale readiness        (candidate / blocked, with the blocking reason)
   ↓
Check for conflicting evidence (do dimensions or sources disagree?)
   ↓
Prepare structured assessment (complete the Output Template)
   ↓
Route to reporting / business review (terminal — see Dependency Matrix)
```

- The skill produces a scale assessment and a DRAFT recommendation only. It does not
  scale, does not execute any skill, and does not act on Amazon Ads.
- It reads the stock gate, budget rules and efficiency targets from the relevant
  `context/` documents **by reference** — it does not copy them here.
- If the stock gate is not evidenced/cleared, readiness is **blocked** regardless of
  efficiency; the stock gate is not waived on strong ACoS alone.
- A dimension with no validated finding, or missing stock evidence, is recorded as
  **Insufficient Evidence**, never assumed ready.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty scale-assessment template. All fields are blank; they are filled per request
from validated upstream findings and filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Scale Assessment | *(empty)* |
| Scale Readiness | *(empty)* |
| Blocking Issues | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Next Review | *(empty)* |

> The completed assessment is a DRAFT scale recommendation for human review — not an
> applied change and not authorisation to scale. Any `Recommended Action` (e.g. a
> budget increase) is drafted, approved by a human, and applied manually in Amazon
> Ads by Jathukulan — never here. Store assessment output per repository convention
> (not as business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** scale campaigns.
- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** create keywords.
- Does **NOT** modify Amazon Ads.

**Insufficient Evidence.** If required validated findings or stock evidence are
missing, set **Validation Status = Insufficient Evidence**, record what is missing
under **Evidence Missing**, and set **Scale Readiness = blocked / not assessable**.

**Conflict.** If dimensions or evidence sources disagree (e.g. efficiency supports
scaling but the stock gate or a budget finding does not), do not choose one without
justification. Set **Validation Status = Conflict**, record every conflicting
source/finding, and require **business review**.

**Gates by reference only.** The stock gate, budget rules, approval thresholds and
efficiency targets are read from `context/budget-rules.md` and
`context/target-metrics.md`. **Never duplicate them in this file**, and never waive a
gate the evidence does not clear. `context/budget-rules.md` also requires
Operations Manager approval to add a product below the stock threshold — this skill
never approves; it flags the requirement.

**Candidate, not decision.** A "ready to scale" assessment is a *candidate* for human
review and manual execution; it is never an approved or applied scale-up.

Any operational rule governing how scale assessments are prioritised, escalated or
approved beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

**`scale-check` is the terminal skill in the current Skills layer.** It has **no
downstream skill** within this repository.

| Direction | Detail |
|-----------|--------|
| Upstream inputs | `campaign-audit` (primary), `acos-check`, `budget-check`, and the wider review/scoping skills (`ppc-brief`, `search-term-check`, `bid-check`, `waste-scan`, `keyword-expand`, `report-draft`) |
| Downstream (in this layer) | **None — terminal skill** |
| Onward transition (outside this layer) | Validated scale assessments transition to **reporting** (filed in `reports/` under `context/reporting-schedule.md`), **business review** (human approval; Operations Manager approval where the stock gate requires it), and **operational execution in Amazon Ads** — all performed manually by Jathukulan, outside this repository's Skills layer. This repository never executes the scale-up. |

Because scaling is the point where analysis becomes an operational, money-spending
action, the chain deliberately ends here with a DRAFT recommendation for humans —
consistent with the repository rule that it never changes Amazon Ads. Where onward
handling is ambiguous, the assessment records it under **Recommended Action** /
**Outstanding Questions** rather than guessing.

---

## Duplicate Truth Prevention

**This skill evaluates evidence only. Business rules remain inside `context/`.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Bid rules** — reference `context/bid-rules.md`.
- **Budget rules** (incl. the stock gate and approval thresholds) — reference
  `context/budget-rules.md`.
- **Keyword governance** — reference `context/keyword-strategy.md` and
  `context/negative-keyword-master.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.

The assessment may *name* the relevant documents and *point to* the gates it
applies, but it must not restate those rules or values, nor re-derive the upstream
findings. If a value is needed, link to its owning document.

---

## Known Limitations

- **Cannot scale campaigns.** It produces a DRAFT recommendation only; any scale-up
  is applied manually after human approval.
- **Cannot assess without validated findings.** Missing audit/efficiency/budget
  outputs → **Insufficient Evidence**; readiness is not assumed.
- **Cannot clear the stock gate without stock evidence.** No stock figure is
  invented; without it, readiness is blocked. The stock gate lives in
  `context/budget-rules.md`. [VERIFY at run time — stock evidence]
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU resolution and the stock-unit count cannot be completed.
  [VERIFY]
- **Cannot infer future performance.** It reviews validated historical evidence; it
  does not predict outcomes.
- **Inherits upstream `[VERIFY]` gaps.** Any dimension whose governing document has
  open `[VERIFY]` items (e.g. no ACoS warning/critical thresholds, incomplete budget
  approval bands, no non-UK values) carries those limits into the assessment.
  [VERIFY]
- **Unknown approval workflow.** Beyond "human approval required" (and Operations
  Manager approval where the stock gate requires it), the approval path is
  undocumented. [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based scale-readiness assessment |
| When should it be used? | Yes | Purpose — last, after the review skills and `campaign-audit` |
| What evidence is required? | Yes | Required Evidence |
| Which Context and Skills are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Why is it the final skill? | Yes | Dependency Matrix — terminal; scaling transitions to reporting, business review and manual execution outside the Skills layer |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/scale-check.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or KPI targets duplicated — stock gate, budget rules and
  targets referenced to `context/budget-rules.md` / `context/target-metrics.md`;
  upstream findings consolidated by reference, not re-derived
- ✓ Empty output template created
- ✓ Dependency Matrix completed (terminal skill; onward transition documented)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
