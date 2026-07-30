<!--
Governance decision record — ARCHITECTURE DIRECTION APPROVED; IMPLEMENTATION NOT
APPROVED.

This file records the Owner's approval of an architecture direction for where
confidential binary primary evidence should be stored and how the AIOS should
reference it. The DIRECTION is approved. THIS APPROVAL APPROVED NOTHING DOWNSTREAM
OF IT: no storage location, no reference mechanism, no retention rule, no schema
change, and no implementation step. That statement is the SCOPE OF THIS APPROVAL,
not a description of current repository governance — some downstream matters have
SINCE been confirmed or partly approved under separate Owner approval. For current
state read "Approval Record" and "Implementation Preconditions" (in particular
Preconditions 1 and 2) together with the owning governance files they name.
It is NOT filled from decisions/TEMPLATE_DECISION_RECORD.md;
whether an approved decision must be re-issued in that template's structure is
recorded as an open precondition. See "Approval Record", "Owner / Review / Status"
and "Implementation Preconditions".

The filename retains its original `DRAFT_` prefix. The prefix is now semantically
stale, but `CLAUDE.md` forbids renaming existing files and no decision-record
filename convention is defined (`decisions/TEMPLATE_DECISION_RECORD.md` → Known
Limitations). The status inside this document, not the filename, is authoritative.
-->

# Decision — Confidential Binary Primary-Evidence Storage and Referencing

**Architecture direction: APPROVED. Implementation: NOT APPROVED.**

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — **architecture direction approved; implementation not approved** |
| Approval Status | **ARCHITECTURE DIRECTION APPROVED — IMPLEMENTATION NOT APPROVED** |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01) |
| Approved By | **Jathukulan — repository Owner. Direction only.** |
| Approval Date | 2026-07-28 — the date the Owner's direction approval was communicated and recorded in this repository. If the Owner's underlying decision was taken on an earlier date, that date is `[VERIFY]`; none is invented here. |
| Approval Scope | **The architecture direction only.** This architecture-direction approval did not itself approve any storage location, reference mechanism, retention rule, schema change, permissions model, supersession process or implementation step. **This field records the scope of that approval, not current repository governance** — for current state see **Precondition 1**, **Precondition 2** and the owning governance files they name. |
| Created | 2026-07-28 |
| Revised | 2026-07-28 — (i) four review findings addressed: evidence supersession (Known Unknown 14), evidence owner/steward (Known Unknown 15), Gap Impact coverage note, retention as an explicit implementation gate (Precondition 2); current-state statements re-checked at HEAD `542ff02`, none changed. (ii) Owner direction approval recorded — see **Approval Record**. (iii) 2026-07-28 — Owner-confirmed Precondition 1 storage governance facts recorded under **Scope A — governance facts only**; Precondition 1 moved OPEN → **PARTIALLY SETTLED**. No implementation performed, no storage provisioned or accessed, no gap created or resolved, and no `[VERIFY]` resolved beyond the attributes the Owner explicitly supplied. (iv) 2026-07-30 — documentation-state reconciliation only: **Precondition 2 moved OPEN → PARTIALLY SETTLED** to match the retention governance committed in `evidence/README.md` at commit `f0591a2`. No retention value is copied into this record, no implementation performed, no storage provisioned or accessed, no gap created, resolved or narrowed, and no `[VERIFY]` resolved. |
| Authoritative for | **The approved architecture direction only, and nothing else.** It defines no storage location, no reference format, no business rule, and authorises no action. |
| Implementation Allowed | **NO** — unchanged by this approval; see **Implementation Preconditions** |

---

## Approval Record

**Approved — architecture direction only.**

The Owner has approved the following architecture direction for confidential
binary primary evidence:

> Confidential binary primary evidence should live outside Git in an approved
> company-controlled location, while version-controlled metadata provides a
> durable reference to that evidence.

**What this approval establishes:**

- **Option C is APPROVED as the architecture direction.** It is the settled
  direction for confidential binary primary evidence in this repository.
- Approved by **Jathukulan, repository Owner**, on **2026-07-28**, as **direction
  only**.

**What this approval does NOT establish.** This section is **scope-specific and
historical**: it records what the 2026-07-28 architecture-direction approval did
**not** itself approve. It is **not** a statement of current repository governance
state — for that, read the later owning sections named in each bullet. None of the
following was established by that approval:

- **Option C implementation is NOT APPROVED.** `Implementation Allowed` remains
  **NO**.
- **This approval approved no storage location, provider, host, service, path,
  bucket, drive or URL**, and no such identifier is defined anywhere in this
  repository. Storage **governance facts** confirmed later are recorded in
  **Precondition 1**, where the official location identifier remains `[VERIFY]`.
- **This approval did not itself approve** any stable-reference mechanism, evidence
  ID, checksum or file-size schema, confidentiality-classification schema,
  permissions or access-control model, retention rule, supersession mechanism, or
  evidence-owner/steward assignment. For **current** state see **Precondition 1**
  (storage governance), **Precondition 2** together with `evidence/README.md`
  (retention governance), and the **Known Unknowns / `[VERIFY]`** section. Anything
  not answered there remains `[VERIFY]`.
- **This approval authorised no modification to any evidence governance file** —
  the schema and governance changes contemplated here remain gated behind
  Implementation Preconditions 3 and 4. `evidence/README.md` has **since** been
  changed under **separate Owner approval** to record retention governance (see
  **Precondition 2**); `evidence/TEMPLATE_EVIDENCE_RECORD.md` is unchanged.
- **No `[VERIFY]` item was resolved by this approval.** At the time of approval,
  Known Unknowns 1–15 stood exactly as recorded. Some have **since** been answered
  or partly answered by later, separately approved governance. The **Known Unknowns
  / `[VERIFY]`** section carries their current state and is authoritative for it;
  this bullet records only that the direction approval itself resolved none of them.
- **No existing gap was resolved by this approval.** GAP-E01, GAP-E02, GAP-E03,
  GAP-C09, GAP-C10 and GAP-G01 all remain open, and this approval modified
  `validation/REPOSITORY_GAP_REGISTER.md` in no way. The register's GAP-E02 row was
  **later** updated under separate approval to re-point at the retention governance;
  **GAP-E02's status was not changed** and remains Open `[VERIFY]`.
- **All eight Implementation Preconditions remain in force** — Preconditions 3–6
  and 8 are **OPEN**; Preconditions 1, 2 and 7 are **PARTIALLY SETTLED**. Approving
  the direction does not satisfy, waive, reduce or reorder any of them. The change
  of state attributable to **this approval** is recorded openly in
  **Precondition 7**: because this record is no longer an unapproved draft, it is
  now eligible to remain in `decisions/`. The rest of that precondition — how much
  rationale a decision record may carry, and where future unapproved drafts belong —
  stays `[VERIFY]`. Preconditions 1 and 2 moved to **PARTIALLY SETTLED** later and
  for separate reasons, recorded in **Precondition 1** and **Precondition 2**
  respectively; neither was changed by this approval, and neither is satisfied.

**Option E remains the active safe interim operational state.** Until every
implementation precondition is met, no confidential binary is stored or referenced
under this direction, and canonical rule files continue to record their
`Evidence-filing status` as `[VERIFY]`.

