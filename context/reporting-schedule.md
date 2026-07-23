# Reporting Schedule

Canonical **reporting governance specification** for LEDSone Amazon PPC.

This document defines *reporting cadence, ownership, evidence requirements,
validation, lifecycle, approval, AI-skill consumption and governance rules*. It
is **not** a report, it contains **no** campaign performance, and it holds no
report rows. Actual reports are stored separately in `reports/` (organised
`weekly/`, `monthly/`, `sent/`). No reporting record may be added here until
verified evidence and an approved schedule exist.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — recorded as `Owner` in `README.md`, `CLAUDE.md`, `reports/README.md`, `context/bid-rules.md` and `context/budget-rules.md` |
| Business Owner | [VERIFY] — no governance section exists in `README.md` or `CLAUDE.md`. "MD" appears in `context/budget-rules.md` as a budget **approver**, but is nowhere defined as Business Owner. Do not assume the two are the same role. |
| Technical Reviewer | [VERIFY] — no technical reviewer role is defined anywhere in this repository |
| Queryability Reviewer | [VERIFY] — no queryability reviewer role is defined anywhere in this repository |
| Status | Active — governance specification approved; the reporting register is empty and exact schedules remain `[VERIFY]` pending approved cadence |
| Version | 1.0 |
| Last Updated | 2026-07-23 |
| Source Documents | See the **Evidence** section below |

---

## Purpose

This document exists so that every person and every AI skill in this repository
governs reporting the **same** way, from one canonical definition.

**Why reporting exists.** Reporting turns raw Amazon Ads evidence into a
reviewed, dated statement of what happened, so performance can be judged against
the targets in `context/target-metrics.md` (referenced, not restated).

**Why reporting supports decision making.** Bid, budget, keyword and scaling
decisions are only as good as the evidence behind them. Reporting is the
structured, validated bridge between operational evidence and the DRAFT
recommendations this repository produces.

**How reporting validates PPC optimisation.** A report records the state before
and after action, so the effect of an optimisation can be checked and, if it
underperforms, rolled back and logged in `decisions/` (consistent with the
rollback discipline in `context/bid-rules.md` and `context/budget-rules.md`).

**This document defines reporting governance, NOT actual reports.** No report
data, schedule, KPI value or ownership assignment is asserted here beyond what
repository evidence supports. Actual reports live in `reports/`.

---

## Evidence

Every statement in this document originates from one of the sources below.
Physical existence inside this repository was checked on 2026-07-23 by listing
the repository contents.

| Source | Location | Exists in this repository? | Used for |
|--------|----------|---------------------------|----------|
| `README.md` | repository root | **Exists — verified in-repo document** | Repository purpose; "weekly and monthly report drafts, plus a record of what was sent"; evidence-first and human-approval policy; the `skills/` list |
| `CLAUDE.md` | repository root | **Exists — verified in-repo document** | Governance: Existing Asset First, Evidence First, Queryability First, No Duplicate Truth, Human Approval Required, Never Modify Amazon Ads |
| `reports/README.md` | `reports/README.md` | **Exists — verified in-repo document** | The `reports/` structure (`weekly/`, `monthly/`, `sent/`); raw data belongs in `evidence/`, approvals in `decisions/`; Owner Jathukulan |
| `context/target-metrics.md` | `context/target-metrics.md` | **Exists — verified in-repo document** | KPI targets reports are judged against; it defers every metric's "Review Frequency" to **this** document, confirming no approved cadence exists yet |
| `context/campaign-list.md` | `context/campaign-list.md` | **Exists — verified in-repo document** | Canonical campaign register (linked, never restated) |
| `context/keyword-strategy.md` | `context/keyword-strategy.md` | **Exists — verified in-repo document** | Canonical keyword strategy (linked, never restated) |
| `context/negative-keyword-master.md` | `context/negative-keyword-master.md` | **Exists — verified in-repo document** | Negative-keyword governance (linked, never restated) |
| `context/bid-rules.md` | `context/bid-rules.md` | **Exists — verified in-repo document** | Rollback logging in `decisions/`; bid logic reports may reference |
| `context/budget-rules.md` | `context/budget-rules.md` | **Exists — verified in-repo document** | Rollback logging in `decisions/`; budget logic reports may reference |
| existing `context/reporting-schedule.md` | `context/reporting-schedule.md` | **Exists — this file.** Prior content was a placeholder stub (`Status: [VERIFY] — not yet documented`), now replaced by this specification. | The document being completed |

