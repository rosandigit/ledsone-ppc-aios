# Hour Budget Check Skill

An evidence-based review skill for LEDSone Amazon PPC. It reviews **intraday
(current-day)** budget-pacing evidence for a campaign and prepares a validated
finding on whether a **DRAFT intraday budget increase** should be recommended —
against the canonical rule in `context/hour-budget-rules.md`. It never owns the
rule, never decides, and never changes anything. **The AIOS never increases a
campaign budget and never schedules a budget change.**

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `hour-budget-check` |
| Purpose | Review intraday budget-pacing evidence against `context/hour-budget-rules.md` (by reference) and prepare a validated DRAFT intraday budget-increase finding for downstream review |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); the canonical decision logic is owned by `context/hour-budget-rules.md` and read by reference. Routes to downstream skills (see **Dependency Matrix**); typically follows `ppc-brief`. It changes nothing. |

---

## Purpose

**Why this skill exists.** A small, efficient campaign can exhaust its daily
budget part-way through the trading day and lose sales it would otherwise win.
Whether a within-day budget increase is warranted is defined only by the canonical
rule in `context/hour-budget-rules.md` (an intraday rule evaluated against
current-day pacing, distinct from the daily budget rules owned by
`context/budget-rules.md`). Judging it requires **current-day (intraday)**
evidence, not multi-day windows. This skill turns that intraday evidence into a
structured, evidence-checked review: whether the canonical rule can be evaluated at
all, whether the evidence satisfies it, and where evidence or a rule parameter is
missing or conflicting.

**When it should be used.** After `ppc-brief` has scoped an intraday
budget-pacing request, and once current-day evidence (the campaign's current daily
budget, today's spend, and current-day efficiency for the marketplace and campaign
in scope) is available. If mandatory evidence is missing, the review records
**Insufficient Evidence** rather than proceeding to a verdict.

**What evidence it reviews.** Amazon Ads **current-day (intraday)** campaign
reporting for the scope in question, plus the campaign identity/type context needed
to apply the canonical marketplace and scope logic (see **Required Evidence**).

**What it deliberately does NOT do.** It does not increase budgets, schedule budget
changes, execute repeated hourly actions, change bids, keywords or negatives, pause
anything, or modify Amazon Ads. It is **not** a general budget-adequacy review —
that is `budget-check`'s responsibility against `context/budget-rules.md`. It does
not infer a missing current-day figure, substitute multi-day (L7D/L30D) evidence
for the required current-day evidence, approximate a marketplace value, or resolve a
`[VERIFY]` parameter. It evaluates verified evidence **against** the canonical rule
and hands a DRAFT finding to a human/downstream skill. Any actual budget change is
drafted, approved by a human, and applied manually in Amazon Ads — never here.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each comes
from the request or from filed evidence. Field **types** only — no runtime values,
and no rule thresholds against which they will be tested.

- **Evaluation timestamp / date** — establishes the current-day / intraday
  evaluation point the canonical rule is applied at; the cadence and windows are
  defined in `context/hour-budget-rules.md`.
- **Marketplace** — selects the applicable canonical parameter set; the values are
  owned by `context/hour-budget-rules.md` (some, e.g. US/CA, are `[VERIFY]` there).
- **Campaign identity + type / scope** — the campaign under review (SP / SB / SD),
  as defined in `context/campaign-list.md` (identity referenced there, not
  redefined here).
- **Current daily budget** — the campaign's current daily budget, required to apply
  the canonical constraint and pacing comparison.
