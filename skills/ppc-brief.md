# PPC Brief Skill

The entry-point skill for LEDSone Amazon PPC work. It prepares a structured,
evidence-backed **work brief** before any optimisation, validation, reporting or
recommendation begins. It never analyses performance and never changes anything.

**Safety wording (required of every skill — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Skill Metadata

| Field | Value |
|-------|-------|
| Skill Name | `ppc-brief` |
| Purpose | Prepare an evidence-backed work brief that scopes a PPC request and routes it to the correct downstream skill |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1.0 |
| Dependencies | Consumes `context/` documents (see **Required Context**); routes to downstream skills (see **Dependency Matrix**). It changes nothing. |

---

## Purpose

**Why this skill exists.** PPC work in this repository is evidence-first
(`README.md`, `CLAUDE.md`). Before any bid, budget, keyword or reporting skill
runs, someone must establish *what is being asked*, *what evidence exists*, *what
is missing*, and *which skill should actually do the work*. `ppc-brief` performs
that preparation in one consistent structure, so downstream skills start from a
known, evidence-checked position rather than an ambiguous request.

**When it should be used.** First — at the start of any PPC task, question or
request, before any analysis or recommendation. If a request arrives without a
clear scope or without its supporting evidence identified, run `ppc-brief`.

**What it prepares.** A completed **Output Template**: the business objective,
scope, campaign/marketplace, the evidence available versus missing, the Context
documents that apply, known constraints, outstanding questions, and the
recommended next skill.

**What it deliberately does NOT do.** It does not analyse PPC performance, judge
whether a campaign is on-target, calculate bids or budgets, create keywords or
negatives, or recommend any Amazon Ads action. It prepares information for later
skills; it does not act. Judgement of performance belongs to the downstream
skills, using the rules in `context/`.

---

## Inputs

Inputs that may accompany a request. None is invented by the skill; each is taken
from the request or from filed evidence.

- **Business request** — the plain-language ask.
- **User question** — the specific question to be answered.
- **Business objective** — the goal behind the request (e.g. improve efficiency,
  scale, reduce waste).
- **Campaign name** — as defined in `context/campaign-list.md` (identity is
  referenced there, not redefined here).
- **ASIN / SKU** — product identifiers. **Note:** product master data lives in
  `context/amazon-vendor-bridge.md`, which is currently an unpopulated stub;
  until it is populated, product references cannot be resolved — record as
  **Insufficient Evidence** rather than inventing a mapping.
- **Marketplace** — the Amazon marketplace in scope (repository is GBP/UK-denominated).
- **Date range** — the reporting window the request concerns (source, date and
  date range required per `README.md`).

Any input a request needs but does not supply, or any input type not listed
above, is **[VERIFY]**; do not assume it.

---

## Required Context

Documents this skill consults to scope a brief. It **references** them; it never
copies their contents (see **Duplicate Truth Prevention**).

| Context document | Consulted for |
|------------------|---------------|
| `context/target-metrics.md` | The KPI targets and alert thresholds a request will ultimately be judged against |
| `context/campaign-list.md` | Whether the campaign in scope is defined; the register fields a downstream skill will need |
| `context/keyword-strategy.md` | Keyword classification, discovery and lifecycle relevant to the request |
| `context/negative-keyword-master.md` | Negative-keyword governance relevant to waste/search-term requests |
| `context/reporting-schedule.md` | Reporting governance and (once approved) cadence relevant to reporting requests |
| `context/bid-rules.md` | Bid governance (e.g. sample-size gate) relevant to bid requests |
| `context/budget-rules.md` | Budget governance (e.g. minimums, stock gate) relevant to budget requests |

Supporting: `validation/CONTEXT_REVIEW.md` records the Context layer's open
`[VERIFY]` items and readiness — useful for flagging known constraints in a brief.

---

## Required Evidence

A brief may mark a request "ready to proceed" only when the relevant approved
evidence is available. Approved evidence includes:

- **Amazon Ads reports**
- **Campaign exports**
- **Search Term Reports**
- **Budget reports**
- **Business request** (documented)
- **Approved operational evidence**

**Manual opinion alone is insufficient.** A request with no filed evidence behind
it cannot be marked ready; the brief records the gap under **Evidence Missing**
and sets the decision to **Insufficient Evidence**. All evidence must be filed
per `README.md` with its source, date and date range.

---

## Brief Generation Workflow

```
Receive request
   ↓
Identify scope              (objective, campaign, marketplace, date range)
   ↓
Identify required context   (which context/ documents apply)
   ↓
Identify required evidence  (which approved sources are needed)
   ↓
Check missing information   (evidence gaps, [VERIFY] items, unresolved inputs)
   ↓
Prepare structured brief    (complete the Output Template)
   ↓
Recommend next skill        (route per the Dependency Matrix)
```

- The skill produces a brief and a routing recommendation only. It does not
  execute the recommended next skill and it does not act on Amazon Ads.
- Where required evidence or a required input is missing, the workflow still
  completes a brief — but the brief records **Insufficient Evidence** and lists
  what must be supplied before a downstream skill can proceed.
- No step beyond the above is assumed; any additional workflow is **[VERIFY]**.

---

## Output Template

An empty brief template. All fields are blank; they are filled per request from
the actual request and filed evidence, never invented.

| Field | Value |
|-------|-------|
| Business Objective | *(empty)* |
| Scope | *(empty)* |
| Campaign | *(empty)* |
| Marketplace | *(empty)* |
| Evidence Available | *(empty)* |
| Evidence Missing | *(empty)* |
| Context Documents | *(empty)* |
| Known Constraints | *(empty)* |
| Outstanding Questions | *(empty)* |
| Recommended Next Skill | *(empty)* |

> The completed brief is work-preparation output. It is not a report and not a
> recommendation to act. Store completed briefs per repository convention (not as
> business rules in `context/`).

---

## Decision Rules

This skill:

- Does **NOT** optimise bids.
- Does **NOT** pause campaigns.
- Does **NOT** change budgets.
- Does **NOT** create keywords.
- Does **NOT** create negatives.
- Does **NOT** recommend actions without evidence.

**Insufficient Evidence.** If required evidence is missing, the skill does not
proceed to a recommendation. It states **Insufficient Evidence**, records what is
missing under **Evidence Missing**, and lists the required evidence to obtain.

**Routing, not acting.** The only recommendation this skill makes is *which skill
should run next* (see **Dependency Matrix**). It never recommends an Amazon Ads
change itself.

Any operational rule governing how a brief is prioritised, escalated or approved
is **[VERIFY]** — not defined in this repository.

---

## Dependency Matrix

Downstream skills this brief may route to. **Only skills that exist in `skills/`
are listed** (all present). This skill *recommends* the next skill; it does not
run it. Each downstream skill applies the rules in its governing `context/`
document(s).

| Recommend next skill | When to recommend it |
|----------------------|----------------------|
| `search-term-check` | Request concerns customer search terms — promoting winners or negating waste (`keyword-strategy.md`, `negative-keyword-master.md`) |
| `bid-check` | Request concerns bid levels, once the sample-size gate in `context/bid-rules.md` can be met |
| `acos-check` | Request concerns efficiency vs the ACoS/ROAS targets in `context/target-metrics.md` |
| `budget-check` | Request concerns daily budgets, minimums, overrides or the stock gate (`context/budget-rules.md`) |
| `campaign-audit` | Request is a full campaign review against `context/campaign-list.md` |
| `waste-scan` | Request concerns spend without return / candidates for negation |
| `keyword-expand` | Request concerns discovering and adding new targeting keywords (`keyword-strategy.md`) |
| `report-draft` | Request concerns producing a report under `context/reporting-schedule.md` |
| `scale-check` | Request concerns scaling spend, subject to the stock gate and efficiency targets |

Where the correct downstream skill is ambiguous, or the request spans several,
the brief records the options under **Recommended Next Skill** and flags the
ambiguity as an **Outstanding Question** rather than guessing.

---

## Duplicate Truth Prevention

**This skill prepares work only. Business rules remain inside `context/`.**

- **Never duplicate KPIs** — reference `context/target-metrics.md`.
- **Never duplicate keyword strategy** — reference `context/keyword-strategy.md`
  and `context/negative-keyword-master.md`.
- **Never duplicate reporting rules** — reference `context/reporting-schedule.md`.
- **Never duplicate bid or budget rules** — reference `context/bid-rules.md` and
  `context/budget-rules.md`.
- **Never duplicate campaign records** — reference `context/campaign-list.md`.

The brief may *name* the relevant documents and *point to* the values a
downstream skill will use, but it must not restate those values. If a value is
needed, link to its owning document.

---

## Known Limitations

- **Cannot analyse missing reports.** With no filed report/evidence, the skill
  can only record the gap, not analyse performance.
- **Cannot infer campaign performance.** It does not calculate or judge metrics;
  that is the downstream skills' role.
- **Cannot invent metrics.** KPI values come only from `context/target-metrics.md`.
- **Cannot recommend optimisation without evidence.** Missing evidence →
  **Insufficient Evidence**.
- **Cannot resolve product references yet.** `context/amazon-vendor-bridge.md` is
  unpopulated, so ASIN/SKU-to-campaign mapping cannot be completed. [VERIFY]
- **Unknown approval workflow.** How a brief is reviewed/approved before work
  proceeds is undocumented. [VERIFY]
- **Reviewer role undefined.** No Technical/Queryability Reviewer exists
  repository-wide. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What does this skill do? | Yes | Header; Purpose — prepares an evidence-backed work brief |
| When should it be used? | Yes | Purpose — first, before any analysis |
| What evidence is required? | Yes | Required Evidence |
| What Context documents does it consume? | Yes | Required Context |
| What does it NOT do? | Yes | Purpose; Decision Rules |
| Which skill should run next? | Yes | Dependency Matrix |

**Result: PASS**