**No external source is cited by this document.** Every source above is a
verified in-repository markdown file.

---

## Scope

This governance specification is the shared reporting reference for the following
areas. It defines their governance; it does not produce any report.

| Area | How this document governs it |
|------|------------------------------|
| Daily Reporting | Defines governance for any daily operational report — cadence remains `[VERIFY]` (no repository evidence for a daily schedule) |
| Weekly Reporting | Governs weekly report drafts filed in `reports/weekly/` (folder evidenced); exact timing `[VERIFY]` |
| Monthly Reporting | Governs monthly report drafts filed in `reports/monthly/` (folder evidenced); exact timing `[VERIFY]` |
| Campaign Review | Governs reports that audit campaigns defined in `context/campaign-list.md` |
| Budget Review | Governs reports on budget performance against `context/budget-rules.md` |
| Bid Review | Governs reports on bid performance against `context/bid-rules.md` |
| Keyword Review | Governs reports on keyword/search-term activity per `context/keyword-strategy.md` and `context/negative-keyword-master.md` |
| Executive Reporting | Governs any executive summary — process and audience `[VERIFY]` |
| AI Skills | Every reporting-related skill in `skills/` reads this specification — see the **Dependency Matrix** |

**Out of scope.** This document does not contain report data, KPI values,
campaign records, keyword lists or a reporting calendar with approved timings.
Those live in their authoritative files (or do not yet exist) and are linked,
never restated or invented.

**Safety.** Any output derived from this document that touches bids, budgets,
keywords, campaigns or targeting: **outputs DRAFT recommendations only, never
applies Amazon Ads changes, human approval required** before implementation.
Jathukulan reviews and applies every change manually. If automation of Amazon
Ads is implied, **STOP** and flag it.

---

## Reporting Types

Report types the governance covers. Only types supported by repository evidence
are asserted as existing today; the rest are governed here but marked where no
repository evidence yet confirms an active process.

| Report type | Description | Repository evidence |
|-------------|-------------|---------------------|
| Daily operational reports | Short-cycle operational status. | [VERIFY] — no daily report folder or reference exists |
| Weekly optimisation reports | Weekly review of performance and optimisation actions. | Evidenced — `reports/weekly/` and README reference to "weekly … report drafts" |
| Monthly performance reports | Monthly performance summary. | Evidenced — `reports/monthly/` and README reference to "monthly report drafts" |
| Executive summary reports | High-level summary for leadership. | [VERIFY] — no executive reporting process is documented |
| Campaign audit reports | Output of a campaign audit. | Partially — `campaign-audit` skill exists as a stub; report format `[VERIFY]` |
| Exception reports | Reports triggered by a threshold breach (e.g. CTR/CVR alert ladders in `context/target-metrics.md`). | Partially — thresholds exist in `target-metrics.md`; a defined exception-report process is `[VERIFY]` |

Any report type a downstream process needs but that is not listed above is
**[VERIFY]**; do not invent one.

---

## Reporting Cadence

Reporting frequencies. **No exact schedule (day, time, cut-off) is approved
anywhere in this repository** — `context/target-metrics.md` explicitly defers
every metric's review frequency to this document, and no approved timing has been
supplied. Frequencies are therefore recorded as `[VERIFY]`. The existence of
`reports/weekly/` and `reports/monthly/` evidences the *cadence categories*
weekly and monthly, but not their precise timing.

| Frequency | Status |
|-----------|--------|
| Daily | **Daily [VERIFY]** — no repository evidence for a daily reporting schedule |
| Weekly | **Weekly [VERIFY]** — category evidenced by `reports/weekly/`; exact day/time/cut-off undocumented |
| Monthly | **Monthly [VERIFY]** — category evidenced by `reports/monthly/`; exact date/cut-off undocumented |
| Quarterly | **Quarterly [VERIFY]** — no repository evidence for a quarterly reporting schedule |

Do **not** invent timing. Exact schedules must be added only from an approved
source.

---

## Evidence Sources

A report may be generated **only** from approved evidence. Approved evidence
includes:

- **Amazon Ads Reports**
- **Campaign Reports**
- **Search Term Reports**
- **Budget Reports**
- **Bid Reports**
- **Approved operational exports**