**Approver role.** The Owner approved in the capacity of repository `Owner`
(`README.md`, `CLAUDE.md`). This does **not** define a Technical, Queryability or
Business Reviewer role — those remain `[VERIFY]` under GAP-G01, and no reviewer is
assigned by this approval.

---

## Purpose

To record, in one place, the **approved governance direction** for storing
confidential binary primary evidence (for example supplier or Amazon
specification PDFs) and for referencing that evidence durably from this
repository, **without committing the binary to Git** — together with everything
about that direction that remains unresolved.

This document exists because the repository documented no answer to that
question, and several `context/` rule files already cite confidential PDFs they
cannot point a reader to.

**The direction is approved; nothing has been implemented.** This document
creates no evidence record, moves no file, defines no storage location, modifies
no governance document, and applies nothing to Amazon Ads. Per `CLAUDE.md`, this
repository produces documents, not actions.

### Placement note

**For this document, the placement question is now settled.**
`decisions/README.md` excludes *"Draft recommendations **not yet approved**"*. With
the Owner's direction approval recorded above, this document is no longer an
unapproved draft: it records a decision taken and an approval given, which is the
stated purpose of `decisions/` (*"Record of decisions taken and approvals given"*).
It is therefore **eligible to remain in `decisions/`**.

Two things remain open and are **not** decided by this document:

- **How much rationale may accompany a decision record.** `decisions/README.md`
  also directs *"Analysis (use `evidence/` or `reports/`)"* elsewhere, and this
  record carries a substantial options analysis as its rationale. Where that line
  falls is undocumented — `[VERIFY]`.
- **Where FUTURE unapproved governance drafts belong.** Whether an unapproved
  governance draft belongs in `decisions/`, `validation/` or elsewhere is a
  general repository question that remains `[VERIFY]` (Known Unknown 13,
  Implementation Precondition 7). **No new draft-storage convention is designed
  here**, and `decisions/README.md` is not changed.

**Current status: this file is tracked and committed.** It was first committed at
`a3f70c8` and revised at `0fc9ea5`; revisions recorded in the **Revised** metadata
entry after that point may still be uncommitted in the working tree at any given
moment. That is a statement of fact about version control, not a statement about
its eligibility to remain in `decisions/`.

---

## Business Question

> **Where should confidential binary primary evidence live, and how should the
> AIOS reference it durably without committing the binary to Git?**

**In scope:** storage location class for confidential binaries; what is committed
to Git in their place; what a stable reference must let a reader determine.

**Out of scope (owned elsewhere, not answered here):** the evidence lifecycle
(GAP-E01), retention and archival (GAP-E02), general repository governance, the
filing of any specific named source, and any Amazon PPC business rule. Those
remain owned by `evidence/README.md`, `validation/REPOSITORY_GAP_REGISTER.md`
and the `context/` layer respectively.

---

## Current State / Evidence

**This section is a dated snapshot, not a live view.** Every statement below was
verified by reading the named file in this repository on 2026-07-28 at commit
`e52d3de`, and **is preserved as the state at that date**. No fact outside
repository evidence is introduced. Where later, separately approved governance has
since moved an item — in particular storage governance — the owning section wins:
see **Precondition 1 — Owner-Confirmed Storage Governance Facts** for current
storage state, **Precondition 2** with `evidence/README.md` for current retention
state, and the **Known Unknowns / `[VERIFY]`** section for everything else. No
confirmed value from those sections is restated here.

