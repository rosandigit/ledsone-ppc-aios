# Budget Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews campaign budget
performance against the rules in `context/budget-rules.md` and prepares validated
findings — budget-limited, unused-budget, needs-investigation, insufficient-evidence,
and conflicting-evidence — for downstream review. It never calculates a budget,
never decides, and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `budget-check` |
| Purpose | Review campaign budget performance against `context/budget-rules.md` (by reference) and prepare validated candidate findings for downstream review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); `context/budget-rules.md` explicitly names `/budget-check` as the consumer of its budget logic. Routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** A campaign can be held back by too little budget, or
waste account budget it does not need, and either is only judgeable against
approved evidence and the rules in `context/budget-rules.md` (minimums, Special
Rule overrides, stock gate, approval thresholds). This skill turns budget
evidence into a structured, evidence-checked review: whether a campaign appears
budget-limited, whether it has unused budget, whether more investigation is
needed, and where evidence is missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped a budget-related request,
and once budget/performance evidence (daily budget, spend, budget-limited
indicators) for the campaign, marketplace and date range is available. If evidence
is missing or too thin, the review records **Insufficient Evidence** rather than
proceeding to a finding.

**What evidence it reviews.** Amazon Ads budget/campaign reporting — daily budget,
spend against budget, budget-limited status, and the order-volume/ACoS context the
Special Rules in `context/budget-rules.md` depend on — for the scope in question
(see **Required Evidence**).

**What it deliberately does NOT do.** It does not change campaign budgets or bids,
does not pause campaigns, and does not modify Amazon Ads. It does not apply the
minimums, Special Rule overrides, stock gate or approval thresholds as actions —
it reads them from `context/budget-rules.md` by reference to frame a finding. Any
actual budget change is drafted, approved by a human, and applied manually — never
here. It also respects the stock gate: scaling implications are flagged for
`scale-check`, not decided here.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence.

- **Campaign Performance Report** — spend and budget-utilisation evidence.
- **Budget Report** — current daily budgets and budget-limited indicators.
- **Campaign** — as defined in `context/campaign-list.md` (identity referenced
  there, not redefined here).
- **Ad Group** — where relevant to the scope.
- **Marketplace** — the Amazon marketplace (repository is GBP/UK-denominated;
  `context/budget-rules.md` records non-UK Spend Pause values as `[VERIFY]`).
- **Date Range** — the reporting window (source, date and date range required per
  `README.md`); the Special Rules use L7D/L30D windows.
