# evidence

## Purpose
Source data and exports that recommendations are based on. Evidence-first: no recommendation without a reference here.

## What belongs here
- Exports, screenshots and data extracts, each with the date, source and date range recorded

## What should NOT be stored here
- Conclusions or recommendations (use `reports/` or `decisions/`)
- Edited or re-cut versions of an original export

## Owner
Jathukulan

## Status
Active

## Evidence Filename Convention

Recommended repository naming patterns for material filed in this layer.

**Evidence export:** `YYYY-MM-DD-source-description.ext`

Examples:

- `2026-07-22-amazon-search-term-report.csv`
- `2026-07-22-amazon-campaign-performance.xlsx`
- `2026-07-22-amazon-budget-export.csv`

**Metadata record:** `YYYY-MM-DD-source-description-record.md`

Examples:

- `2026-07-22-amazon-search-term-report-record.md`

These are **repository naming conventions only. They are NOT business rules.**
They exist so evidence sorts chronologically and each export can be matched to its
metadata record; they define no schedule, threshold or operational requirement.

## Metadata Relationship

Every evidence export should have an associated **metadata record** based on
`evidence/TEMPLATE_EVIDENCE_RECORD.md`. The metadata record documents:

- source
- collection date
- evidence date range
- related skills
- related report

The metadata record provides traceability; the **original evidence files remain
unchanged** (consistent with "What should NOT be stored here" above — no edited or
re-cut versions of an original export). The record points to the original via its
`Source File` / `Evidence References` fields; it never replaces or alters it.

## Duplicate Truth Prevention

- Evidence files remain the **original source material**.
- Metadata records provide **traceability only** and are never a source of business
  truth.
- Business rules remain in the **Context layer** (`context/`).
- Recommendations remain in **Reports** (`reports/`).
- Approvals remain in **Decisions** (`decisions/`).

Nothing in this document defines or restates a business rule, KPI, cadence or
threshold; those are referenced to their owning documents.

## Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Evidence lifecycle** — no documented flow from import → reference → archival is
  defined for evidence. [VERIFY]
- **Retention policy** — no approved retention/archival period for evidence is
  documented. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined
  repository-wide. [VERIFY]
- **Outstanding external evidence** — sources cited elsewhere but not yet filed
  here (e.g. `Amazon_BGCT_PayPerClick.pdf` and the "Approved PPC Metrics
  (2026-07-22)" record noted in `context/target-metrics.md` and
  `validation/CONTEXT_REVIEW.md`) remain un-filed. [VERIFY]
