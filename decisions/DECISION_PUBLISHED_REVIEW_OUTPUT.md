<!--
Governance decision record — CONCEPT DEFINED; NOTHING ELSE DECIDED.

This file records the Owner's canonical definition of the architectural concept
"Published Review Output". The CONCEPT is defined. NOTHING DOWNSTREAM OF IT IS
DECIDED: no storage location, no addressing scheme, no persistence rule, no
filename, no lifecycle, no retention, no implementation, and no change to any
skill, rule file, routing asset, validation asset or CLAUDE.md.

Defining a concept is not implementing it, and is not deciding where it lives.

This record does NOT redefine Phase 1b, Test 1, Test 2, marketplace routing,
authorisation, or Validation Status. Each remains owned exactly where it is owned
today.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, ratio, click gate, order count, price band, spend trigger, budget
figure, multiplier, efficiency value, evaluation window, rule tier or formula
appears anywhere in it, and none may be added. It contains NO routing matrix, NO
authorised-marketplace list and NO Test 2 availability matrix.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename
follows the DECISION_ prefix pattern already used by the sibling records in this
folder, and the path was specified by the Owner before creation. The status
inside this document, not the filename, is authoritative.
-->

# Decision — Published Review Output

**Concept defined: APPROVED. Storage, addressing, persistence, filenames,
lifecycle and implementation: NOT DEFINED — OPEN `[VERIFY]`.**

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — architectural concept definition |
| Approval Status | **DRAFT — awaiting Owner review** |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | `[VERIFY]` — not yet approved; this is a first draft |
| Decision Date | `[VERIFY]` — pending Owner approval |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-08-04 |
| Repository HEAD when created | **`0282167f42d4e49765494fd4376b0514bf5db337`** |
| Path | `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` — specified by the Owner before creation |
| Authoritative for | **The architectural concept "Published Review Output", and nothing else.** |
| Explicitly NOT authoritative for | Storage; addressing; persistence; filenames; repository location; lifecycle; retention; implementation; Validation Status; Phase 1b; Test 1; Test 2; marketplace routing; authorisation; any skill's own execution procedure; any PPC rule content. |
| Implementation Authorised By This Record | **NO** |
| Storage Defined By This Record | **NO** |
| Existing Files Modified By This Record | **NONE** |

---

## 1. Purpose

**This record gives the repository one canonical definition of the architectural
concept "Published Review Output", and does nothing else.**

**The business question it answers:**

> What is a "published review output", as that term is used in the approved
> Phase 1b skill-type architecture?

**Why a record is needed.** The approved Phase 1b skill-type architecture states
that Type 2 and Type 3 skills reference the originating skill's **published review
output only**. That rule names an object. **No repository asset defined what that
object is**, and no asset claimed to own it. A read-only architecture discovery
performed at HEAD `0282167f42d4e49765494fd4376b0514bf5db337` established the
absence and recommended that the concept be named and owned.

Under `CLAUDE.md` → *Queryability First*, a rule that refers to an undefined object
cannot be applied tomorrow: two tasks could reach opposite readings of what a Type 2
or Type 3 skill is permitted to reference, and each could cite governance.

**The Owner has now supplied the definition. It is new governance truth as of this
record.**

**How the gap was found.** The read-only architecture discovery **identified** that
no canonical concept existed. **It did not supply, derive or prove the definition**,
and it is not filed as a repository artefact. `[VERIFY]` — whether it should be
filed is not decided here.

**No external source consulted.** No Amazon Ads data was read, requested or filed.
No Amazon Ads connection exists.

---

## 2. Scope

**This record defines one architectural concept only.**

It settles what a Published Review Output **is**, what **"published"** means as an
architectural state, and **who owns the concept**.

It settles nothing about where a Published Review Output lives, how it is named,
how it is addressed, whether or how it persists, how long it is kept, or how any
skill implements it.

**Defining a concept is not implementing it, and is not deciding where it lives.**
Those are separate acts requiring separate Owner decisions, and only the first has
occurred here.

This record therefore does **not**:

