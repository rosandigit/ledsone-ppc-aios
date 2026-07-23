<!--
Reusable DECISION RECORD template — approved decisions only.

How to use: copy this file to a new dated record in decisions/ and fill each
section to log one approved business decision (or rollback). Do not edit this
template in place. This record documents an approved decision for traceability;
it is never a source of business rules. See "About this template" and "Duplicate
Truth Prevention" at the foot of the file.
-->

# Decision Metadata

- Decision Title:
- Decision Date:
- Decision Type:
- Approval Status:
- Approved By:
- Decision Owner:

# Business Objective

# Evidence References

# Related Report

# Decision Outcome

# Rollback Reference

# Notes

---

# About this template

- **This template records approved decisions only.** It documents a decision that
  has already been reviewed and approved by a human — consistent with
  `decisions/README.md` ("Draft recommendations not yet approved" do not belong
  here).
- **Draft recommendations belong in Reports** (`reports/`); a draft is not a
  decision until approved.
- **Evidence belongs in the Evidence layer** (`evidence/`); this record links to it
  via `Evidence References`, it does not hold the evidence itself.
- **Business rules remain in the Context layer** (`context/`). KPI targets, bid
  rules, budget rules, keyword strategy and reporting governance are referenced,
  never restated here.
- **Rollback details follow the existing rule files.** The fields to record for a
  reversal are defined in `context/bid-rules.md` (campaign, keyword, old bid, new
  bid, reverted bid, reason) and `context/budget-rules.md` (the budget equivalent).
  `Rollback Reference` points to that record; the fields are not re-specified here.

Together the sections above let a reader answer: **what decision was approved**
(Decision Metadata / Decision Outcome), **what evidence supports it** (Evidence
References), **which report led to it** (Related Report), **where business rules
live** (Context layer), and **what this template does NOT decide** — nothing; it
records a human decision and changes nothing in Amazon Ads.

# Duplicate Truth Prevention

This template never becomes a source of business rules.

It records approved decisions for traceability only. It must not restate KPI
targets, bid rules, budget rules, keyword strategy or reporting governance —
reference the owning `context/` document instead. Draft analysis lives in
`reports/`, source data in `evidence/`, and the business rules in `context/`.

# Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Filename convention** — `decisions/README.md` requires the date, approver,
  evidence reference and outcome to be recorded, but no explicit filename format
  for decision records is defined. [VERIFY]
- **Approval-status vocabulary** — the allowed values for `Approval Status` (e.g.
  Approved / Rejected / Rolled-back) are not defined in the repository. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined
  repository-wide; approver roles beyond Jathukulan (and MD / Operations Manager
  for the budget thresholds in `context/budget-rules.md`) are not consolidated.
  [VERIFY]
- **Decision lifecycle** — no documented flow from approved → applied → rolled-back
  / archived exists for decision records. [VERIFY]

# Queryability Test

| Question | Answerable? | Where |
|----------|-------------|-------|
| What decision was approved? | Yes | Decision Metadata; Decision Outcome |
| What evidence supports it? | Yes | Evidence References |
| Which report led to it? | Yes | Related Report |
| Where do business rules live? | Yes | About this template; Duplicate Truth Prevention — the Context layer |
| What does this template NOT decide? | Yes | About this template — nothing; it records an approved human decision only |

**Result: PASS**
