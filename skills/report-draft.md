# Report Draft Skill

A presentation skill for LEDSone Amazon PPC. It converts the **validated findings**
already produced by `campaign-audit` and the upstream review skills into a
structured PPC report **draft**. It performs no new analysis, reinterprets nothing,
and changes nothing — it formats what has already been validated.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `report-draft` |
| Purpose | Convert validated upstream findings into a structured PPC report draft for human review and publication under `context/reporting-schedule.md` |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes validated outputs of upstream skills (esp. `campaign-audit`) and `context/` documents (see **Required Context**); routes to `scale-check` (see **Dependency Matrix**). It changes nothing and analyses nothing new. |

---

## Purpose

**Why this skill exists.** Once findings are validated and consolidated by
`campaign-audit`, they need to be presented in a consistent report structure so a
human can review and, after approval, publish them under
`context/reporting-schedule.md`. This skill performs that final formatting step —
turning validated findings into a report draft — so reports stay consistent month
to month.

**When it should be used.** Last in the review chain: after `campaign-audit` (and
the review skills it consolidates) have produced validated findings for the campaign
in scope. It is the bridge between the Skills layer and the `reports/` area.

**What evidence it reviews.** The **validated outputs of upstream skills** — chiefly
the consolidated `campaign-audit`, and the individual review records it draws on. It
does not open raw Amazon Ads data to form new conclusions; it presents conclusions
already validated upstream.

**What it deliberately does NOT do.** It does not perform new analysis, does not
reinterpret evidence, does not judge performance itself, does not change campaigns,
bids, budgets or keywords, and does not modify Amazon Ads. It does not invent
conclusions, upgrade an "insufficient evidence" finding into a firm one, or add a
strength/risk that no upstream skill validated. If a report section has no validated
finding behind it, the draft records that gap rather than filling it.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes from
the request or from validated upstream outputs.

- **Campaign Audit output** — the consolidated `campaign-audit` record (primary
  input).
- **Upstream review outputs** — `search-term-check`, `bid-check`, `acos-check`,
  `budget-check`, `waste-scan`, `keyword-expand` records the audit draws on.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated).
- **Date Range** — the reporting window (source, date and date range required per
  `README.md`).
- **Business Request** — the plain-language ask/objective and the report audience.
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, currently an unpopulated stub; until it is
  populated, ASIN/SKU-to-campaign resolution cannot be completed — record as
  **Insufficient Evidence**, do not invent a mapping.

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents and skills this draft consults. It **references** them; it never copies
their rules or KPIs (see **Duplicate Truth Prevention**).

| Source | Consulted for |
|--------|---------------|
| `context/reporting-schedule.md` | **Authoritative reporting governance** — report types, lifecycle, validation, evidence requirements, and (once approved) cadence. Applied by reference only; never restated. |
| `context/target-metrics.md` | KPI context for presenting strengths/risks (by reference; the judgement was made upstream) |
| `context/campaign-list.md` | Campaign identity and type for the report header |
| `context/keyword-strategy.md`, `context/negative-keyword-master.md` | Context for presenting keyword/negation findings |
| `context/bid-rules.md`, `context/budget-rules.md` | Context for presenting bid/budget findings |
| `skills/campaign-audit.md` | The primary upstream skill whose consolidated findings this draft presents |
| `skills/ppc-brief.md`, `skills/search-term-check.md`, `skills/bid-check.md`, `skills/acos-check.md`, `skills/budget-check.md`, `skills/waste-scan.md`, `skills/keyword-expand.md` | The scoping and review skills whose validated outputs feed the audit and thus the draft |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A report may be drafted only from validated upstream findings resting on approved
evidence. Approved evidence includes:

- **Validated `campaign-audit` output**
- **Validated upstream review outputs** (each citing its own approved evidence)
- **Amazon Ads reports** underlying those reviews
- **Business request** (documented)

**Manual opinion alone is insufficient.** A report statement not backed by a
validated upstream finding cannot be drafted as a conclusion; it is recorded under
**Evidence Missing** and the section set to **Insufficient Evidence**. All evidence
must be filed per `README.md` with its source, date and date range. Consistent with
`context/reporting-schedule.md`, the report draft itself is filed in `reports/`, not
in `context/`.

If any Required Context document or upstream output is missing at run time, record
it here as a missing source rather than proceeding on assumption. (At authoring, all
Required Context documents and skills exist; upstream *outputs* are produced per run
and may be absent — that is an evidence gap, not a defect.)

---

## Report Draft Workflow

```
Receive request
   ↓
Validate inputs              (is a validated campaign-audit / review set available?)
   ↓
Confirm no new analysis needed (all conclusions already validated upstream?)
   ↓
Assemble report sections     (executive summary, strengths, risks — from validated findings)
   ↓
Carry over gaps & conflicts  (record Evidence Missing / Conflict verbatim from upstream)
   ↓
Prepare structured draft      (complete the Output Template)
   ↓
Recommend downstream skill    (route per the Dependency Matrix)
```