- redefine Phase 1b;
- redefine Test 1;
- redefine Test 2;
- redefine marketplace routing;
- redefine authorisation;
- redefine Validation Status;
- prescribe implementation;
- prescribe storage;
- prescribe filenames;
- prescribe any repository location;
- prescribe addressing, identity, persistence, lifecycle or retention;
- modify any existing file;
- authorise any repository modification;
- resolve any existing `[VERIFY]`.

**It performs no file operation beyond its own creation.**

---

## 3. Definition — What a Published Review Output Is

**This section defines an architectural concept only. It defines no artefact
format, no file, no location and no mechanism.**

> **A Published Review Output is the completed result of a single skill's own
> action, in the state where that skill has finished that action and treats the
> result as final for that run.**

Four properties follow, and they are the whole of the definition:

1. **It belongs to exactly one skill — the originating skill.** It is that skill's
   own result, produced by that skill's own action, under that skill's own rules.
2. **It is complete for that run.** The originating skill has finished; it is not a
   partial, in-progress or working result.
3. **It is final as to that skill's action.** The originating skill does not intend
   to revise it further for that run.
4. **It is the only thing another skill may reference in place of performing that
   skill's work.**

**What it is not:**

- **It is not an artefact format.** No structure, template, schema, section list or
  field set is defined, prescribed or implied here.
- **It is not a file.** No file, path, folder or filename is defined, prescribed or
  implied here.
- **It is not a status.** It names a thing, not a state of evaluation.
- **It is not a report.** A report is a separate downstream product, owned by its
  existing owning records, and is not defined, described or changed here.
- **It is not evidence.** Evidence governance is owned elsewhere, is referenced by
  neither name nor path here, and is unchanged by this record.

**The shape of any given skill's output remains owned by that skill.** This record
neither restates, summarises, standardises nor constrains it. **No skill's output
structure is defined here, and none may be inferred from this record.**

---

## 4. Publication — What "Published" Means

**"Published" is an architectural state, not a storage mechanism.**

> **A review output is *published* when the originating skill has completed its own
> action and treats the result as final for that run — and is therefore in the state
> in which another skill may reference it.**

**Publication is a state, not an act performed on a location.** It describes the
condition the result is in. It does not describe writing, saving, filing, copying,
transmitting, committing or storing anything anywhere.

**What publication is NOT:**

- **Not storage.** Nothing about where a published review output resides is defined
  here. Publication does not require, imply or describe persistence of any kind.
- **Not a filing act.** No location, folder, path or filename is involved in
  reaching the published state.
- **Not human approval.** Approval remains a separate act, governed where it is
  already governed. A published review output remains a DRAFT result and is never,
  by virtue of being published, approved.
- **Not issuing a report to a recipient.** Publication in that reporting sense is a
  different act with a different meaning, owned by its existing owning records. It
  is neither defined, redefined nor affected here.
- **Not a validation verdict.** Publication says the originating skill has finished;
  it says nothing about what the result concluded. See **6**.

**Publication confers no authority.** A published review output is referenceable —
nothing more. It is not authoritative over any rule, any test, any marketplace or
any other skill's work.

---

## 5. Ownership

**Three separate statements. None implies another, and none may be collapsed into
another.**

### 5.1 — This decision owns only the concept

**This record owns the architectural concept "Published Review Output" — its
definition (**3**) and the meaning of "published" (**4**). That is the whole of what
it owns.**

It owns no instance, no artefact, no location, no format, no lifecycle and no
implementation. It is not the owner of any skill's output, and it never becomes one.

### 5.2 — Originating skills own their own published review outputs

**Each skill owns its own published review output** — its content, its structure,
its completeness, and the determination that its own action is finished for that
run.

That ownership is unchanged by this record. **No skill's output is transferred,
centralised, standardised or absorbed here**, and no skill's own execution procedure
is altered.

### 5.3 — Type 2 and Type 3 skills reference published review outputs only

**A Type 2 or Type 3 skill references an originating skill's published review output.
It does not own it, does not produce it, does not alter it, and does not re-derive
it.**

Referencing is consumption. It creates no ownership over what is referenced, and it
grants the referencing skill no authority over the originating skill's result.