| # | State confirmed as at 2026-07-28 (`e52d3de`) | Where verified |
|---|-------------------------|----------------|
| 1 | The repository forbids creating binary files. | `CLAUDE.md` → "Repository Safety Rules": *"Do not create binary files."* |
| 2 | The repository holds no Amazon Ads connection and no credentials; it produces documents, not actions. | `CLAUDE.md` → "Never Modify Amazon Ads" |
| 3 | Confidential PDFs cannot be assumed safe to commit. `.gitignore` ignores `.csv`, `.xlsx`, `.xls`, `.png`, `.jpg` under a "Commercial Data" heading, and secrets under a "Secrets" heading — **it does not list any PDF pattern.** A PDF placed in the working tree today would therefore be a candidate for commit rather than ignored. | `.gitignore` (read in full) |
| 4 | Git history is distributed and effectively permanent for anyone with a clone; the repository has a remote (`origin/main`). No repository document states that committed binaries could be withdrawn. | `git status` at `e52d3de` |
| 5 | `evidence/` holds **primary evidence** — original source material — and this is defined separately from canonical business truth. | `evidence/README.md` → "Purpose", "Duplicate Truth Prevention": *"Evidence files remain the original source material."* |
| 6 | **Metadata records provide traceability only and are never a source of business truth.** They point to the original via `Source File` / `Evidence References`; they never replace or alter it. | `evidence/README.md` → "Metadata Relationship", "Duplicate Truth Prevention"; `evidence/TEMPLATE_EVIDENCE_RECORD.md` → "About this template" |
| 7 | Canonical business-rule interpretation remains in the Context layer (`context/`). | `evidence/README.md`; `evidence/TEMPLATE_EVIDENCE_RECORD.md`; `CLAUDE.md` → "No Duplicate Truth" |
| 8 | **No approved external, VM or company-controlled storage location for confidential binaries is documented anywhere in this repository.** A repository-wide search for external / VM / ignored-local evidence storage returned no such document. | Repository search on 2026-07-28; `decisions/` contains only `README.md` and `TEMPLATE_DECISION_RECORD.md` |
| 9 | **No stable evidence-ID or checksum reference mechanism is documented.** No file defines an evidence ID syntax, a checksum field, or an immutable-identity check. | Repository search on 2026-07-28 |
| 10 | The evidence metadata template defines `Source File` as a free-text field and **has no checksum, file-size, storage-location or access-classification field.** | `evidence/TEMPLATE_EVIDENCE_RECORD.md` → "Evidence Metadata" block |
| 11 | Evidence filenames follow a repository naming convention (`YYYY-MM-DD-source-description.ext`, record `…-record.md`), and that convention is explicitly **not** a business rule and defines no identity or integrity guarantee. | `evidence/README.md` → "Evidence Filename Convention" |
| 12 | Canonical rule files already depend on confidential PDFs that a reader cannot open, and each records its filing status as `[VERIFY]`. | `context/hour-budget-rules.md` → "Source Evidence"; `context/product-pause-rules.md` → "Source Evidence"; `context/target-metrics.md` → "Evidence" table |
| 13 | Externally-cited sources not filed in the repository are already a ranked risk. | `validation/CONTEXT_REVIEW.md`; `validation/REPOSITORY_GAP_REGISTER.md` → GAP-E03 (Priority High) |
| 14 | No reviewer or approver role beyond the repository Owner is defined. | `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01; repeated as `Reviewer: [VERIFY]` across `skills/` |
| 15 | A workstation `Downloads` path is not a durable, queryable company reference: it is machine-specific, user-specific, not company-controlled, and cannot be opened by another person or by a clean LLM reading this repository. No repository document records such a path as an approved evidence location. | Derived from #5–#8 and `CLAUDE.md` → "Queryability First" (*"Write so another LLM can use the file tomorrow with no verbal explanation"*) |

**Net state as at 2026-07-28:** the repository requires evidence-first traceability,
forbids creating binaries, has no ignore rule covering PDFs, has no approved place
to put a confidential binary, and has no mechanism to reference one durably.
Confidential primary evidence was therefore **cited but unreachable**. For state
after that date, read the owning sections named above rather than this paragraph.

---

## Constraints

Constraints below are quoted from or directly traceable to repository governance.
They bound every option in the next section.

1. **No binary creation.** `CLAUDE.md` — *"Do not create binary files."*
2. **Evidence First.** Every recommendation must trace to evidence in `evidence/`
   recorded with its source, date and date range (`CLAUDE.md`).
3. **Queryability First.** A reference must be usable by another LLM tomorrow with
   no verbal explanation (`CLAUDE.md`).
4. **No Duplicate Truth.** Each fact lives in exactly one place (`CLAUDE.md`);
   metadata records never become business truth (`evidence/README.md`).
5. **Existing Asset First.** Nothing existing may be overwritten, renamed, moved or
   reorganised (`CLAUDE.md`).
6. **Originals are immutable.** No edited or re-cut versions of an original export
   (`evidence/README.md`).
7. **Human Approval Required.** Governance direction is proposed, never applied
   (`CLAUDE.md`).
8. **Confidentiality.** Commercial data is deliberately kept out of Git — the
   "Commercial Data" and "Secrets" sections of `.gitignore` establish the intent,
   even though no PDF pattern is currently listed.
9. **Irreversibility of commits.** Once a binary is committed and pushed, no
   repository process for its removal is documented.

---

## Options Considered

Only the five options presented for evaluation are assessed. No sixth option is
invented. Each is scored against the seven required dimensions.

**Temporal scope of this entire section — read before any table below.** Every
option table, verdict and the comparison summary is the **original evaluation as
written on 2026-07-28**, preserved as the reasoning that led to the decision. **It
is deliberately not updated as repository state changes.** Several `[VERIFY]`
markers and "not yet defined" assessments in these tables — notably around access
model, custody, backup and retention — have **since** been answered or partly
answered by later, separately approved governance. For **current** state always
read **Precondition 1 — Owner-Confirmed Storage Governance Facts** (storage),
**Precondition 2** together with `evidence/README.md` (retention), and the **Known
Unknowns / `[VERIFY]`** section. Those sections own the current position; nothing
from them is restated in the tables below, and nothing below should be read as a
present-day claim.

### Option A — Metadata record pointing to a personal `Downloads` path

| Dimension | Assessment |
|-----------|------------|
| Confidentiality | Adequate by accident — the binary never enters Git — but the location is uncontrolled and unclassified, so confidentiality is unmanaged rather than protected. |
| Portability | **Fails.** The path resolves on one workstation for one user account. Nobody else, and no clean LLM, can act on it. |
| Queryability | **Fails** `CLAUDE.md` "Queryability First": the reference cannot be resolved without verbal explanation from the individual who holds the file. |
| Git safety | Safe — nothing binary is committed. |
| Evidence durability | **Fails.** A `Downloads` folder is transient by convention; loss, clear-out or machine change destroys the primary evidence with no record that it is gone. |
| Duplicate-truth risk | Moderate-to-high. When the original becomes unreachable, the metadata record becomes the only surviving description and drifts into being treated as truth — exactly what `evidence/README.md` forbids. |
| Operational limitations | Creates the appearance of evidence-first compliance without the substance. Would let a recommendation claim a traceable source that no reviewer can open. |

**Verdict:** not acceptable as a durable answer.

### Option B — Confidential binaries in a defined ignored-local repository location, with committed metadata records

| Dimension | Assessment |
|-----------|------------|
| Confidentiality | Depends entirely on an ignore rule holding. `.gitignore` today lists no PDF pattern (#3), so this option requires an ignore change that is **out of scope for this draft** and unapproved. A single mis-scoped rule or `git add -f` exposes the binary. |
| Portability | **Fails.** "Ignored-local" means present on one clone only. Another clone of the same repository is empty of the binary, with nothing to indicate that. |
| Queryability | Weak. The path is stable and describable, which is better than Option A, but the file is still unreachable for anyone who did not personally receive it. |
| Git safety | Conditionally safe, and fragile. Safety rests on configuration rather than on the binary being outside the repository boundary. |
| Evidence durability | Weak. Local disk only; no company custody, no documented backup. |
| Duplicate-truth risk | Same drift risk as Option A once the local copy is unavailable. |
| Operational limitations | Requires modifying `.gitignore` and evidence governance — both explicitly excluded from this task, and neither approved. |

**Verdict:** an improvement on A, but it keeps confidential material inside the
repository boundary and depends on a not-yet-approved ignore change.

### Option C — Confidential binaries in an approved external / company-controlled evidence location, with committed metadata records

| Dimension | Assessment |
|-----------|------------|
| Confidentiality | **Strongest of the five.** The binary sits outside the Git boundary entirely, in a location whose access can be governed by whoever controls it. Access control specifics are `[VERIFY]` — no such location exists yet. |
| Portability | **Strongest.** Any authorised person, on any machine, retrieves from the same company-controlled location. The committed metadata record travels with every clone. |
| Queryability | **Strongest**, *conditional on* a stable reference mechanism existing. Without one, this option degrades toward Option A. The reference requirements are set out below. |
| Git safety | **Strongest.** No binary is ever a commit candidate; `CLAUDE.md`'s "do not create binary files" is satisfied structurally, not by configuration. |
| Evidence durability | **Strongest**, conditional on custody and backup that are **not yet defined** — `[VERIFY]`. |
| Duplicate-truth risk | **Lowest**, provided the boundary in the next section is preserved: primary evidence stays the binary, the committed record stays traceability-only, canonical interpretation stays in `context/`. |
| Operational limitations | **State as evaluated on 2026-07-28, when this options analysis was written:** the location did not exist and nothing about it was documented — no host, service, directory, permission model, retention period or backup policy. Implementation is impossible until those are defined and approved. **This row is the original evaluation and is not updated as state changes.** For **current** storage-governance state see **Precondition 1**; for **current** retention-governance state see **Precondition 2** and `evidence/README.md`. No confirmed value is restated here. |

**Verdict:** the only option that satisfies confidentiality, portability, Git
safety and durability simultaneously — and it is entirely blocked on approvals
that have not happened.

### Option D — Confidential binaries committed directly to Git

| Dimension | Assessment |
|-----------|------------|
| Confidentiality | **Fails outright.** Confidential material becomes permanently distributed to every clone and to the remote. |
| Portability | High — but portability of confidential material is the failure, not the benefit. |
| Queryability | High. |
| Git safety | **Fails.** Directly violates `CLAUDE.md` — *"Do not create binary files."* No documented removal process exists (#4/#9). |
| Evidence durability | High and immutable — at an unacceptable confidentiality cost. |
| Duplicate-truth risk | Low. |
| Operational limitations | Irreversible in practice. Rejected on governance grounds regardless of its other properties. |

**Verdict:** rejected. Prohibited by `CLAUDE.md`.

### Option E — No evidence records until storage and reference governance exists

| Dimension | Assessment |
|-----------|------------|
| Confidentiality | Fully preserved — nothing is stored or referenced. |
| Portability | Not applicable. |
| Queryability | **Fails.** Canonical rule files already cite confidential PDFs (#12); with no records at all, a reader cannot even determine *which* source a rule came from or that it exists. |
| Git safety | Fully safe. |
| Evidence durability | **Fails.** Nothing is recorded, so nothing is preserved — not even the knowledge of what the primary evidence was. |
| Duplicate-truth risk | Low in principle, but rule files continue to carry source claims with no companion record, which is itself a traceability defect. |
| Operational limitations | Blocks the evidence-first policy from ever being satisfied and leaves GAP-E03 (Priority High) untouched. Sustainable only as a temporary state. |

**Verdict:** acceptable **only** as the status quo while approval is pending —
which is precisely the state this repository is in today. It is not a destination.

### Comparison summary

| | A | B | C | D | E |
|---|---|---|---|---|---|
| Confidentiality | Unmanaged | Config-dependent | **Strong** `[VERIFY]` | Fails | Strong |
| Portability | Fails | Fails | **Strong** | High | n/a |
| Queryability | Fails | Weak | **Strong** (conditional) | High | Fails |
| Git safety | Safe | Conditional | **Structural** | Fails | Safe |
| Durability | Fails | Weak | **Strong** `[VERIFY]` | High | Fails |
| Duplicate-truth risk | Mod–High | Mod–High | **Low** | Low | Low |
| Blocked by | Nothing (but unusable) | Ignore + governance change | Approvals `[VERIFY]` | Prohibited | Nothing |

---

## Duplicate Truth Boundary

This document holds no business rule and no evidence value. The boundary it
proposes to preserve — restating no rule, only naming which layer owns what — is:

```
CONFIDENTIAL PRIMARY EVIDENCE   →  the original binary, unedited, outside Git
                                   (per evidence/README.md: originals are the
                                   source material and are never re-cut)