- The skill produces a report draft and a routing recommendation only. It does not
  publish the report, does not execute any skill, and does not act on Amazon Ads.
- It presents upstream conclusions **as validated** — it does not strengthen,
  soften or re-derive them. Gaps and conflicts are carried through unchanged.
- It reads reporting governance and any referenced values from the relevant
  `context/` documents **by reference** — it does not copy them here.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty report-draft template. All fields are blank; they are filled per request
from validated upstream findings, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Executive Summary | *(empty)* |
| Validated Strengths | *(empty)* |
| Validated Risks | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Follow-up | *(empty)* |
| Validation Status | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed draft is a DRAFT report for human review — not a published report
> and not a recommendation to act. It is filed in `reports/` (per
> `context/reporting-schedule.md`), reviewed, and only published after human
> approval. Store draft output per repository convention (not as business rules in
> `context/`).

---

## Decision Rules

This skill:

- Does **NOT** analyse new data.
- Does **NOT** change campaigns.
- Does **NOT** change bids.
- Does **NOT** change budgets.
- Does **NOT** modify Amazon Ads.
- Does **NOT** invent conclusions.

**Insufficient Evidence.** If required validated findings are missing, set
**Validation Status = Insufficient Evidence**, record what is missing under
**Evidence Missing**, and leave the affected report sections empty rather than
filling them.

**Conflict.** If upstream findings or evidence sources conflict, carry the conflict
into the draft: set **Validation Status = Conflict**, record every conflicting
source/finding, and require **business review** before the report is published. Do
not resolve the conflict in the draft.

**Presents, does not re-derive.** The draft reflects the validated upstream
findings exactly. It never upgrades an insufficient/under-review finding to a firm
conclusion, and never adds a finding no upstream skill validated.

**Rules and governance by reference only.** KPI targets, bid rules, budget rules,
keyword governance and reporting governance are read from their owning `context/`
documents. **Never duplicate them in this file.**

Any operational rule governing how a draft is prioritised, approved or published
beyond the above is **[VERIFY]** — not defined in this repository (reporting cadence
and approval are open `[VERIFY]` items in `context/reporting-schedule.md`).

---

## Dependency Matrix

Downstream skill this draft may route to. **Only skills that exist in `skills/` are
listed.** This skill *recommends* the next skill; it does not run it.

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `scale-check` | The report's validated strengths show efficient headroom, making the campaign a scaling candidate, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

`report-draft` is the final presentation step in the review chain; its main output
is a report filed in `reports/` for human review and publication under
`context/reporting-schedule.md`. Where onward routing is ambiguous, the draft
records the options under **Recommended Next Skill** and flags the ambiguity as an
**Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill drafts reports only. Business rules remain in `context/`. Findings come
from validated upstream skills.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Bid rules** — reference `context/bid-rules.md`.
- **Budget rules** — reference `context/budget-rules.md`.
- **Keyword governance** — reference `context/keyword-strategy.md` and
  `context/negative-keyword-master.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.

The draft may *name* the relevant documents and *present* the validated findings,
but it must not restate the underlying rules or values, nor re-derive the findings.
If a value is needed, link to its owning document. Report rows and data live in
`reports/`, not in this file or `context/`.

---

## Known Limitations

- **Cannot perform analysis.** It presents validated findings only; if a needed
  finding was never produced, the draft records the gap.
- **Cannot analyse missing reports.** With no validated upstream output, the draft
  records the gap only.
- **Cannot invent conclusions.** Every strength, risk and follow-up must trace to a
  validated upstream finding.
- **Cannot modify campaigns.** It produces a DRAFT report only; publication and any
  action follow human approval.
- **Cannot recommend action without evidence.** Missing or insufficient validated
  findings → **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign resolution cannot be completed. [VERIFY]
- **No approved reporting cadence or templates.** `context/reporting-schedule.md`
  records report cadence, templates and calendar as `[VERIFY]`; the draft's timing
  and format are limited accordingly. [VERIFY]
- **Inherits upstream `[VERIFY]` gaps.** Any dimension whose governing document has
  open `[VERIFY]` items carries those limits into the report. [VERIFY]
- **Unknown approval/publication workflow.** How a draft is approved and published
  is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — drafts a report from validated findings, no new analysis |
| When should it be used? | Yes | Purpose — last, after `campaign-audit` |
| What evidence is required? | Yes | Required Evidence |
| Which Context and Skills are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skill follows? | Yes | Dependency Matrix — `scale-check` |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/report-draft.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or KPI targets duplicated — all referenced to their owning
  `context/` documents; findings presented from validated upstream skills, not
  re-derived
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