**The skill types themselves, and which skill is of which type, are not defined
here.** They are owned by `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md`,
cited in **7** and never restated.

---

## 6. Relationship to Validation Status

**This record does NOT define Validation Status.**

`Validation Status` is an existing field, owned by each skill's own Decision Rules,
with meanings those skills already record. **Nothing here defines, redefines,
widens, narrows, standardises or reinterprets it**, and no status vocabulary is
created, extended or changed by this record.

**The relationship between Validation Status and Published Review Output remains an
OPEN `[VERIFY]` Owner decision.**

Specifically, and deliberately, this record does **not** decide:

- whether a review output can be published while its Validation Status records an
  incomplete or unresolved evaluation;
- whether any particular Validation Status value affects publication;
- whether publication affects Validation Status;
- whether the two concepts are related at all.

**No reconciliation between them is authorised by this record**, and none may be
performed on the strength of it. Any task that reconciles, aligns or couples the two
requires its own separate Owner decision.

**A caution, recorded so it is not mistaken for a decision.** That both concepts
concern a completed review does **not** make them the same concept, and does not
make either derivable from the other. **Neither is defined in terms of the other
here.**

---

## 7. Relationship to Existing Decisions

**Three records are referenced. Each continues to own its own subject in full. None
is amended, reinterpreted, narrowed or widened by this record.**

| Record | Continues to own |
|--------|------------------|
| `decisions/DECISION_PHASE_1B_DEFINITION.md` | **The definition of the term "Phase 1b".** Not redefined here. |
| `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` | **The Phase 1b skill types, their Test 1 relationships, their Test 2 relationships, and the confirmed and unresolved skill mappings.** Not redefined here. This record supplies the meaning of one term that record uses; it changes nothing that record decides. |
| `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` | **The Test 2 verification criterion.** Not redefined here, not restated, and not applied. |

**Where this record and any record above appear to disagree, the record above
wins.** This record states no skill classification, no test relationship, no
verification criterion and no phase definition.

---

## 8. Explicit Exclusions

**This decision does NOT define any of the following. Each remains OPEN
`[VERIFY]`.**

| # | Not defined | Status |
|---|-------------|--------|
| **M3** | **Storage** — where a published review output resides, or whether it resides anywhere | **OPEN `[VERIFY]`** |
| **M4** | **Addressing** — how a specific published review output is identified, named or referred to | **OPEN `[VERIFY]`** |
| — | **Persistence** — whether a published review output is retained at all, and in what form | **OPEN `[VERIFY]`** |
| — | **Filenames** — any naming pattern of any kind | **OPEN `[VERIFY]`** |
| **M5** | **Lifecycle** — currency, supersession, staleness, archival, retention | **OPEN `[VERIFY]`** |
| — | **Implementation** — how any skill consumes, produces or references a published review output | **OPEN `[VERIFY]`** |

**No location is chosen, proposed, reserved or implied by this record**, including
no folder, no path and no repository layer.

**No mechanism is designed.** No process, workflow, hand-off or interface between
skills is defined here.

**These exclusions are part of the decision, not commentary on it.** A later task
must not treat any of them as settled, as implied, or as derivable from the
definition in **3** or **4**.

---

## 9. Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the architectural concept "Published Review Output" —
its definition and the meaning of "published". That is new truth and exists nowhere
else in the repository.

**What it does NOT own, and never becomes:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window, rule tier or formula appears here. This is
  verifiable by reading the file: it contains none.
- **A second owner of any skill's output.** Each skill retains ownership of its own
  published review output; no output structure, template, field or section is
  restated, standardised or absorbed here.
- **A second Validation Status owner.** The field remains owned by each skill's own
  Decision Rules; their meanings are unchanged. See **6**.
- **A second Test 1 / routing owner.** No routing matrix, no authorised-marketplace
  list and no marketplace authorisation statement appears here.
- **A second Test 2 owner.** Neither the criterion nor any content-availability
  status is reproduced, and no marketplace / rule-family combination is classified.
- **A second owner of the Phase 1b skill types or mappings.** Those remain with the
  record cited in **7**.