- **Business Request** — the plain-language ask/objective.
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, currently an unpopulated stub; until it is
  populated, ASIN/SKU-to-campaign resolution and the stock-gate unit count cannot
  be completed — record as **Insufficient Evidence**, do not invent a mapping.

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their rules
or KPIs (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/budget-rules.md` | **Authoritative budget logic** — daily budget minimums, Special Rule overrides (SR-1 to SR-4), stock gate, approval thresholds, rollback. Applied by reference only; never restated. |
| `context/target-metrics.md` | KPI/efficiency context (ACoS/ROAS) that a budget finding is framed against; note SD has no documented minimum daily budget |
| `context/campaign-list.md` | Campaign identity and type (budget minimums/overrides are type-specific) |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output |
| `skills/ppc-brief.md` | The upstream skill that scopes the request |
| `skills/search-term-check.md` | An upstream skill whose waste findings may prompt a budget review |
| `skills/bid-check.md` | A sibling review skill whose findings may interact with budget |
| `skills/acos-check.md` | A sibling review skill whose efficiency findings may prompt a budget review |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

---

## Required Evidence

A review may produce candidate findings only when the relevant approved evidence
is available. Approved evidence includes:

- **Amazon Ads reports**
- **Campaign export**
- **Budget report / daily budget data**
- **Spend data** (spend against budget; budget-limited indicators)
- **Order-volume and ACoS data** (L7D/L30D, for Special Rule conditions)
- **Business request** (documented)

**Manual opinion alone is insufficient.** A budget claim made on opinion, with no
filed evidence behind it, cannot become a validated finding; the review records
the gap under **Evidence Missing** and sets **Insufficient Evidence**. All evidence
must be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a
missing source rather than proceeding on assumption. (At authoring, all Required
Context documents exist in the repository.)

---

## Budget Review Workflow

```
Receive request
   ↓
Validate evidence            (is approved budget/spend evidence available?)
   ↓
Confirm sufficient data      (enough spend/budget/order data to assess?)
   ↓
Review budget performance    (against the rules in context/budget-rules.md, by reference)
   ↓
Identify candidate findings  (budget-limited / unused budget / needs investigation)
   ↓
Check for conflicting evidence (do sources disagree?)
   ↓
Prepare structured review    (complete the Output Template)
   ↓
Recommend downstream skill   (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill and it does not act on Amazon Ads.
- It reads budget rules from `context/budget-rules.md` **by reference** — it does
  not copy the minimums, override tables, stock gate or approval thresholds here.
- A campaign with too little data to assess is recorded as **Insufficient
  Evidence**, never as budget-limited or over-funded.
- Scaling is not decided here; a strong-efficiency, budget-limited finding is
  routed to `scale-check`, which applies the stock gate in `context/budget-rules.md`.
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
| Budget Findings | *(empty)* |
| Validation Status | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Action | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed review is evidence-review output, not a budget change and not a
> report. Any `Recommended Action` is a DRAFT for human review — never an applied
> change. Store review output per repository convention (not as business rules in
> `context/`).

---

## Decision Rules

This skill:

- Does **NOT** change budgets.
- Does **NOT** change bids.
- Does **NOT** pause campaigns.
- Does **NOT** modify Amazon Ads.
- Does **NOT** duplicate budget rules.

**Insufficient Evidence.** If evidence is missing or too thin to assess budget
performance, set **Validation Status = Insufficient Evidence**, record what is
missing under **Evidence Missing**, and do not produce a budget verdict.

**Conflict.** If evidence sources disagree (e.g. spend/budget figures differ
between sources), do not choose one source without justification. Set **Validation
Status = Conflict**, record every conflicting source, and require **business
review**.

**Budget rules by reference only.** All budget thresholds — minimums, Special Rule
overrides (SR-1 to SR-4), stock gate, approval thresholds, rollback — are read
from `context/budget-rules.md`. **Never duplicate them in this file.** If they
change, they change in `context/budget-rules.md` only.

**Approval thresholds respected.** `context/budget-rules.md` gates who may approve
a budget increase (several bands are `[VERIFY]`). This skill never approves;
`Recommended Action` is a DRAFT for the appropriate human approver.

**Candidates, not decisions.** Every finding is a *candidate* for human review and
a downstream skill; it is never an approved or applied change.

Any operational rule governing how findings are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `waste-scan` | Unused budget or spend-without-return suggests waste to investigate before any budget change |
| `campaign-audit` | Findings suggest a broader structural issue warranting a full campaign review (`context/campaign-list.md`) |
| `report-draft` | The review is to be captured in a report under `context/reporting-schedule.md` |
| `scale-check` | A budget-limited campaign with strong efficiency is a scaling candidate, subject to the stock gate and efficiency gates (`context/budget-rules.md`, `context/target-metrics.md`) |

Where the correct downstream skill is ambiguous or the findings span several, the
review records the options under **Recommended Next Skill** and flags the
ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

Never duplicate:

- **KPI targets** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Budget rules** (minimums, SR-1 to SR-4, stock gate, approval thresholds,
  rollback) — reference `context/budget-rules.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rules it applies,
but it must not restate those rules or values. If a value is needed, link to its
owning document. `context/budget-rules.md` is the single source of every budget
threshold.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed budget/spend evidence, the
  skill records the gap only; it cannot assess a campaign that is not evidenced.
- **Cannot infer future spend.** It reviews historical evidence; it does not
  predict outcomes.
- **Cannot change budgets.** It produces DRAFT candidate findings only; any change
  is applied manually after human approval.
- **Cannot recommend budget changes without evidence.** Missing or insufficient
  evidence → **Insufficient Evidence**.
- **Cannot resolve product references or the stock gate yet.**
  `context/amazon-vendor-bridge.md` is unpopulated, so ASIN/SKU resolution and the
  stock-unit count the stock gate needs cannot be completed. [VERIFY]
- **No Sponsored Display budget minimum.** `context/budget-rules.md` /
  `context/target-metrics.md` record no approved minimum daily budget for SD;
  SD findings are limited accordingly. [VERIFY]
- **Budget approval bands and non-UK values incomplete.**
  `context/budget-rules.md` marks several approval-threshold £ bands and non-UK
  Spend Pause values as `[VERIFY]`. [VERIFY]
- **Unknown approval workflow.** How a review is approved before a budget change
  is drafted is undocumented beyond "human approval required". [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — evidence-based review of campaign budgets |
| When should it be used? | Yes | Purpose — after `ppc-brief`, when budget/spend evidence is available |
| What evidence is required? | Yes | Required Evidence |
| Which Context documents are consumed? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which downstream skills follow? | Yes | Dependency Matrix |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/budget-check.md` changed
- ✓ Repository structure unchanged
- ✓ No business rules or KPI targets duplicated — all referenced to
  `context/budget-rules.md` and `context/target-metrics.md`
- ✓ Empty output template created
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