**Manual commentary alone is not sufficient evidence.** Narrative written without
one of the sources above behind it does not meet the evidence-first policy
(`README.md`, `CLAUDE.md`) and must not be published as a validated report.

Consistent with `reports/README.md`, raw data belongs in `evidence/` (with
source, date and date range), not inside the report or this document.

---

## Report Lifecycle

The stages a report moves through, from request to archival. Stages are governed
here; specific transition rules and approvers are `[VERIFY]` where no repository
document defines them.

```
Requested     A report is asked for (scheduled or ad hoc)
   ↓
Generated     Drafted from approved evidence (e.g. via report-draft)
   ↓
Validated     Checked against its evidence (see Validation Rules)
   ↓
Reviewed      Human review of content and conclusions
   ↓
Approved      Signed off for publication (human approval)
   ↓
Published     Issued; a record of what was sent kept in reports/sent/
   ↓
Archived      Retained for reference
```

- **Human approval.** Movement to **Approved** and **Published** requires human
  approval; approvals are recorded in `decisions/` per `reports/README.md`.
- **Draft-only.** Every generated report is a DRAFT until reviewed and approved;
  a draft is not authorisation to act (`README.md`).
- **Transition rules.** The precise conditions and approver for each transition
  are **[VERIFY]** — not defined in this repository. Any lifecycle stage a
  downstream process needs but that is not listed above is **[VERIFY]**; do not
  invent one.

---

## Reporting Register

The canonical register structure. It is **empty by design**. No row below the
header is populated, and none may be added except from verified evidence and an
approved schedule.

| Report Name | Report Type | Frequency | Evidence Source | Owner | Reviewer | Status | Approval | Generated Date | Last Reviewed | Validation Status |
|-------------|-------------|-----------|-----------------|-------|----------|--------|----------|----------------|---------------|-------------------|
| *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* |

> **Operational reports shall only be generated from verified evidence.** No
> report name, schedule, KPI, owner or performance value has been entered,
> because no approved schedule and no verified evidence have been imported. The
> single placeholder row above shows the columns only and is not a record. Actual
> reports are stored in `reports/`, not here.

---

## Validation Rules

Every report must include all of the following before it is treated as valid:

- **Evidence** — an approved source from **Evidence Sources**;
- **Generation date** — when the report was drafted;
- **Reviewer** — the human who reviewed it;
- **Approval** — the approval record (kept in `decisions/`);
- **Validation status** — the outcome of validation.

**Conflict handling.** If evidence sources conflict (they disagree on a figure,
classification or conclusion), do **not** choose one source without
justification. Instead:

- set **Validation Status = Conflict**;
- record **every** conflicting evidence source;
- **require business review before publication**.

The full set of allowed Validation Status values (beyond `Conflict`), and any
further validation rules, are not established by repository evidence: **[VERIFY]**.

---

## Relationship Matrix

The logical chain a report sits within. This describes the conceptual
relationship only; no implementation detail is invented.

```
Campaigns
   ↓
Keywords
   ↓
Performance Metrics
   ↓
Reports
   ↓
Business Decisions
```

- **Campaigns → Keywords** — campaigns (defined in `context/campaign-list.md`)
  contain the keywords (governed by `context/keyword-strategy.md`) that generate
  activity.
- **Keywords → Performance Metrics** — keyword/campaign activity produces the
  metrics defined in `context/target-metrics.md`.
- **Performance Metrics → Reports** — reports aggregate and present those metrics
  against their targets.
- **Reports → Business Decisions** — reviewed, approved reports inform DRAFT
  recommendations and the manual decisions logged in `decisions/`.

Cardinality, aggregation rules and any marketplace-specific variations of this
chain are not documented in this repository: **[VERIFY]**.

---

## Dependency Matrix

Which register fields / reporting activities are consumed or produced by which
skills. **Only skills that exist in `skills/` are listed.** Every skill file is
currently an early-stage stub, and none yet declares its reporting inputs or
outputs. Dependencies are recorded as confirmed **only** where a skill's own name
states its function; everything else is `[VERIFY]` and must be filled in as each
skill is defined — not guessed.