COMMITTED METADATA RECORD       →  traceability only, never business truth
                                   (per evidence/README.md and
                                   evidence/TEMPLATE_EVIDENCE_RECORD.md)

CONTEXT (context/)              →  canonical business-rule interpretation —
                                   the only place a rule value is stated

SKILL (skills/)                 →  the evaluation procedure that consumes
                                   evidence and produces DRAFT output only

THIS DOCUMENT (decisions/)      →  the approved architecture direction, and
                                   nothing else; it states no rule, no location
                                   and no mechanism, and authorises no action
```

Specifically:

- A metadata record **does not become** the evidence, and does not become truth
  if the binary is unavailable — it becomes a record of unavailable evidence.
- This draft **does not restate** any KPI target, bid rule, budget rule, hour
  budget rule, product pause rule, keyword strategy or reporting rule. Those are
  referenced to their owning `context/` file and never copied.
- This draft **does not restate** any gap definition; gaps stay owned by their
  source files and indexed by `validation/REPOSITORY_GAP_REGISTER.md`.
- This draft **does not amend** `evidence/README.md`,
  `evidence/TEMPLATE_EVIDENCE_RECORD.md`, `CLAUDE.md`, `.gitignore` or
  `.gitattributes`. Where it identifies a need in those files, it marks it
  `[VERIFY]` for a future approved change.

**Duplicate Truth Check: PASS.**

---

## Decision — Architecture Direction APPROVED; Implementation NOT APPROVED

> **Status: the architecture direction below is APPROVED. Implementation is NOT
> APPROVED.** Everything downstream of the direction — location, mechanism,
> retention, schema, permissions, supersession, ownership and every implementation
> step — was **not approved by this decision**. Some of those matters have **since**
> been confirmed or partly approved under **separate Owner approval**, recorded in
> **Precondition 1** (storage governance) and in **Precondition 2** together with
> `evidence/README.md` (retention governance). Everything still unresolved is
> governed by the **Implementation Preconditions** and the **Known Unknowns /
> `[VERIFY]`** section, which are authoritative for current state. **None of that
> authorises implementation: nothing here may be implemented.** Implementation
> requires the preconditions below and human approval (`CLAUDE.md`).

On the documented constraints, **Option C is the approved architecture
direction**, with **Option E as the active interim state until Option C's
preconditions are met.** Options A, B and D are not adopted: A and B fail
portability and durability, and D is prohibited by `CLAUDE.md`.

Approving this direction settles **which architecture** is to be used. It settles
nothing about **how** it is built: no part of the block below is an instruction to
act, and each `[VERIFY]` inside it is untouched by the approval.

The approved direction is stated at architecture level only:

```
CONFIDENTIAL PRIMARY EVIDENCE
    → stored in an approved, non-Git, company-controlled location
      [VERIFY — no such location is identified or approved for confidential
       binary primary evidence; the storage governance facts confirmed so far
       are recorded in Precondition 1, not here]

COMMITTED METADATA RECORD
    → committed to this repository; carries a stable reference to the
      primary evidence; remains traceability only, never business truth
      [VERIFY — the reference mechanism is not defined]

CONTEXT
    → canonical business-rule interpretation; unchanged by this proposal

SKILL
    → evaluation procedure; unchanged by this proposal
