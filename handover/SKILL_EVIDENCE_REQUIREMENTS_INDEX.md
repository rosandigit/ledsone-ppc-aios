# Skill → Evidence Requirements Index

A cross-skill **routing index**: for each PPC AIOS skill, which evidence or report
source it requires, and where that requirement is authoritatively documented.

**This index owns nothing.** Every requirement remains owned by its skill file in
`skills/`. If this index and a skill file ever disagree, **the skill file wins.**

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Type | Cross-skill routing / queryability index (navigation only) |
| Location | `handover/` — per `handover/README.md`, material another person or LLM needs to continue this work without verbal explanation. That README also directs that content duplicated from elsewhere be **linked to, not copied**, which is the discipline this index follows. |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Status | Active |
| Created | 2026-07-30 |
| Built from repository HEAD | `8aa58828819146a1b1e6957d5f1444f7a7a10e23` |
| Authoritative for | Nothing. Each evidence requirement is owned by its skill file (see **Ownership Boundary**). |

---

## Purpose

**What this index is.** A single table listing every skill in `skills/` alongside a
**neutral label** for the evidence or report source that skill requires, and a
pointer to the authoritative `## Required Evidence` section that defines it.

**Why it exists.** The requirement is already documented — every skill file carries
its own `Required Evidence` section — but it is distributed across twelve separate
files. No single document lets a reader see the full set at once, so the question
below could not previously be answered without opening all twelve.

**The operational question it answers:**

> Which existing evidence or report source does each PPC AIOS skill require, and
> where is the authoritative requirement documented?

**What kind of asset this is.** A **routing and queryability asset**. It helps a
reader or an LLM navigate to the right owning document. It is not a specification,
not a rule, not a data schema, and not an instruction to acquire anything.

**The skills remain authoritative.** This index restates no evidence rule, no
threshold, no decision criterion and no required-field specification. For any
detail beyond "which source, documented where", read the owning skill file.

---

## Source and Evidence

This index was derived **entirely from files already committed to this
repository** — specifically the `## Required Evidence` section of each skill file
under `skills/`, read at repository HEAD
`8aa58828819146a1b1e6957d5f1444f7a7a10e23`.

No external source was consulted. No Amazon Ads export was read, requested or
filed. No fact outside repository evidence is introduced.

**This index does not claim that any Amazon runtime evidence has been filed.** At
the HEAD above, the `evidence/` layer holds its README and metadata-record template
only. The evidence position is recorded factually in
`handover/PPC_AIOS_CURRENT_ARCHITECTURE.md`; this index neither restates nor
changes it. Listing a required source here is a statement about **what a skill
documents that it needs** — never a statement that the source exists, has been
exported, or has been filed.

---

## Ownership Boundary

- **`skills/*.md` own skill-specific evidence requirements.** Each skill's
  `## Required Evidence` section is the sole authority for what that skill
  requires, in what form, and under what conditions a review may proceed.
- **This file owns only the cross-skill routing index** — the mapping from skill
  to owning section. It defines no requirement and resolves no question.
- **`evidence/` owns evidence governance and records** according to
  `evidence/README.md` — filing conventions, the metadata-record relationship,
  retention governance and that layer's Known Limitations.
- **`validation/` owns validation and gap tracking** — `validation/CONTEXT_REVIEW.md`
  and `validation/REPOSITORY_GAP_REGISTER.md`.
- **This file must not be used as a substitute for the owning skill.** A neutral
  label here is sufficient to route a reader; it is **not** sufficient to run a
  review, scope an export, or judge whether evidence is adequate. Read the owning
  skill before acting on anything.

---

## Skill → Evidence Index

One row per skill file discovered under `skills/`. **Neutral evidence/report
label** is a routing label only — a conservative, source-level summary taken from
the owning section, with metric fields, conditions and evaluation criteria
deliberately omitted. **Authoritative requirement** is the pointer that governs.

| Skill | Neutral evidence/report label | Authoritative requirement |
|-------|-------------------------------|---------------------------|
| `ppc-brief` | Amazon Ads reports (campaign exports, Search Term Reports, budget reports); documented business request; approved operational evidence | `skills/ppc-brief.md` → Required Evidence |
| `search-term-check` | Amazon Search Term Report; Amazon Ads campaign export; documented business request; approved operational evidence | `skills/search-term-check.md` → Required Evidence |
| `bid-check` | Amazon Ads campaign export and bid performance data; documented business request | `skills/bid-check.md` → Required Evidence |
| `acos-check` | Amazon Ads campaign performance report; documented business request | `skills/acos-check.md` → Required Evidence |
| `budget-check` | Amazon Ads campaign export and budget report; documented business request | `skills/budget-check.md` → Required Evidence |
| `hour-budget-check` | Amazon Ads **current-day (intraday)** campaign report; campaign/scope context; documented business request | `skills/hour-budget-check.md` → Required Evidence |
| `product-pause-check` | Amazon Ads **product/ASIN-level** performance report; product master data for product identity; campaign/scope context; documented business request | `skills/product-pause-check.md` → Required Evidence |
| `waste-scan` | Amazon Ads campaign performance report; Search Term Report; documented business request | `skills/waste-scan.md` → Required Evidence |
| `keyword-expand` | Amazon Search Term Report; Amazon keyword/performance report; Helium 10 export; Amazon Brand Analytics; documented business request | `skills/keyword-expand.md` → Required Evidence |
| `campaign-audit` | Validated upstream review outputs, plus the Amazon Ads reports underlying those reviews; documented business request | `skills/campaign-audit.md` → Required Evidence |
| `report-draft` | Validated `campaign-audit` output and validated upstream review outputs, plus the Amazon Ads reports underlying them; documented business request | `skills/report-draft.md` → Required Evidence |
| `scale-check` | Validated `campaign-audit`, `acos-check` and `budget-check` outputs; stock/inventory evidence; the Amazon Ads reports underlying those reviews; documented business request | `skills/scale-check.md` → Required Evidence |

