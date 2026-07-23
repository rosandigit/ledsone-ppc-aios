<!--
Reusable HANDOVER NOTE template — continuity information only.

How to use: copy this file to a new dated note in handover/ and fill each section
so another person or LLM can continue the work without verbal explanation. Do not
edit this template in place. This note records continuity only; it never
duplicates Reports, Evidence, Decisions or Validation — it links to them. See
"About this template" and "Duplicate Truth Prevention" at the foot of the file.
-->

# Handover Metadata

- Handover Date:
- Prepared By:
- Current Repository Status:

# Current State Summary

# Work Completed Today

# Work In Progress

# Next Recommended Action

# Blockers / Open Questions

# Related Evidence

# Related Reports

# Related Decisions

# Related Validation

# Notes

---

# About this template

- **This template records continuity only** — what a successor needs to pick the
  work up, consistent with `handover/README.md` ("Material needed for another
  person or another LLM to continue this work without verbal explanation").
- **Do not duplicate content from Reports, Evidence, Decisions or Validation.**
  Link to those assets instead:
  - `Related Evidence` → files/records in `evidence/`
  - `Related Reports` → drafts/records in `reports/`
  - `Related Decisions` → records in `decisions/`
  - `Related Validation` → `validation/` (e.g. `validation/CONTEXT_REVIEW.md` for
    the consolidated open `[VERIFY]` items)
- **Business rules remain in the Context layer** (`context/`). KPI targets, bid
  rules, budget rules, keyword strategy and reporting governance are referenced,
  never restated here.

Together the sections above let a successor answer: **what is the current state**
(Current State Summary; Current Repository Status), **what was completed** (Work
Completed Today), **what is next** (Next Recommended Action), **what is blocking
progress** (Blockers / Open Questions), and **where the supporting assets are**
(the Related Evidence / Reports / Decisions / Validation links).

# Duplicate Truth Prevention

This template exists only to help another person or another LLM continue the work.

It never becomes a source of business truth. It must not restate KPI targets, bid
rules, budget rules, keyword strategy or reporting governance, and it must not copy
report content, evidence data or decision records — it links to them. Each fact
lives in exactly one place; this note points to that place.

# Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Filename convention** — `handover/README.md` requires notes to be "dated" but
  no explicit filename format for handover notes is defined. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined
  repository-wide. [VERIFY]
- **Handover lifecycle** — no documented flow (e.g. how long a handover note is
  current, or when it is superseded/archived) exists. [VERIFY]

# Queryability Test

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is the current state? | Yes | Current State Summary; Handover Metadata (Current Repository Status) |
| What was completed? | Yes | Work Completed Today |
| What is next? | Yes | Next Recommended Action |
| What is blocking progress? | Yes | Blockers / Open Questions |
| Where are the supporting assets? | Yes | Related Evidence / Reports / Decisions / Validation |

**Result: PASS**
