# Repository Gap Register

A single repository-wide **navigation index** to gaps that are already documented
elsewhere in this repository. It exists to make documented gaps discoverable from
one place. It owns nothing.

| Field | Value |
|-------|-------|
| Document Type | Repository-wide gap **index** (navigation only) |
| Location | `validation/` — per `validation/README.md`, the home for records of `[VERIFY]` items outstanding |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository |
| Status | Active (living index) |
| Created | 2026-07-24 |
| Authoritative for | Nothing. Each gap is owned by its source file (see **Ownership Rules**). |

---

## Purpose

- This is a **repository-wide navigation index**. Its only job is to help
  coordinators, reviewers and LLMs **locate** documented gaps from one place.
- **Every gap remains owned by its source file.** This register does not define,
  resolve, or restate any gap.
- **No duplicate truth is permitted.** This document **references** documented
  gaps; it never copies the underlying rule, KPI value, architecture, or
  `[VERIFY]` text.
- It exists **only to improve discoverability**. If it disagrees with a source
  file, the **source file wins** — always.

---

## Scope

**Included:** Pointers to gaps that are **already documented** in the repository —
`[VERIFY]` items, `Known Limitations` entries, and unpopulated/deferred stubs —
across the Context, Skills, Evidence, Reports and Handover areas, plus the
repository-wide governance-role gap.

**Excluded:**
- Any gap that is not already documented in an owning file. This register
  **invents no gaps**.
- The gap *definitions*, rules, thresholds, KPI values and architecture
  themselves — those stay in their owning files and are only linked to here.
- Resolution of any gap. Closing a gap happens in its owning file, not here.

**Historical validation reports remain historical records.**
`validation/CONTEXT_REVIEW.md` is a completed, dated (2026-07-23), read-only
review of the Context layer. It is a **review snapshot**, not a living register,
and is **left unchanged**. This register links to it as evidence; it does not
replace, extend, or edit it.

---

## Ownership Rules

- **Business rules remain in `context/`.** KPI targets, bid rules, budget rules,
  keyword strategy and reporting governance are owned there and referenced here.
- **Skill limitations remain in `skills/`.** Each skill's `Known Limitations`
  section owns its own gaps.
- **Layer-organisation gaps remain in their layer README** (`evidence/README.md`,
  `reports/README.md`, `handover/…`).
- **Historical findings remain in validation review documents**
  (`validation/CONTEXT_REVIEW.md`).
- **This register references rather than duplicates them.** It holds pointers,
  never restated content.

**Ownership model**

```
Owning Files                    →   Gap Definition        (context/, skills/, evidence/, reports/, handover/)
Historical Validation Documents →   Review Snapshot       (validation/CONTEXT_REVIEW.md — unchanged)
REPOSITORY_GAP_REGISTER.md      →   Repository Navigation Index   (this file — indexes only)
```

The register indexes gaps only. It does not own any gap definition.

---

## Repository Gap Register

Index of already-documented gaps. **Title** is a neutral topic label, not the
gap's content. **Evidence Reference** and **Notes** are pointers only — no rule,
KPI, architecture or `[VERIFY]` text is copied. `Owner / Reviewer` reflects the
documented repository roles (owner defined; reviewer undefined `[VERIFY]`).
`Priority` is shown only where a source document already ranks it; otherwise
`[VERIFY]`.