**Reading the labels.**

- Labels are **source-level only.** Where an owning skill enumerates specific
  metric fields, evaluation windows, conditions or gates, those are **not** carried
  here — they remain in the owning section.
- Rows naming *validated upstream outputs* (`campaign-audit`, `report-draft`,
  `scale-check`) consume other skills' validated findings as their input. Their
  underlying Amazon Ads evidence is whatever those upstream reviews cited; this
  index does not enumerate it.
- `product-pause-check` additionally depends on product master data. The
  product-master owner is `context/amazon-vendor-bridge.md`, whose unpopulated
  state is already indexed as **GAP-C08** in
  `validation/REPOSITORY_GAP_REGISTER.md`. That gap is referenced here, not
  restated, and is **not** changed by this index.

---

## Coverage Validation

Counts measured against the repository at HEAD
`8aa58828819146a1b1e6957d5f1444f7a7a10e23`. `skills/README.md` is the layer README,
not a skill, and is correctly excluded from the skill count.

| Measure | Expected for PASS | Actual | Result |
|---------|-------------------|--------|--------|
| Skill files discovered under `skills/` | 12 | **12** | PASS |
| Skills indexed in the table above | 12 | **12** | PASS |
| Missing skills (discovered but not indexed) | 0 | **0** | PASS |
| Duplicate rows (a skill appearing more than once) | 0 | **0** | PASS |
| Skills lacking a `## Required Evidence` section | 0 | **0** | PASS |

**Coverage result: PASS.** Every skill file discovered in the repository appears
exactly once, and each carries the `## Required Evidence` section its row points
to. No count was assumed; each was measured.

---

## Gap Relationship

- This asset **supports work related to GAP-E03** (external evidence sources cited
  but not filed) by making the documented per-skill evidence requirements
  navigable from one place.
- It **does NOT resolve GAP-E03.** Nothing here files any evidence, and no source
  becomes reachable because it is listed.
- **GAP-E03's status is unchanged** — it remains as recorded in its owning file and
  indexed in `validation/REPOSITORY_GAP_REGISTER.md`.
- **GAP-S03** (skill→field dependency mappings largely unconfirmed) is **adjacent
  but is not resolved by this index.** This index maps skill → evidence *source*
  at routing level; it does not confirm, define or complete any skill→field
  mapping, which remains owned by each skill's Dependency Matrix.
- **`validation/REPOSITORY_GAP_REGISTER.md` is not modified** by this document. No
  gap is created, resolved, narrowed or re-scoped.

---

## Known Limits

- **This index does not prove that any evidence has been exported or filed.** It
  records what skills document that they require, nothing more.
- **It does not define evidence-field mappings.** Where a field-level mapping
  exists, it is owned by the skill's own Dependency Matrix; where it does not, it
  remains `[VERIFY]` there (GAP-S03).
- **It resolves no `[VERIFY]` item** anywhere in the repository.
- **It authorises no Amazon Ads execution.** This repository holds no Amazon Ads
  connection and no credentials; it produces documents, not actions (`CLAUDE.md`).
- **It does not replace `evidence/README.md` or any `skills/*.md` file.** For
  evidence governance read `evidence/README.md`; for any requirement read the
  owning skill.
- **Neutral labels are deliberately lossy.** They are sufficient to route, not to
  execute. Acting on a label without reading the owning skill risks scoping the
  wrong evidence.
- **This index is not self-updating.** If a skill's `Required Evidence` section
  changes, or a skill is added, this file must be re-derived. It records the HEAD
  it was built from so drift is detectable.

---

## Owner / Review / Status

| Field | Value |
|-------|-------|
| Owner | **Jathukulan** — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | **[VERIFY]** — no Technical / Queryability Reviewer role is defined repository-wide (GAP-G01). None is invented or assigned here. |
| Status | **Active.** Created 2026-07-30 as a pointer-only index at HEAD `8aa58828819146a1b1e6957d5f1444f7a7a10e23`. All twelve discovered skills are indexed; coverage validation returns PASS. No existing file was modified and no gap status changed. |
| Next step | Use this index to determine the **minimum evidence acquisition** needed for the first evidence-backed skill run — that is, read the owning `Required Evidence` sections for the skills to be run first and identify which sources must be obtained. Determining, approving and performing that acquisition is separate work and is **not** authorised by this document. |

---

## Pass / Fail Rule

This document PASSES only if all of the following hold:

- ✓ **Every discovered skill appears exactly once** — 12 discovered, 12 indexed, 0
  missing, 0 duplicates (see **Coverage Validation**).
- ✓ **Every row points to its owning `Required Evidence` section** — each of the
  twelve rows cites `skills/<file>.md → Required Evidence`, and each named file
  was confirmed to contain that section.
- ✓ **No business rule, threshold, decision criterion or detailed evidence
  specification is duplicated** — no ACoS, ROAS, CTR, CVR, click, budget, bid,
  pause or scale value appears here; no evaluation formula, workflow step,
  condition, window or required-field specification is copied; labels are
  source-level only.
- ✓ **No `[VERIFY]` is resolved** — every `[VERIFY]` referenced remains open and
  owned by its source file.
- ✓ **No gap status changes** — GAP-E03, GAP-S03, GAP-C08 and every other gap
  remain exactly as recorded; the Gap Register is untouched.
- ✓ **Only the approved target file is created** —
  `handover/SKILL_EVIDENCE_REQUIREMENTS_INDEX.md`. No existing file is modified,
  moved, renamed or deleted.

**Output: PASS**