```

**Deliberately not specified — and expressly not approved by this decision.** The
following were **not** approved, not proposed and not implied by this document or by
the approval of the direction, and must not be inferred from either. This list
records the **scope of that approval**, not current repository state: where a later,
separately approved governance record answers an item, that owning record governs —
see **Precondition 1**, **Precondition 2** and the **Known Unknowns / `[VERIFY]`**
section. Anything not answered there remains `[VERIFY]`:

- host or VM name, and whether a VM is the right class of location at all;
- directory, path or folder structure;
- cloud service, provider, bucket, drive or URL;
- permission model, access-control list or authorisation process;
- retention period, and the archive / archival trigger — **this decision established
  neither.** They are not one uniform current-state item: retention governance is
  owned by `evidence/README.md` and is now **partly approved**, while the **archive
  trigger** and the **preservation exception** remain `[VERIFY]` (see
  **Precondition 2**). No retention value is recorded in this document;
- evidence ID syntax or allocation process;
- checksum algorithm choice, encoding or schema placement;
- backup, replication or disaster-recovery policy;
- who may retrieve confidential evidence, and how they request it.

Inventing any of the above would breach `CLAUDE.md` — *"Never invent Amazon PPC
rules, business processes, metrics or thresholds"* — and would create a parallel
truth for an architecture that does not exist.

---

## Stable Reference Requirements

These are **requirements to be satisfied by a future approved mechanism**, not a
design and not a schema. They state what a clean LLM or a developer with no
verbal briefing must be able to determine from a committed record alone.

| # | The reference must let a reader determine | Why (traceable to governance) | Satisfied today? |
|---|-------------------------------------------|-------------------------------|------------------|
| R1 | **What evidence is being referenced** — its human-readable identity and what it contains. | Evidence First; Queryability First (`CLAUDE.md`). | Partly — `Evidence Title` / `Evidence Type` exist in the template. |
| R2 | **Exact source identity** — the specific source system, document and version, distinguished from any similar document. | `evidence/README.md` requires source, date and date range. | Partly — `Source System` / `Source File` are free text with no version or identity guarantee. |
| R3 | **Where an authorised person can retrieve it** — a location reference that resolves for someone other than the person who obtained the file. | Queryability First; Option A's failure mode (#15). | **No** — no storage-location field and no approved location. `[VERIFY]` |
| R4 | **Which canonical asset it supports** — the `context/` rule or `reports/` output that depends on it. | No Duplicate Truth; evidence-first traceability. | Partly — `Related Skills` / `Related Report` exist; no field names the supported `context/` asset. `[VERIFY]` |
| R5 | **Whether it is the same immutable source** — that the file retrieved today is byte-identical to the file the rule was extracted from. | Originals are immutable (`evidence/README.md`); rule values are extracted from a specific document (`context/hour-budget-rules.md`, `context/product-pause-rules.md`). | **No** — no integrity mechanism exists. `[VERIFY]` |
| R6 | **Confidentiality / access classification** — whether the evidence is confidential and what class of handling it needs. | Confidential material is the reason the binary stays out of Git. | **No** — no classification field exists. `[VERIFY]` |
| R7 | **Current validation status** — whether the evidence is confirmed filed and usable, or still outstanding. | `context/` files already record `Evidence-filing status: [VERIFY]`; GAP-E03. | Partly — `Validation Status` exists in the template but its vocabulary is undefined. `[VERIFY]` |

**R5 fixes identity; it does not address change.** R1–R7 describe how to identify
and retrieve **one** version of a source. What should happen when that source is
legitimately reissued or replaced is a separate and currently unresolved question,
recorded as **Known Unknown 14**. A mechanism that satisfied R5 without answering
supersession would allow a `context/` rule to cite a source that has since been
superseded, with nothing in the committed record to show it. No answer is proposed
here.

### Would SHA-256 + file size improve immutable identity?

**Assessment: yes, in principle — and it is not adopted here.**

- A cryptographic digest plus byte size would let a reader confirm that a
  retrieved binary is the *same* file a rule was extracted from, satisfying **R5**,
  which no current field addresses. Filename and date cannot do this: filenames are
  a naming convention explicitly declared not to be a business rule
  (`evidence/README.md`), and the same filename can hold different bytes.
- It would also strengthen **R2** by giving a source identity that does not depend
  on a path remaining valid.
- It would introduce no confidential content into Git: a digest and a size describe
  the file without reproducing any of it.

**However — the current template defines no checksum field, and this draft does
not add one.** Adding a field would modify `evidence/TEMPLATE_EVIDENCE_RECORD.md`,
which is out of scope and unapproved. Therefore:

- **Schema support for a checksum: `[VERIFY]`.**
- Algorithm choice, encoding, where the value would live, and who computes and
  re-verifies it: **all `[VERIFY]`, none proposed here.**
- No checksum value is recorded anywhere by this document.

---

## Known Unknowns / [VERIFY]

**This section is authoritative for the current state of each item.** Every item
was genuinely undocumented in this repository when first recorded, and none has
ever been worked around by inventing a value. Some have **since** been answered or
partly answered by later, separately approved governance — each such item says so
in its own entry and names the owning section. Items still marked `[VERIFY]` remain
unresolved. No approved value is restated here; the owning section holds it.

1. **Approved storage location** — **partly answered.** The class and company-control
   status are now confirmed; the **official drive / location name or identifier is
   not**, and explicit permission to store confidential binary primary evidence
   there is not. Values are recorded once, in **Precondition 1 — Owner-Confirmed
   Storage Governance Facts**, and are not restated here. `[VERIFY]` on the
   identifier and on the confidentiality permission.
2. **Location class** — **answered.** Recorded in the Owner-confirmed facts section.
3. **Access model** — **answered as supplied**: who may access, and how access is
   requested and granted, are both recorded in the Owner-confirmed facts section.
4. **Custody and backup** — **answered as supplied**: custodian, and the existence
   of backup or replication, are recorded in the Owner-confirmed facts section. No
   documented backup arrangement detail was supplied, and none is invented.
5. **Retention** — **partly answered.** Retention governance covering the
   confidential-primary-evidence subset relevant to this direction is now recorded
   in `evidence/README.md` → **Evidence Retention Governance**, which owns it; its
   approved values are **not restated here**. Two attributes of that governance
   remain `[VERIFY]` — the **archive trigger** and the **preservation exception** —
   and **GAP-E02 remains Open `[VERIFY]`**, retaining unresolved retention
   governance for evidence outside that subset. See **Implementation
   Precondition 2**. `[VERIFY]`
6. **Evidence ID mechanism** — no evidence-ID concept, syntax or allocation process
   is documented. `[VERIFY]`
7. **Checksum schema support** — `evidence/TEMPLATE_EVIDENCE_RECORD.md` has no
   checksum or file-size field; none is added here. `[VERIFY]`
8. **Storage-location and classification fields** — the template has no field for
   retrieval location (R3) or confidentiality class (R6). `[VERIFY]`
9. **Validation-status vocabulary** — the allowed values for `Validation Status` are
   undefined. `[VERIFY]`
10. **`.gitignore` coverage of PDFs** — no PDF pattern is listed today; whether one
    should be added is a separate, unapproved change and is **not** proposed or made
    here. `[VERIFY]`
11. **Reviewer / approver roles** — no Technical or Queryability Reviewer role is
    defined repository-wide (GAP-G01). `[VERIFY]`
12. **Decision filename and lifecycle convention** — `decisions/README.md` defines no
    filename format, and `decisions/TEMPLATE_DECISION_RECORD.md` records both the
    filename convention and the decision lifecycle as open. The filename of this
    file follows the descriptive, upper-case style used by other repository
    governance documents; it asserts no numbering scheme. `[VERIFY]`
13. **Home for FUTURE unapproved governance drafts** — whether an unapproved
    governance draft belongs in `decisions/`, `validation/` or elsewhere remains a
    general repository question (see the Placement note above). The direction
    approval settled placement for **this** record only; it defines no convention
    for future drafts, and none is designed here. `[VERIFY]`
14. **Evidence supersession** — what happens when a primary evidence source is
    reissued, replaced, updated or otherwise superseded is undocumented. Four
    questions are open and none is answered here: (a) how a future reviewer
    determines **which version of a source supported the canonical interpretation
    currently recorded in `context/`**; (b) whether superseded primary evidence
    remains retrievable, and for how long; (c) how any successor/predecessor
    relationship between sources would be represented in a committed record; and
    (d) what a superseded source means for a rule already extracted from it. This
    is inseparable from **R5** (immutable identity): fixing identity to one file
    says nothing about what should happen when a newer file properly replaces it.
    No version numbering, archive behaviour, successor identifier, evidence ID,
    filename, storage path, retention behaviour or deletion policy is proposed
    here. `[VERIFY]`
15. **Evidence owner / steward** — who owns or stewards an **individual** primary
    evidence asset, who is accountable for its custody and for the continuing
    correctness of its reference, and whether that owner must appear in the
    committed metadata record, are all undocumented.
    `evidence/TEMPLATE_EVIDENCE_RECORD.md` **has no dedicated evidence-owner or
    steward field** — its `Evidence Metadata` block records title, type, source
    system, source file, collection date, evidence date range, marketplace,
    campaign and product identifiers only. This is a **different concept from the
    Owner of this decision**: the repository Owner recorded in `README.md` and
    `CLAUDE.md` owns the decision, and it must **not** be inferred that the same
    person owns or stewards every evidence asset. No person, role, team or
    department is assigned here, and the template is not changed. `[VERIFY]`

---

## Owner / Review / Status

| Role | Value | Source |
|------|-------|--------|
| Owner | **Jathukulan** | `README.md`, `CLAUDE.md` — repository Owner |
| Reviewer | **[VERIFY]** — no Technical / Queryability Reviewer role is defined in this repository; none is assigned by the direction approval | GAP-G01 in `validation/REPOSITORY_GAP_REGISTER.md` |
| Approver (architecture direction) | **Jathukulan — repository Owner**, approving the **direction only** | Owner authority in `README.md`, `CLAUDE.md`. The general approver-role question is unresolved — `[VERIFY]`, GAP-G01; the approval-status vocabulary is likewise `[VERIFY]` in `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations, so the status wording above is self-describing rather than relying on an undefined status word |
| Approver (implementation) | **[VERIFY]** — no implementation approval has been given or sought | Implementation Preconditions |
| Status | **ARCHITECTURE DIRECTION APPROVED — IMPLEMENTATION NOT APPROVED** | This document |
| Approval Date (direction) | 2026-07-28 — date communicated and recorded. Any earlier underlying decision date is `[VERIFY]` | Approval Record |