- **Current-day advertising spend (today's spend)** — required for the canonical
  intraday pacing comparison.
- **Current-day ACoS** — the current-day efficiency figure the canonical rule
  conditions test (ACoS is the KPI defined in `context/target-metrics.md`).

Any input a request needs but does not supply, or any input type not listed above,
is **[VERIFY]**; do not assume it.

### Runtime Input Contract

| Field | Purpose | Expected Source | Validation Requirement |
|-------|---------|-----------------|------------------------|
| Evaluation timestamp / date | Fixes the intraday evaluation point per the canonical rule | Request / filed evidence timestamp | Must be present to establish the current-day evaluation point by reference |
| Marketplace | Selects the canonical parameter set | Request / `context/campaign-list.md` | Must map to a marketplace whose values are defined in `context/hour-budget-rules.md`; otherwise `[VERIFY]` |
| Campaign identity + type / scope | Confirms SP/SB/SD applicability and scope | `context/campaign-list.md` | Must be identified; unresolved scope → Insufficient Evidence |
| Current daily budget | Feeds the canonical constraint and pacing comparison | Amazon Ads current-day export → `evidence/` | Must be the current daily budget; never inferred |
| Current-day advertising spend | Feeds the canonical intraday pacing comparison | Amazon Ads current-day (intraday) export → `evidence/` | Must be current-day spend; multi-day spend is **not** a substitute |
| Current-day ACoS | Feeds the canonical efficiency conditions | Amazon Ads current-day (intraday) export → `evidence/` | Must be current-day ACoS; multi-day ACoS is **not** a substitute |

The *which conditions apply and what values they test against* are determined
**only** by `context/hour-budget-rules.md` at evaluation time; this table names
field types, never rule values.

---

## Required Context

Documents this skill consults. It **references** them; it never copies their rules
or values (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/hour-budget-rules.md` | **Authoritative Hour Budget decision logic** — the intraday rule, its conditions, constraint, action, evaluation cadence and marketplace values. Applied by reference only; never restated. |
| `context/target-metrics.md` | **Authoritative metric definition** — the ACoS definition the canonical rule triggers on. Referenced, never redefined. |
| `context/campaign-list.md` | Campaign identity, type (SP/SB/SD) and scope for the campaign in question. |
| `context/reporting-schedule.md` | Evidence-filing and reporting governance for the review output. |

Supporting: `validation/CONTEXT_REVIEW.md` (open `[VERIFY]` items and layer
readiness).

**Adjacent owners (referenced for boundary clarity, not consumed as decision
rules):** `context/budget-rules.md` owns the **Standard** daily budget rules, the
stock gate, approval bands and rollback discipline; a DRAFT intraday increase from
this skill remains subject to the **human-approval and rollback discipline** owned
there, but the Standard daily rules are **not** used to decide an intraday increase
here (that is `budget-check`'s domain). `context/amazon-vendor-bridge.md` is the
product-master owner; it is **not** required for this skill's decision (the Hour
Budget rule operates at campaign level, not on product price/ASIN).

---

## Required Evidence

A review may produce an intraday-increase verdict only when **all** evidence the
canonical rule requires is available. Approved evidence includes:

- **Amazon Ads current-day (intraday) campaign report** — current daily budget,
  today's spend, and current-day efficiency
- **Campaign / scope** context
- **Business request** (documented)

**Manual opinion alone is insufficient.** An increase flagged on opinion, with no
filed current-day evidence behind it, cannot become a validated finding; the review
records the gap under **Evidence Missing** and sets **Insufficient Evidence**. All
evidence must be filed per `README.md` with its source, date and date range.

If any Required Context document is missing at run time, record it here as a missing
source rather than proceeding on assumption. (At authoring, all Required Context
documents exist in the repository; current-day intraday evidence is produced per run
and is not yet filed — that is an evidence gap, not a defect.)

---

## Hour Budget Review Workflow

```
Receive request
   ↓
Validate campaign identity & scope       (resolved and in-scope? — else Insufficient Evidence)
   ↓
Validate marketplace                     (defined in the canonical rule? — else [VERIFY])
   ↓
Determine required evidence fields        (by reference to context/hour-budget-rules.md)
   ↓
Validate current-day evidence completeness (are all required current-day fields present?)
   ↓
If mandatory evidence missing             → Insufficient Evidence (identify what is missing)
   ↓
If an applicable canonical parameter is unresolved  → [VERIFY] (identify the parameter)
   ↓
Evaluate verified evidence against the canonical rule (conditions + constraint, strictly by reference)
   ↓
Check for conflicting evidence            (do verified sources disagree? → Conflict)
   ↓
Prepare structured review                 (complete the Output Template)
   ↓
Recommend downstream skill                (route per the Dependency Matrix)
```

- The skill produces a review and a routing recommendation only. It does not
  execute the downstream skill, does not increase or schedule any budget, and does
  not act on Amazon Ads.
- It reads the conditions, constraint, action and marketplace values from
  `context/hour-budget-rules.md` **by reference** — it does not copy them here.
- A campaign with too little current-day data to evaluate is recorded as
  **Insufficient Evidence**, never as **No Action** and never as an increase
  candidate.
- **"Hourly" is a re-evaluation cadence, not an action.** The skill evaluates the
  current-day evidence available at the evaluation point and drafts a finding; it
  never runs itself on a schedule and never repeats an action hourly.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty review template. All fields are blank; they are filled per request from
filed evidence, never invented. No example budget amounts or percentages appear.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Business Question | *(empty)* |
| Campaign Scope | *(empty)* |
| Marketplace | *(empty)* |
| Evaluation Point | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Source References | *(empty)* |
| Applicable Canonical Rule Reference | *(empty)* |
| Hour Budget Findings | *(empty)* |
| Validation Status | *(empty)* |
| Recommended Action | *(empty)* |
| Reason / Evidence Basis | *(empty)* |
| Outstanding Questions | *(empty)* |
| [VERIFY] Items | *(empty)* |
| Recommended Next Skill | *(empty)* |
| Reviewer | *(empty)* |
| Status | *(empty)* |

> The completed review is evidence-review output, not a budget change and not a
> report. Any `Recommended Action` is a DRAFT for human review — never an applied
> change. The `Applicable Canonical Rule Reference` points to
> `context/hour-budget-rules.md`; it does not restate the rule, and any increase
> value it implies is owned there, not here. Store review output per repository
> convention (not as business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** increase campaign budgets.
- Does **NOT** schedule budget changes or run itself on a schedule.
- Does **NOT** execute repeated hourly budget actions.
- Does **NOT** change bids, keywords or negatives.
- Does **NOT** pause campaigns or products.
- Does **NOT** modify Amazon Ads.
- Does **NOT** own or duplicate Hour Budget rules, and is **NOT** a general
  budget-adequacy review (that is `budget-check`).

**Allowed outcomes.**

- **DRAFT — Increase Daily Budget (intraday):** all evidence the canonical rule
  requires is present and verified, and the rule's conditions and constraint are
  satisfied. The applicable increase and its value are taken from
  `context/hour-budget-rules.md`, cited by reference — never computed here. Requires
  human approval; applied manually.
- **No Action:** the evaluation **was completed** on sufficient current-day evidence
  and no canonical increase recommendation resulted.
- **Insufficient Evidence:** the evaluation **could not be completed** because
  mandatory current-day evidence is missing or unresolved.

**Insufficient Evidence ≠ No Action.** *No Action* means sufficient evidence was
evaluated and no increase resulted. *Insufficient Evidence* means the evaluation
could not be completed. Never report one as the other.

**[VERIFY].** Where evidence exists but the **canonical rule itself** does not
define the required parameter or relationship for the case (e.g. an undefined
marketplace value, or the rule's precedence against the Standard budget rules), set
the affected item to **[VERIFY]** and identify the parameter. Do **not** convert a
`[VERIFY]` into a guessed rule.

**Conflict.** If two **verified** evidence sources disagree on a required runtime
value, do not select the more likely value, average, or reconcile them. Set
**Validation Status = Conflict**, record every conflicting source, and require
**business review**.

**Never guess or substitute.** The skill never guesses missing values, substitutes
multi-day (L7D/L30D) evidence for the required current-day evidence, assumes campaign
values, approximates a marketplace value, or silently resolves conflicting evidence.

**Canonical rule by reference only.** All conditions, constraint, action, values,
cadence and marketplace parameters are read from `context/hour-budget-rules.md`.
**Never duplicate them in this file.** If they change, they change in
`context/hour-budget-rules.md` only.

**Candidates, not decisions.** Every finding is a *candidate* for human review and a
downstream skill; it is never an approved or applied budget change.

Any operational rule governing how findings are prioritised, escalated or approved
beyond the above is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this review may route to. **Only skills that exist in `skills/`
are listed.** This skill *recommends* the next skill; it does not run it. Each
downstream skill applies the rules in its governing `context/` document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `campaign-audit` | The validated Hour Budget finding is to be consolidated with other validated findings into a campaign audit (`context/campaign-list.md`) |
| `report-draft` | The validated finding is to be captured in a report under `context/reporting-schedule.md` |

Upstream, this skill typically follows `ppc-brief` (which scopes the request).
Where the correct downstream skill is ambiguous or the findings span several, the
review records the options under **Recommended Next Skill** and flags the ambiguity
as an **Outstanding Question** rather than guessing.

> **Routing integration status.** As at authoring, `skills/ppc-brief.md` does **not**
> yet route to `hour-budget-check`, and `skills/campaign-audit.md` does **not** yet
> name it in its input list. This skill routes *to* `campaign-audit` and
> `report-draft` by the existing convention, but the reciprocal references have not
> been added to those files (no existing file is modified by this task). Recorded
> under **Known Limitations**.

---

## Duplicate Truth Prevention

**This skill performs evidence review only. Business rules remain inside
`context/`.**

- **`context/hour-budget-rules.md` owns the Hour Budget decision logic** — the
  intraday rule's conditions, constraint, action, cadence and marketplace values.
- **This skill owns** only the **evaluation procedure** and the **structured DRAFT
  review output**. It does **not** own the underlying thresholds, budget values,
  increase amounts, percentages, timing values or marketplace values.
- **`context/budget-rules.md` owns the Standard daily budget rules**, and
  **`skills/budget-check.md` owns the Standard daily budget review** — a **separate**
  rule family and skill. This skill does not consume, restate or absorb them.

Never duplicate:

- **Hour Budget rules / thresholds / budget values / increase amounts / percentages
  / timing / marketplace values** — reference `context/hour-budget-rules.md`.
- **Metric definitions** (ACoS/ROAS/CTR/CVR) — reference `context/target-metrics.md`.
- **Standard budget rules** (minimums, SR-1…SR-4, stock gate, approval, rollback) —
  reference `context/budget-rules.md`.
- **Reporting governance** — reference `context/reporting-schedule.md`.
- **Campaign governance** — reference `context/campaign-list.md`.

The review may *name* the relevant documents and *point to* the rule it applies, but
it must not restate those rules or values. If a value is needed, link to its owning
document. `context/hour-budget-rules.md` is the single source of Hour Budget decision
logic.

---

## Known Limitations

- **Current-day runtime evidence not filed.** The intraday current-day feed (current
  daily budget, today's spend, current-day ACoS) is not yet filed in `evidence/`; the
  repository is not yet capable of supplying it, so affected reviews return
  **Insufficient Evidence**. [VERIFY]
- **Unresolved marketplace parameters.** `context/hour-budget-rules.md` records
  certain marketplace values (e.g. US/CA) as `[VERIFY]` (see
  `validation/REPOSITORY_GAP_REGISTER.md` → GAP-C09 and the owning file's Known
  Limitations); cases depending on them return **[VERIFY]**, not a guessed rule.
- **Rule precedence vs Standard Budget Rules undefined.** How this intraday rule
  ranks against the daily rules owned by `context/budget-rules.md` is not established
  in the source; treated as **[VERIFY]**. [VERIFY]
- **Stock-gate interaction undefined.** Whether an intraday increase should be
  suppressed for stock-constrained products (stock gate owned by
  `context/budget-rules.md`) is not addressed by the source; treated as **[VERIFY]**.
  [VERIFY]
- **Evidence-filing status of the source.** `context/hour-budget-rules.md` records
  that its primary source PDF is not confirmed filed in `evidence/` (see GAP-C09 and
  the owning file); operational use depends on that being resolved. [VERIFY]
- **Routing not yet reciprocated.** `skills/ppc-brief.md` does not yet route to
  `hour-budget-check`, and `skills/campaign-audit.md` does not yet name it; that
  integration has not been made (no existing file modified here). [VERIFY]
- **Cannot infer future pacing.** It reviews current-day/filed evidence; it does not
  predict outcomes.
- **Cannot increase a budget.** It produces DRAFT candidate findings only; any
  increase is applied manually after human approval.
- **Unknown approval workflow.** How a review is approved before an increase is
  drafted is undocumented beyond "human approval required" (the repository's approval
  bands are themselves `[VERIFY]` in `context/budget-rules.md`). [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document and its explicit references.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What business question does this skill answer? | Yes | Header; Purpose — "when should a campaign receive a DRAFT intraday budget-increase recommendation under the Hour Budget Optimisation rule?" |
| Which file owns Hour Budget business rules? | Yes | Required Context; Duplicate Truth Prevention — `context/hour-budget-rules.md` |
| Does the skill own any Hour Budget thresholds or monetary values? | Yes | Duplicate Truth Prevention — **No; owned by `context/hour-budget-rules.md`** |
| What runtime evidence does it require? | Yes | Inputs; Runtime Input Contract; Required Evidence |
| What happens if runtime evidence is missing? | Yes | Decision Rules — Insufficient Evidence |
| Difference between Insufficient Evidence and No Action? | Yes | Decision Rules — "Insufficient Evidence ≠ No Action" |
| What happens if a canonical parameter is undefined? | Yes | Decision Rules — [VERIFY] |
| What happens when verified evidence conflicts? | Yes | Decision Rules — Conflict |
| What DRAFT action can it recommend? | Yes | Decision Rules — DRAFT Increase Daily Budget (intraday) |
| How is it different from `budget-check`? | Yes | Purpose; Duplicate Truth Prevention — intraday Hour Budget vs Standard daily budget review |
| What does "hourly" mean? | Yes | Workflow — a re-evaluation cadence, not an action or automation |
| May the AIOS automatically increase or schedule a budget? | Yes | Header; Decision Rules — **No** |
| Who implements an approved budget change? | Yes | Purpose; Decision Rules — a human, manually in Amazon Ads |
| Where do validated findings go next? | Yes | Dependency Matrix — `campaign-audit`, then `report-draft` |

**Result: PASS**

---

## Final Validation

- ✓ Only `skills/hour-budget-check.md` created
- ✓ Repository structure unchanged; existing skill structure followed
- ✓ No Hour Budget rules, thresholds, budget values, increase amounts, percentages,
  timing or marketplace values duplicated — all referenced to
  `context/hour-budget-rules.md`
- ✓ No values invented; Standard Budget ownership not absorbed
  (`context/budget-rules.md` / `skills/budget-check.md` remain separate)
- ✓ Runtime evidence gating explicit; current-day evidence required, multi-day not
  substituted
- ✓ Missing runtime evidence → Insufficient Evidence; unresolved canonical parameter
  → [VERIFY]; conflicting verified sources → Conflict
- ✓ Insufficient Evidence and No Action kept distinct
- ✓ All outputs remain DRAFT / manual; the AIOS never increases or schedules a budget
- ✓ "Hourly" stated as a re-evaluation cadence, not automation; no automation
  implementation exists
- ✓ Downstream routing described without falsely claiming existing integration
- ✓ Empty output template created (no example figures)
- ✓ Dependency Matrix completed (existing skills only)
- ✓ Duplicate Truth Prevention included
- ✓ Queryability PASS

**Output: PASS**