| Gap ID | Title | Source File | Evidence Reference | Current Status | Owner / Reviewer | Priority | Last Reviewed | Notes |
|--------|-------|-------------|--------------------|----------------|------------------|----------|---------------|-------|
| GAP-G01 | Reviewer / approver roles undefined (Business Owner, Technical Reviewer, Queryability Reviewer) | Repository-wide; consolidated in `validation/CONTEXT_REVIEW.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → A" | Open `[VERIFY]` | Jathukulan / [VERIFY] | High | 2026-07-23 | Recurs in every `skills/*.md` (`Reviewer: [VERIFY]`) and `handover/TEMPLATE_HANDOVER_NOTE.md`; ranked risk #3 in CONTEXT_REVIEW |
| GAP-C01 | Target-metric thresholds / secondary targets not fully defined | `context/target-metrics.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → C" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | See owning file; consumed by `skills/acos-check.md` |
| GAP-C02 | Campaign register unpopulated; lifecycle/portfolio rules incomplete | `context/campaign-list.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → D" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | Register empty by design pending verified export |
| GAP-C03 | Keyword-strategy items undefined | `context/keyword-strategy.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → E" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | See owning file |
| GAP-C04 | Negative-keyword policy items undefined | `context/negative-keyword-master.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → F" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | See owning file |
| GAP-C05 | Reporting cadence / schedule not approved | `context/reporting-schedule.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → G" | Open `[VERIFY]` | Jathukulan / [VERIFY] | High | 2026-07-23 | Ranked risk #2 in CONTEXT_REVIEW; also referenced by `reports/README.md` |
| GAP-C06 | Bid-rules internal items undefined | `context/bid-rules.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → H" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | Gates `skills/bid-check.md` |
| GAP-C07 | Budget-rules internal items undefined | `context/budget-rules.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → H" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | Gates `skills/budget-check.md` |
| GAP-C08 | Vendor bridge unpopulated (product↔campaign resolution blocked) | `context/amazon-vendor-bridge.md` | Owning file header `Status: [VERIFY]`; CONTEXT_REVIEW → "Outstanding VERIFY Items → I" | Open `[VERIFY]` | Jathukulan / [VERIFY] | High | 2026-07-23 | Ranked risk #4 in CONTEXT_REVIEW; blocks ASIN/SKU use across review skills |
| GAP-S01 | Approval workflow undocumented beyond "human approval required" | `skills/*.md` (all ten) | Each skill → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | Also surfaced for reporting in `reports/README.md` |
| GAP-S02 | No central numeric waste threshold defined | `skills/waste-scan.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | See owning file |
| GAP-S03 | Skill→field dependency mappings largely unconfirmed | `skills/*.md` (Dependency Matrices) | CONTEXT_REVIEW → "Dependency Review" / "Outstanding VERIFY Items → I" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | 2026-07-23 | Resolve per skill as each is built |
| GAP-E01 | Evidence lifecycle (import → reference → archival) undefined | `evidence/README.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | See owning file |
| GAP-E02 | Evidence retention policy undefined | `evidence/README.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | See owning file |
| GAP-E03 | External evidence sources cited but not filed | `evidence/README.md`; also `context/target-metrics.md` | CONTEXT_REVIEW → "Outstanding VERIFY Items → B" | Open `[VERIFY]` | Jathukulan / [VERIFY] | High | 2026-07-23 | Ranked risk #1 in CONTEXT_REVIEW |
| GAP-R01 | Report-draft retention duration undefined | `reports/README.md` | Owning file → "Draft Retention" / "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | Only `reports/sent/` immutability is documented |
| GAP-R02 | Report reviewer/approver path undocumented | `reports/README.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | Related to GAP-S01 |
| GAP-H01 | Handover-note filename convention undefined | `handover/TEMPLATE_HANDOVER_NOTE.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | See owning file |
| GAP-H02 | Handover lifecycle (currency / supersession / archival) undefined | `handover/TEMPLATE_HANDOVER_NOTE.md` | Owning file → "Known Limitations" | Open `[VERIFY]` | Jathukulan / [VERIFY] | [VERIFY] | [VERIFY] | See owning file |

**Notes on the index (not gap content):**
- `Priority` values shown as `High` are taken by reference from
  `validation/CONTEXT_REVIEW.md` → "Largest remaining risks" / "AIOS Readiness
  Score"; they are pointers to that ranking, not a new business judgement. All
  other priorities are `[VERIFY]` because no source document ranks them.
- `Last Reviewed = 2026-07-23` means the gap was last assessed by
  `CONTEXT_REVIEW.md` on that date; `[VERIFY]` means no dated review of that gap
  is recorded in its owning file.
- To update a gap's status, edit its **owning file**, then update this pointer.
  Never resolve a gap here.

---

## Queryability Test

Using only this register (and following its pointers), a reader or LLM can answer:

| Question | Answerable? | Where |
|----------|-------------|-------|
| What gaps exist? | Yes | The **Repository Gap Register** table (Gap ID + Title) |
| Where are they documented? | Yes | `Source File` + `Evidence Reference` columns |
| Who owns them? | Yes | `Owner / Reviewer` column and **Ownership Rules** (each gap owned by its source file) |
| What is their status? | Yes | `Current Status` column |
| Which document is authoritative? | Yes | **Ownership Rules** — the source file owns the gap; `CONTEXT_REVIEW.md` is the historical review snapshot; this register is index-only |

**Result: PASS**

---

## PASS / FAIL Checklist

- ✓ **No duplicate truth** — every cell is a label or pointer; no rule, KPI,
  architecture or `[VERIFY]` text is copied.
- ✓ **Existing files unchanged** — only `validation/REPOSITORY_GAP_REGISTER.md`
  was created; `CONTEXT_REVIEW.md` and all owning files are untouched.
- ✓ **Every gap references an authoritative source** — each row cites its
  `Source File` and `Evidence Reference`.
- ✓ **Register acts only as an index** — it defines and resolves nothing; the
  owning file wins on any conflict.
- ✓ **Repository governance preserved** — no new architecture, no new governance
  roles; undefined roles remain `[VERIFY]`; ownership stays with source files.

**Output: PASS**