- **A second owner of the term "Phase 1b".** That remains with the record cited in
  **7**.
- **A storage-governance owner.** No location, layer, folder, path or filename is
  defined or implied. See **8**.
- **An evidence-governance owner.** No evidence path, rule or convention is defined,
  restated or invented.
- **A status-vocabulary owner.** No status is created, widened, narrowed or
  redefined.
- **An authorisation owner.** Authorisation remains with `CLAUDE.md`.

**No existing `[VERIFY]` is resolved** by this record. No gap is created, closed or
narrowed; `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Known Limitations

Genuine unresolved governance items. None is worked around by inventing data.

1. **Storage, addressing, persistence, filenames, lifecycle and implementation are
   all undefined.** Every item in **8** remains open, and none may be inferred from
   this record. `[VERIFY]`
2. **The relationship between Validation Status and Published Review Output is
   undecided.** No reconciliation is authorised. See **6**. `[VERIFY]`
3. **No skill is modified by this record**, and no skill yet states that it produces
   or references a published review output in these terms. `[VERIFY]`
4. **Whether a published review output is ever persisted is not decided.** The
   definition in **3** is satisfied by a result that exists only for the duration of
   a run. Whether that is sufficient in practice is not determined here. `[VERIFY]`
5. **The architecture discovery that identified this gap is not filed** as a
   repository artefact, consistent with the treatment of prior read-only
   discoveries. `[VERIFY]`
6. **This record is not indexed in `validation/REPOSITORY_GAP_REGISTER.md`.**
   Whether the open items in **8** should be indexed there is a separate question for
   that register's own governance, and is not decided here. `[VERIFY]`
7. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
8. **Decision-record filename convention undefined** —
   `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
   here is descriptive, not conventional; the path was specified by the Owner before
   creation. `[VERIFY]`

---

## Review Requirement

**Owner review only.**

- **Owner:** Jathukulan — repository `Owner`.
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01). No reviewer is
  assigned or invented by this record.
- **What review means here:** confirming that the concept is defined as the Owner
  intends, that the exclusions in **8** hold, and that nothing beyond the concept has
  been decided. **Review approves no downstream work, because none is proposed.**

**This record is a DRAFT.** It carries no Owner approval and no decision date until
the Owner supplies them.

---

## Next Step

**One next action, and it is a decision, not implementation.**

Owner review of this draft, and — separately, and only if the Owner wishes — a
decision on the open items in **8**, and on the Validation Status relationship in
**6**.

Neither is made here, neither is pre-empted here, and **this record recommends no
implementation.**

---

## 10. Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one file created — this record; no existing file modified | **PASS** |
| 2 | No PPC business-rule value present | **PASS** |
| 3 | **M1** defined — what a Published Review Output is | **PASS** — **3** |
| 4 | **M2** defined — what "published" means, as an architectural state | **PASS** — **4** |
| 5 | **M6** defined — who owns the concept | **PASS** — **5** |
| 6 | **M3** (storage), **M4** (addressing) and **M5** (lifecycle) left OPEN `[VERIFY]` | **PASS** — **8** |
| 7 | Publication defined as a state, **not** a storage mechanism | **PASS** — **4** |
| 8 | Ownership stated as three separate statements | **PASS** — **5.1**, **5.2**, **5.3** |
| 9 | Validation Status **not** defined; its relationship recorded as OPEN `[VERIFY]`; no reconciliation authorised | **PASS** — **6** |
| 10 | Exactly three existing decision records referenced in **7**, each left owning its own subject | **PASS** — **7** |
| 11 | Phase 1b, Test 1, Test 2, marketplace routing and authorisation **not** redefined | **PASS** — **2**, **7**, **9** |
| 12 | No implementation described; no storage, filename or repository location prescribed | **PASS** — **2**, **8** |
| 13 | No artefact format, template, schema or field set defined | **PASS** — **3** |
| 14 | No new status vocabulary created | **PASS** — **6**, **9** |
| 15 | No existing `[VERIFY]` resolved; Gap Register untouched | **PASS** — **9** |
| 16 | Draft status recorded honestly — not presented as Owner Approved | **PASS** — Metadata; Review Requirement |