No reviewer identity is invented. Where a role is not established in the
repository it is left `[VERIFY]` and unanswered, per `CLAUDE.md`. The Owner's
approval of the direction defines no reviewer role.

**Decision Owner is not evidence owner.** The Owner above owns **this decision**.
Who owns or stewards an **individual piece of primary evidence** is a separate,
currently undocumented question — see **Known Unknown 15**. Nothing in this
document assigns evidence ownership to any person or role.

**Implementation cannot begin until every one of the eight Implementation
Preconditions below is met** — not merely the storage location and the reference
mechanism, but also retention governance (Precondition 2), any metadata-template
change, the `.gitignore` question, the reviewer-role question, placement, and
re-issue. Approving the architecture direction satisfies none of them.

Until then the repository remains in the **Option E interim state**: canonical
rule files continue to record their `Evidence-filing status` as `[VERIFY]`, and no
confidential binary is stored or referenced under this direction.

---

## Precondition 1 — Owner-Confirmed Storage Governance Facts

**Scope A — governance facts only.** The Owner supplied and confirmed the facts
below as the governance definition for Precondition 1. Recording them **authorises
nothing**: no storage was provisioned, no folder created, no permission tested, no
file uploaded, moved or copied, no evidence record created, and no `.gitignore`,
`evidence/` or schema change made. `Implementation Allowed` remains **NO**.

These facts are recorded **verbatim as supplied**. Nothing is inferred, expanded or
strengthened, and no identifier, path, server, host, share name, URL, provider or
service is invented.

| Attribute | Owner-confirmed value | State |
|-----------|----------------------|-------|
| Storage class | **Shared network drive for internal documents** | **Confirmed** |
| Official drive / location name or identifier | — | **`[VERIFY]`** — not supplied; none invented here |
| Custodian | **CPPC** | **Confirmed** |
| Backup or replication exists | **YES** | **Confirmed.** No documented arrangement detail was supplied with this confirmation, and none is invented here |
| Who may access | **Manager, TL, MD** | **Confirmed** |
| How access is requested / granted | **Manager request** | **Confirmed** |
| Company-controlled | **YES** | **Confirmed** |
| Confidential binary primary evidence explicitly permitted there | — | **`[VERIFY]`** — not confirmed; do **not** infer permission from company control or from the class |
| Durable / independent of an individual employee's workstation | **YES, with permission** | **Confirmed, as qualified.** The qualifier "with permission" is part of the answer and is not dropped |
| Date these arrangements were confirmed | — | **`[VERIFY]`** — the Owner states the arrangements were confirmed **before 2026-07-28**, but the exact date was not noted. No date is inferred. **Provenance only: this is not a Precondition 1 closure condition** |
| Approval scope | **Scope A — governance facts only** | **Confirmed** |

**What these facts do not do.** They do not approve Option C implementation, do not
identify a specific location, do not establish that confidential binary primary
evidence may be placed there, and do not satisfy any other precondition. The
architecture direction remains approved; implementation remains not approved;
Option E remains the active interim state.

**Date boundary.** The `Approval Date` in the header of this record (2026-07-28) is
the date of the **architecture-direction approval**. It is a different event from
the storage-arrangement confirmation above, whose exact date is `[VERIFY]`. The two
must not be conflated, and the direction-approval date must not be read as the
storage-confirmation date.

---

## Implementation Preconditions

All of the following must be **approved and documented** before any part of the
approved direction is implemented. This list is a gate, not a plan, and it
authorises nothing. **The Owner's approval of the architecture direction satisfies
none of these preconditions and does not reduce, waive or reorder any of them.**
**All eight remain in force and none is satisfied.** Their current states are:
Preconditions **3–6 and 8 OPEN**; Preconditions **1, 2 and 7 PARTIALLY SETTLED**,
each recorded explicitly in its own entry below. **PARTIALLY SETTLED does not mean
met** — a precondition gates implementation until it is fully satisfied.

1. An approved storage location for confidential primary evidence is **defined and
   documented** by the Owner — including its class, custodian and access model
   (items 1–4 above). **PARTIALLY SETTLED — stated openly, not silently:** the
   Owner has confirmed the storage class, custodian, backup existence, access list,
   access-request route, company control and workstation independence — see
   **Precondition 1 — Owner-Confirmed Storage Governance Facts** above. **Two
   required attributes remain `[VERIFY]` and keep this precondition unmet:**
   (a) the official drive / location name or identifier; (b) explicit permission to
   store confidential binary primary evidence there. Until both are answered,
   Precondition 1 is **not** satisfied. The **exact date** on which the
   arrangements were confirmed is also `[VERIFY]`, but it is **provenance only and
   is not a closure condition** — this precondition requires the location to be
   defined and documented with its class, custodian and access model, not dated.
