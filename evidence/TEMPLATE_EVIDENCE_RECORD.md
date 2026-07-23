<!--
Reusable EVIDENCE RECORD template — metadata only.

How to use: copy this file to a new dated record in evidence/ and fill each
section to describe a piece of filed evidence (an export, screenshot or data
extract). Do not edit this template in place. This record describes evidence; it
is NOT the evidence file itself, and it is never a source of business truth. See
"About this template" and "Duplicate Truth Prevention" at the foot of the file.
-->

# Evidence Metadata

- Evidence Title:
- Evidence Type:
- Source System:
- Source File:
- Collection Date:
- Evidence Date Range:
- Marketplace:
- Campaign:
- Product / ASIN / SKU (if applicable):

# Business Objective

# Related Skills

# Related Report

# Validation Status

# Evidence Available

# Evidence Missing

# Notes

# Evidence References

---

# About this template

- **This template records evidence metadata only.** It is a companion record that
  describes a piece of evidence for traceability; it is **not** an evidence file
  itself.
- **Original evidence files remain unchanged.** Consistent with
  `evidence/README.md`, originals are never edited or re-cut — this record points
  to them via `Source File` / `Evidence References`.
- **What evidence this describes:** the export, screenshot or data extract named in
  the `Evidence Metadata` block, with its `Source System`, `Collection Date` and
  `Evidence Date Range` recorded per the evidence-first policy in `README.md` and
  `CLAUDE.md` (source, date and date range required).
- **Which skill consumes it:** whichever review skill listed under `Related Skills`
  (e.g. `search-term-check`, `bid-check`, `acos-check`, `budget-check`,
  `waste-scan`, `keyword-expand`, `campaign-audit`, `report-draft`, `scale-check`).
  Each of those skills requires filed evidence like this before producing a
  validated finding.
- **Where business rules live:** the Context layer. KPI targets
  (`context/target-metrics.md`), bid rules (`context/bid-rules.md`), budget rules
  (`context/budget-rules.md`), keyword strategy (`context/keyword-strategy.md`,
  `context/negative-keyword-master.md`) and reporting governance
  (`context/reporting-schedule.md`) are referenced, never restated here.
- **What this template does NOT do:** it makes no recommendation, decision or
  optimisation, and it changes nothing in Amazon Ads. **Recommendations belong in
  `reports/`; approvals belong in `decisions/`.**

# Duplicate Truth Prevention

This template never becomes a source of business truth.

It records metadata for traceability only. It must not restate KPI targets, bid
rules, budget rules, keyword strategy or reporting governance — reference the
owning `context/` document instead. Conclusions live in `reports/`, approvals in
`decisions/`, and the original data in the evidence file itself.

# Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Filename convention** — `evidence/README.md` requires the date, source and
  date range to be recorded, but no explicit filename format for evidence files or
  these records is defined. [VERIFY]
- **Evidence lifecycle** — no documented flow from import → reference → retention
  exists for evidence (only original immutability is stated). [VERIFY]
- **Retention policy** — no approved retention/archival period for evidence is
  documented. [VERIFY]
- **External evidence not yet filed** — sources cited elsewhere but not present in
  the repository (e.g. `Amazon_BGCT_PayPerClick.pdf` and the "Approved PPC Metrics
  (2026-07-22)" record noted in `context/target-metrics.md` and
  `validation/CONTEXT_REVIEW.md`) remain un-filed. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined repository-wide.
  [VERIFY]

# Queryability Test

| Question | Answerable? | Where |
|----------|-------------|-------|
| What evidence does this describe? | Yes | Evidence Metadata; About this template |
| Which skill consumes it? | Yes | Related Skills; About this template |
| Where do business rules live? | Yes | About this template; Duplicate Truth Prevention — the Context layer |
| What decisions does this template NOT make? | Yes | About this template — none; metadata only (reports/ for recommendations, decisions/ for approvals) |

**Result: PASS**