**Result: PASS** — concept defined; nothing downstream decided.

---

## Queryability Test

Using only this record and the paths it references, can another LLM answer:

| # | Question | Answerable? | Answer / Where |
|---|----------|-------------|----------------|
| 1 | What is a Published Review Output? | Yes | The completed result of a single skill's own action, final for that run — **3** |
| 2 | Which skill does one belong to? | Yes | Exactly one — the originating skill — **3**, **5.2** |
| 3 | Is it a file? | Yes | **No** — **3** |
| 4 | Is a format or template defined? | Yes | **No** — **3** |
| 5 | What does "published" mean? | Yes | An architectural state: the originating skill has finished and treats the result as final for that run — **4** |
| 6 | Is "published" a storage act? | Yes | **No** — **4** |
| 7 | Does publication mean human approval? | Yes | **No** — **4** |
| 8 | Does publication mean a report was issued? | Yes | **No** — a different act, owned elsewhere — **4** |
| 9 | Who owns the concept? | Yes | **This record**, and only the concept — **5.1** |
| 10 | Who owns an individual published review output? | Yes | The originating skill — **5.2** |
| 11 | What may a Type 2 or Type 3 skill do with one? | Yes | Reference it only — **5.3** |
| 12 | Does referencing create ownership? | Yes | **No** — **5.3** |
| 13 | Where is a published review output stored? | Yes | **Not defined — OPEN `[VERIFY]`** — **8** |
| 14 | How is a specific one identified? | Yes | **Not defined — OPEN `[VERIFY]`** — **8** |
| 15 | How long is one kept? | Yes | **Not defined — OPEN `[VERIFY]`** — **8** |
| 16 | Does this record define Validation Status? | Yes | **No** — **6** |
| 17 | How do Validation Status and Published Review Output relate? | Yes | **Undecided — OPEN `[VERIFY]` Owner decision; no reconciliation authorised** — **6** |
| 18 | Does this redefine Phase 1b, Test 1, Test 2, routing or authorisation? | Yes | **No** — **2**, **7** |
| 19 | Which records own the Phase 1b skill types? | Yes | `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` — **7** |
| 20 | Which record owns the Test 2 criterion? | Yes | `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` — **7** |
| 21 | Does this authorise implementation? | Yes | **No** — **2**, **8**; Metadata |
| 22 | Does this record contain any PPC value? | Yes | **No** — **9** |
| 23 | Is this record approved? | Yes | **No — DRAFT**, awaiting Owner review — Metadata; Review Requirement |
| 24 | What is the next action? | Yes | Owner review of this draft — Next Step |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** `[VERIFY]` — not yet approved
- **Decision Date:** `[VERIFY]` — pending Owner approval
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** **DRAFT — awaiting Owner review**
- **Repository HEAD when created:** `0282167f42d4e49765494fd4376b0514bf5db337`
- **Authoritative for:** the architectural concept "Published Review Output" only
- **Existing files modified by this task:** **NONE**
- **Skills modified:** **NO**
- **Rule files modified:** **NO**
- **Registry modified:** **NO**
- **Validation assets modified:** **NO**
- **`CLAUDE.md` modified:** **NO**
- **Storage defined:** **NO**
- **Addressing defined:** **NO**
- **Persistence defined:** **NO**
- **Lifecycle defined:** **NO**
- **Implementation authorised:** **NO**
- **Validation Status defined:** **NO**
- **Evidence filed by this task:** **NO**
- **`[VERIFY]` items resolved by this task:** **NONE**
- **Gap Register modified:** **NO**

---

## Safety Boundary

Per `CLAUDE.md`:

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

Naming a concept changes what a skill may **refer to**. It changes nothing about
what a skill is permitted to **do**. Every skill output remains an evidence-backed
DRAFT recommendation only. Amazon Ads changes remain human reviewed and human
executed, applied manually by Jathukulan.

This record is documentation. It performs no Amazon Ads action, holds no
credentials, and produces no recommendation to act. No Amazon Ads connection exists
in this repository.