| Reporting element | Used By |
|-------------------|---------|
| Report generation (drafting) | `report-draft` (named for the function); precise inputs [VERIFY] |
| Campaign audit reports | `campaign-audit` (named for the function); report format [VERIFY] |
| Budget review inputs | `budget-check` (consumes `context/budget-rules.md`); reporting dependence [VERIFY] |
| Bid review inputs | `bid-check` (consumes `context/bid-rules.md`); reporting dependence [VERIFY] |
| Search-term review inputs | `search-term-check`; reporting dependence [VERIFY] |
| Waste review inputs | `waste-scan`; reporting dependence [VERIFY] |
| ACoS/efficiency inputs | `acos-check` (consumes `context/target-metrics.md`); reporting dependence [VERIFY] |
| Scaling review inputs | `scale-check`; reporting dependence [VERIFY] |
| Report Name / Frequency / Owner / Reviewer / Status / Approval / dates / Validation Status | [VERIFY] — no skill declares consumption of these register fields yet |

Skill present in `skills/` with **no** clear reporting dependency: `ppc-brief`
(a briefing function; reporting role [VERIFY]). Each `[VERIFY]` entry should be
completed as that skill is defined, not before. No dependency has been invented.

---

## Duplicate Truth Prevention

**This document defines the reporting governance.**

Do **not** duplicate the following inside this document — reference the
authoritative source instead:

| Do not duplicate | Reference instead |
|------------------|-------------------|
| Campaign definitions | `context/campaign-list.md` |
| Keyword strategy | `context/keyword-strategy.md` |
| Negative keyword governance | `context/negative-keyword-master.md` |
| Target metrics (ACoS / ROAS / CTR / CVR) | `context/target-metrics.md` |
| Operational reports | `reports/` (`weekly/`, `monthly/`, `sent/`) |

Additional rules:

- Report **content and data** must not be duplicated here or across markdown
  files; reports live in `reports/`, raw data in `evidence/`, approvals in
  `decisions/` (per `reports/README.md`).
- Bid and budget mechanics are owned by `context/bid-rules.md` and
  `context/budget-rules.md` and are linked, never restated.
- This document owns the **reporting governance** only. It does not redefine any
  campaign, keyword, negative-keyword or metric fact.

---

## Known Limitations

Genuine unresolved items. Each blocks a specific downstream use. None is worked
around by inventing data.

1. **No report schedule approved.** No exact daily/weekly/monthly/quarterly
   timing exists; `context/target-metrics.md` defers review frequency to this
   document, which has no approved cadence to give. [VERIFY]
2. **No report templates imported.** No report format/template has been filed.
3. **No reporting calendar.** No calendar of due dates/cut-offs exists.
4. **No report ownership defined.** Beyond repository Owner Jathukulan, per-report
   Owner and Reviewer are undefined. [VERIFY]
5. **No executive reporting process.** Executive summary audience, cadence and
   format are undocumented. [VERIFY]
6. **Marketplace reporting.** The repository is GBP/UK-denominated; whether
   reporting differs by marketplace is undocumented. [VERIFY]
7. **Automation workflow.** How reports are generated/scheduled (beyond
   `report-draft` existing as a stub) is undocumented — and this repository never
   automates Amazon Ads regardless. [VERIFY]
8. **KPI distribution rules.** Who receives which report, and through what
   channel, is undocumented. [VERIFY]
9. **Exception-report triggers.** CTR/CVR alert thresholds exist in
   `context/target-metrics.md`, but a defined exception-report process is
   undocumented. [VERIFY]
10. **Governance roles undefined.** Business Owner, Technical Reviewer and
    Queryability Reviewer are undefined repository-wide. Until defined, this
    document has an owner but no approver. [VERIFY]
11. **Validation Status vocabulary.** Only `Conflict` is defined by this
    document; the full set of allowed statuses is undocumented. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is this document? | Yes | Header; Purpose — a reporting *governance* specification, not a report |
| Why does it exist? | Yes | Purpose |
| What reports are governed? | Yes | Scope; Reporting Types |
| What evidence is required? | Yes | Evidence Sources |
| How are reports validated? | Yes | Validation Rules, including Conflict handling |
| How are reports approved? | Yes | Report Lifecycle; Validation Rules |
| How should AI skills consume this document? | Yes | Purpose; Scope; Dependency Matrix |
| What remains unknown? | Yes | Every `[VERIFY]` marker, consolidated in Known Limitations |

**Result: PASS**