2. **Required retention / archival governance is resolved or approved.**
   **PARTIALLY SETTLED — stated openly, not silently.** Storage **must not be stood
   up** while the retention question remains open, because a confidential-evidence
   store with no retention rule is an open-ended commitment with no defined end
   state. Retention is **not owned by this record**: it is owned by
   `evidence/README.md` → **Evidence Retention Governance** and indexed as
   **GAP-E02**.

   **What changed.** Retention governance covering the confidential-primary-evidence
   subset relevant to this direction is now **partly approved** and recorded in that
   owning file. Its approved values are **not restated here** — read them there.

   **Two blockers keep this precondition unmet:** (a) the **archive trigger**
   `[VERIFY]`; (b) the **preservation exception** `[VERIFY]`. Until both are
   answered, **Precondition 2 is NOT SATISFIED.** No retention period, deletion
   timing, archive duration, backup period or legal requirement is proposed here.
   Option C may be approved as an architecture direction while this remains partly
   settled; it may not be **implemented**.

   **Scope boundary — GAP-E02 is broader than this precondition. GAP-E02 remains
   Open `[VERIFY]`.** It is not resolved, narrowed or re-scoped by this record, and
   `validation/REPOSITORY_GAP_REGISTER.md` is not modified. Resolving blockers (a)
   and (b) would settle what **this precondition** requires; it would **not**
   necessarily resolve GAP-E02, which also retains unresolved retention governance
   for evidence **outside** the approved confidential-primary-evidence subset. The
   two must not be treated as equivalent in either direction.
3. A stable reference mechanism satisfying **R1–R7** is **approved**, including
   whether an evidence ID and an integrity value (R5) form part of it, and
   including how supersession (item 14) is handled.
4. If the reference mechanism requires new metadata fields, the corresponding
   change to `evidence/TEMPLATE_EVIDENCE_RECORD.md` is **separately approved** —
   this draft neither makes nor pre-authorises that change. The absent fields are
   listed in items 7, 8 and 15.
5. Whether `.gitignore` needs a PDF pattern is **separately decided**; this draft
   makes no such change.
6. The reviewer / approver role question (GAP-G01) is resolved, or the Owner
   explicitly approves as sole approver.
7. The placement question is resolved. **Partially settled — stated openly, not
   silently:** with the direction approved, this record is no longer an unapproved
   draft and is **eligible to remain in `decisions/`** (see the Placement note).
   Two parts remain open: how much rationale may accompany a decision record, and
   where **future** unapproved governance drafts belong (item 13). Both are
   `[VERIFY]`; neither is decided here.
8. This document is re-issued as an **approved** decision — or superseded — via
   `decisions/TEMPLATE_DECISION_RECORD.md`, which records approved decisions only.
   **Open.** This record is not built from that template. Whether an approved
   decision must be re-issued in the template's structure, or whether recording the
   approval in the existing document satisfies `decisions/README.md`, is
   undocumented — the decision lifecycle is itself an open `[VERIFY]` in that
   template's Known Limitations. `[VERIFY]`

**Until every precondition is met: Implementation Allowed = NO.**

---

## Gap Impact

**This decision resolves NO gap — including after the direction approval.**
Approving an architecture direction closes no documented gap. The following all
remain **open**, owned by their source files and indexed by
`validation/REPOSITORY_GAP_REGISTER.md`. **No gap status has changed**; where a
register row has since been re-pointed under separate approval (GAP-E02), that
changed the pointer only:

| Gap ID | Remains open | Owned by |
|--------|--------------|----------|
| GAP-C09 | Yes | `context/hour-budget-rules.md` → Known Limitations |
| GAP-C10 | Yes | `context/product-pause-rules.md` → Known Limitations |
| GAP-E03 | Yes | `evidence/README.md`; also `context/target-metrics.md` |
| GAP-E01 | Yes | `evidence/README.md` → Known Limitations |
| GAP-E02 | Yes | `evidence/README.md` → Evidence Retention Governance **and** Known Limitations |
| GAP-G01 | Yes | Repository-wide; consolidated in `validation/CONTEXT_REVIEW.md` |

`validation/REPOSITORY_GAP_REGISTER.md` is **not modified** by this document. No
gap status is changed. No gap text is restated — the table above carries Gap IDs
and pointers only.

### Coverage note — the central blocker has no owning Gap ID

The six gaps above remain relevant, but **none of them tracks the decision this
draft addresses.** Each owns something adjacent:

- **GAP-E01** owns the evidence **lifecycle** (import → reference → archival);
- **GAP-E02** owns **retention / archival period**;
- **GAP-E03** owns **specific cited-but-unfiled sources**;
- **GAP-C09 / GAP-C10** own unresolved `[VERIFY]` items **inside** two canonical
  rule files, including that each file's primary source is not confirmed filed;
- **GAP-G01** owns **undefined reviewer / approver roles**.

**The absence of an approved, durable storage-and-reference mechanism for
confidential binary primary evidence is not represented by any dedicated Gap ID in
`validation/REPOSITORY_GAP_REGISTER.md`.** None of the six should be read as fully
owning it. A reader consulting only the table above could otherwise conclude the
blocker is already under gap governance; it is not.

**POTENTIAL NEW GAP — recommendation only.** A reviewer should determine whether a
dedicated gap ought to be opened for the storage-and-reference question itself. **No
Gap ID is created here**, no gap is resolved, and the register is not edited. This
record only states that the coverage is absent.

**The direction approval makes this more material, not less.** There is now an
approved architecture direction whose enabling mechanism — the storage location and
the durable reference — is tracked by no gap ID. That is a reason to raise the
question with the Owner; it is **not** a reason to edit the register here, and the
register has not been edited.

**Metadata-schema support.** The record fields that a durable reference would
require but that `evidence/TEMPLATE_EVIDENCE_RECORD.md` does not provide — durable
storage/retrieval reference (R3), integrity/checksum and file size (R5),
confidentiality classification (R6), and evidence owner/steward (item 15) — are
recommended for classification **either as part of the same potential
storage/reference gap, or as a sub-item of it**, at the reviewer's determination. A
second, separate gap is **not** recommended merely for completeness.

---

## Queryability Test

A clean LLM or a new developer, reading only this file and following its
pointers, can answer:

