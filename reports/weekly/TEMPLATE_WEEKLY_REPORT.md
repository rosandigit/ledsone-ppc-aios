<!--
Reusable WEEKLY report template — presentation asset only.

How to use: copy this file to a dated report in reports/weekly/ and fill each
section from the validated output of skills/report-draft.md. Do not edit this
template in place. This template records validated outputs only; it is never a
source of business truth. See "About this template" and "Duplicate Truth
Prevention" at the foot of the file.
-->

# Report Metadata

- Report Title:
- Reporting Period:
- Report Date:
- Marketplace:
- Campaign Scope:
- Prepared By:

# Business Objective

# Executive Summary

# Evidence Sources

# Validated Strengths

# Validated Risks

# Evidence Gaps

# Outstanding Questions

# Recommended Follow-up

# Validation Status

# Reviewer

# Approval Status

# Evidence References

# Decision References

---

# About this template

- **What this template is for:** a reusable presentation layout for a weekly PPC
  report draft. It is filed in `reports/weekly/` (one dated document per week).
- **Which skill produces its content:** [`skills/report-draft.md`](../../skills/report-draft.md).
  Every section above is filled from that skill's validated output; this template
  performs no analysis of its own.
- **Where business rules live:** the Context layer. KPI targets
  (`context/target-metrics.md`), bid rules (`context/bid-rules.md`), budget rules
  (`context/budget-rules.md`), keyword strategy (`context/keyword-strategy.md`,
  `context/negative-keyword-master.md`) and reporting governance
  (`context/reporting-schedule.md`) are referenced, never restated here.
- **What evidence is expected:** validated upstream findings resting on approved
  evidence (Amazon Ads reports, campaign exports, etc.), filed in `evidence/` with
  source, date and date range. `Evidence References` links to those sources;
  `Decision References` links to approvals recorded in `decisions/`.
- **What this template does NOT do:** it makes no optimisation, bid, budget,
  keyword or campaign decision, and it changes nothing in Amazon Ads. It records
  validated outputs for human review and approval only.

# Duplicate Truth Prevention

This template records validated outputs only.

Business rules remain in the Context layer.

Operational decisions remain outside this template.

It must never become a source of business truth, and it must not restate KPI
targets, bid rules, budget rules, keyword strategy or reporting governance —
reference the owning `context/` document instead.

# Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Reporting cadence** — no approved weekly schedule/timing exists;
  `context/reporting-schedule.md` marks cadence `[VERIFY]`. [VERIFY]
- **Filename convention** — `reports/weekly/README.md` states "one document per
  week, dated" but no explicit filename format is defined. [VERIFY]
- **Draft retention policy** — no retention/archival period is documented for
  weekly drafts (only `reports/sent/` immutability is defined). [VERIFY]
- **Approval workflow** — beyond "human approval required", the specific
  reviewer/approver path is undocumented. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined
  repository-wide. [VERIFY]

# Queryability Test

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is this template for? | Yes | About this template |
| Which skill produces its content? | Yes | About this template — `skills/report-draft.md` |
| Where do business rules live? | Yes | About this template; Duplicate Truth Prevention — the Context layer |
| What evidence is expected? | Yes | About this template; `Evidence Sources` / `Evidence References` |
| What decisions does this template NOT make? | Yes | About this template — none; presentation only |

**Result: PASS**
