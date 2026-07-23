# reports

## Purpose
Drafted and sent reporting output.

## What belongs here
- Reports filed under `weekly/`, `monthly/` or `sent/`

## What should NOT be stored here
- Raw data (use `evidence/`)
- Approvals (use `decisions/`)

## Owner
Jathukulan

## Status
Active

## Report Filename Convention

Recommended filename patterns for reports filed in this layer:

- **Weekly:** `YYYY-MM-DD-weekly-report.md` (the date is the start of, or a fixed
  reference day within, the reporting week) — filed in `weekly/`.
- **Monthly:** `YYYY-MM-monthly-report.md` — filed in `monthly/`.

These are **repository naming conventions, not business rules**. They exist so
reports sort chronologically and are easy to locate; they define no reporting
schedule and impose no operational requirement. The templates
`weekly/TEMPLATE_WEEKLY_REPORT.md` and `monthly/TEMPLATE_MONTHLY_REPORT.md` are
copied to a new dated file following these patterns; the templates themselves are
never renamed or overwritten.

## Report Lifecycle

Intended flow of a report through this layer:

```
Weekly Draft      (reports/weekly/, from skills/report-draft.md)
   ↓
Monthly Draft     (reports/monthly/, consolidating the period)
   ↓
Business Review   (human review; approvals recorded in decisions/)
   ↓
Sent              (issued to the recipient)
   ↓
Audit Record      (reports/sent/, kept unchanged)
```

`reports/sent/` contains **immutable copies** — the exact version of each report
as sent, with its send date and recipient, kept unchanged as an audit trail (see
`sent/README.md`). Drafts are never edited after they are sent; a sent report is
never modified in place.

## Draft Retention

**[VERIFY] — no approved retention policy currently exists.** No approved rule
defines how long weekly or monthly drafts are retained before archival or
removal. Only `reports/sent/` immutability is documented. Do not assume a
retention period; this remains an open governance item.

## Governance Notes

- **Reporting cadence** remains owned by `context/reporting-schedule.md`. It is
  not defined here and is currently `[VERIFY]` in that document.
- **Approval workflow** — `[VERIFY]`. Beyond "human approval required" (with
  approvals recorded in `decisions/`), the specific reviewer/approver path is
  undocumented.
- **Business rules remain in the Context layer.** This layer references them; it
  never restates KPI targets, bid rules, budget rules, keyword strategy or
  reporting governance.
- **Templates remain presentation assets only.** They record validated outputs
  from `skills/report-draft.md`; they are never a source of business truth.

## Duplicate Truth Prevention

This document governs **repository organisation only** — where reports live, how
they are named, and how they move from draft to audit record.

Operational rules remain in the Context layer. Nothing in this document defines
or restates a business rule, KPI, cadence or approval requirement; those are
referenced to their owning documents (chiefly `context/reporting-schedule.md`).

## Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Reporting cadence** — no approved schedule/timing; owned by
  `context/reporting-schedule.md`. [VERIFY]
- **Approval workflow** — specific reviewer/approver path undocumented beyond
  "human approval required". [VERIFY]
- **Retention duration** — no approved retention/archival period for weekly or
  monthly drafts. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer defined repository-wide.
  [VERIFY]