| Question | Answerable? | Where |
|----------|-------------|-------|
| Why can confidential PDFs not simply be committed? | Yes | Current State #1, #3, #4, #9; Constraints 1, 8, 9; Option D — `CLAUDE.md` forbids creating binary files, `.gitignore` lists no PDF pattern, and a pushed commit has no documented removal path |
| Is the architecture direction approved? | Yes | **Yes** — Approval Record; header `Approval Status`; approved by Jathukulan, direction only |
| Is implementation approved? | Yes | **No** — header `Implementation Allowed: NO`; Approval Record; all eight Implementation Preconditions remain in force (3–6 and 8 OPEN; 1, 2 and 7 PARTIALLY SETTLED, none satisfied) |
| What storage class is confirmed? | Yes | Precondition 1 — Owner-Confirmed Storage Governance Facts |
| Is the exact location identifier known? | Yes | **No — `[VERIFY]`**; not supplied, none invented |
| Who is custodian, and does backup exist? | Yes | Owner-confirmed facts section — custodian recorded; backup/replication recorded as existing |
| Who has access, and how is it requested? | Yes | Owner-confirmed facts section — access list and request route recorded |
| Is the location company-controlled and workstation-independent? | Yes | Owner-confirmed facts section — both recorded, the second with its qualifier |
| Is confidential binary evidence explicitly permitted there? | Yes | **No — `[VERIFY]`**; must not be inferred from company control or class |
| Is the exact storage-confirmation date known? | Yes | **No — `[VERIFY]`**; Owner states before 2026-07-28, exact date not noted; no date inferred. **Provenance only — not a Precondition 1 closure condition** |
| What is Precondition 1's current state? | Yes | **PARTIALLY SETTLED** — Implementation Precondition 1; **two** attributes remain `[VERIFY]`: the official location identifier and the confidential-binary permission |
| Where are confidential binaries directed to live? | Yes | Decision section — an approved, non-Git, company-controlled location (Option C), at architecture level only |
| Is a specific location approved yet? | Yes | **No.** Approval Record; Current State #8; Known Unknowns 1–4; the "Deliberately not specified" list |
| Which state is operationally active now? | Yes | **Option E** — Approval Record; Owner / Review / Status; the interim state until every precondition is met |
| What is committed to Git instead? | Yes | Decision; Duplicate Truth Boundary — a committed metadata record carrying a stable reference; never the binary |
| Does metadata become business truth? | Yes | **No.** Current State #6; Duplicate Truth Boundary — traceability only, per `evidence/README.md` |
| Where do canonical rules remain? | Yes | Duplicate Truth Boundary — the Context layer (`context/`); this document restates none of them |
| What must be approved before implementation? | Yes | Implementation Preconditions 1–8 |
| What remains [VERIFY]? | Yes | **Known Unknowns / [VERIFY]** — that section is authoritative and states per item whether it is still open, partly answered or answered; **not all of items 1–15 are still open**. Also Stable Reference Requirements R3, R5, R6 and the checksum-schema note |
| Which gaps remain open? | Yes | Gap Impact — GAP-C09, GAP-C10, GAP-E03, GAP-E01, GAP-E02, GAP-G01; none resolved |
| Does an existing Gap ID own the storage/reference blocker? | Yes | **No** — Gap Impact → Coverage note; recorded as a POTENTIAL NEW GAP, recommendation only |
| What happens when evidence is superseded? | Yes | **Unresolved `[VERIFY]`** — Known Unknown 14; the question is documented, no policy is proposed |
| Who owns or stewards an individual evidence asset? | Yes | **Unresolved `[VERIFY]`** — Known Unknown 15; distinct from this decision's Owner |
| Does the metadata template support an owner/steward field? | Yes | **No dedicated field** — Known Unknown 15 |
| May storage be implemented before retention governance is resolved? | Yes | **No** — Implementation Precondition 2; retention governance owned by `evidence/README.md` → Evidence Retention Governance, indexed as GAP-E02 |
| What is Precondition 2's current state, and why? | Yes | **PARTIALLY SETTLED — not satisfied** — Implementation Precondition 2. It changed because retention governance for the confidential-primary-evidence subset relevant to this direction is now partly approved in `evidence/README.md`; the **archive trigger** and the **preservation exception** remain `[VERIFY]` |
| Does resolving Precondition 2's two blockers resolve GAP-E02? | Yes | **No** — Implementation Precondition 2 → Scope boundary. **GAP-E02 remains Open `[VERIFY]`** and is broader, also covering retention for evidence **outside** the approved confidential-primary-evidence subset |
| Who owns and who approved this record? | Yes | Owner / Review / Status — Owner Jathukulan; direction approved by Jathukulan as repository Owner; Reviewer `[VERIFY]` (GAP-G01); implementation approver `[VERIFY]`. Evidence ownership is a separate, open question (item 15) |

**Result: PASS**

---

## PASS / FAIL Checklist

- ✓ **One document** — **this record created, modified, moved, renamed or deleted
  no other file.** (Other repository files have since changed under their own
  separate Owner approvals; that is not this record's doing. See **Precondition 2**.)
  The filename is unchanged — `CLAUDE.md` forbids renaming, and no decision-record
  filename convention is defined.
- ✓ **Existing Asset First** — repository searched first; no existing decision or
  policy owns confidential-binary storage or evidence referencing, so no parallel
  decision was created.
- ✓ **No implementation** — **this document** moved or copied no PDF, created no
  evidence record, changed no evidence governance file, and made no
  `.gitignore` / `.gitattributes` / `CLAUDE.md` change. (Separately and under its
  own Owner approval, `evidence/README.md` was later changed to record retention
  governance — that was not done by, or authorised by, this record. See
  **Precondition 2**.)
- ✓ **No invented facts** — every current-state statement is grounded in the owning
  repository asset it cites, at the revision recorded for that section: the original
  **Current State / Evidence** table was read at commit `e52d3de`, and later
  additions cite the revision recorded for them in the **Revised** metadata entry.
  **No single universal review commit is claimed.** Nothing unanswered is filled in:
  host, directory, service, URL, evidence-ID syntax and checksum schema remain
  `[VERIFY]`, while storage-governance and retention-governance items answered since
  are owned by **Precondition 1** and by **Precondition 2** with
  `evidence/README.md`, and are referenced rather than restated.
- ✓ **No duplicate truth** — no business rule, KPI, threshold or gap definition is
  restated; owning files are referenced.
- ✓ **No gap resolved** — GAP-C09, GAP-C10, GAP-E03, GAP-E01, GAP-E02 and GAP-G01
  remain open; the Gap Register is untouched.
- ✓ **Approval status explicit and bounded** — ARCHITECTURE DIRECTION APPROVED —
  IMPLEMENTATION NOT APPROVED, stated in the header, the Approval Record, the
  Decision section and the Owner / Review / Status section. Implementation remains
  blocked; Option E remains the active interim state.
- ✓ **All eight implementation preconditions remain in force** — none has been
  fully resolved or waived. Preconditions **3–6 and 8 remain OPEN**.
  **Precondition 1 is PARTIALLY SETTLED**: the Owner-confirmed storage governance
  facts are recorded, while the official location identifier and the
  confidential-binary permission remain `[VERIFY]`. The exact confirmation date is
  also `[VERIFY]` but is provenance only, not a closure condition.
  **Precondition 2 is PARTIALLY SETTLED**: retention governance for the
  confidential-primary-evidence subset relevant to this direction is partly
  approved and owned by `evidence/README.md`, while the **archive trigger** and the
  **preservation exception** remain `[VERIFY]`. The precondition is **not
  satisfied**, and **GAP-E02 remains Open `[VERIFY]`** and broader in scope — it is
  neither resolved nor narrowed here.
  **Precondition 7 is PARTIALLY SETTLED**: the settled part is that this approved
  record is eligible to remain in `decisions/`; rationale volume, and the placement
  of future unapproved governance drafts, remain `[VERIFY]`.
- ✓ **Approval scope contained** — the direction is approved; **this record**
  approved, assigned or invented no location, provider, path, mechanism, evidence
  ID, checksum schema, classification schema, permissions model, retention rule,
  supersession rule or evidence owner, and resolved no `[VERIFY]`. Anything
  confirmed or partly approved since was done under separate Owner approval and is
  owned by **Precondition 1**, **Precondition 2** with `evidence/README.md`, or the
  **Known Unknowns / `[VERIFY]`** section.
- ✓ **Changes nothing in Amazon Ads** — this repository has no Amazon Ads
  connection and produces documents, not actions (`CLAUDE.md`).

**Output: PASS**
