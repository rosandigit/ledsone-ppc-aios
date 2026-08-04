<!--
Governance decision record — TERM DEFINED; NOTHING ELSE DECIDED.

This file records the Owner's canonical definition of the architectural concept
"Originating Skill". The CONCEPT is defined. NOTHING DOWNSTREAM OF IT IS DECIDED:
no skill is identified as originating, no skill is determined to produce a
Published Review Output, no publication granularity, no carrier, no addressing,
no storage, no lifecycle, no Validation Status relationship, no implementation,
no repository structure, no schema, no identity scheme, no output template, and
no automation.

Defining a role is not deciding who occupies it.

This record does NOT redefine Published Review Output, the Phase 1b skill types
and mappings, the Test 2 verification criterion, or the term "Phase 1b". Each
remains owned exactly where it is owned today, and each is referenced by path
only.

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

# Decision — Originating Skill

**Concept defined. Which skills qualify, which skills produce, and everything
downstream: NOT DECIDED — OPEN `[VERIFY]`.**

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
| Repository HEAD when created | **`696d47cea822759241110b28f68649e96458577f`** |
| Path | `decisions/DECISION_ORIGINATING_SKILL.md` — specified by the Owner before creation |
| Authoritative for | **The architectural concept "Originating Skill", and nothing else.** |
| Explicitly NOT authoritative for | Which skills qualify as originating; which skills produce a Published Review Output; publication granularity; carrier; addressing; storage; persistence; lifecycle; Validation Status; implementation; repository structure; schema; identity; output templates; automation; Published Review Output; the Phase 1b skill types and mappings; the Test 2 verification criterion; the term "Phase 1b". |
| Skills Identified As Originating By This Record | **NONE** |
| Production Determined By This Record | **NO** |
| Implementation Authorised By This Record | **NO** |
| Existing Files Modified By This Record | **NONE** |

---

## 1. Purpose

**This record gives the repository one canonical definition of the architectural
concept "Originating Skill", and does nothing else.**

**The business question it answers:**

> What is an "originating skill", as that term is used by committed governance?

**Why this decision exists.** Committed governance places an obligation on
referencing skills that is expressed in terms of an *originating skill*. That
obligation therefore depends on the term having a determinate meaning. **No
committed record supplies one.**

Under `CLAUDE.md` → *Queryability First*, an obligation stated in terms of an
undefined role cannot be applied tomorrow: two tasks could reach opposite readings
of what the role names, and each could cite governance. Under `CLAUDE.md` → *No
Duplicate Truth*, the meaning must live in exactly one place — and today it lives
in none.

**This record supplies the meaning of the role. It does not decide who occupies
it.**

**How the gap was found.** A read-only governance verification performed at HEAD
`696d47cea822759241110b28f68649e96458577f` established that the term is used by
committed governance and defined nowhere. **That verification identified the gap.
It did not supply, derive or prove the definition**, and it is not filed as a
repository artefact. `[VERIFY]` — whether it should be filed is not decided here.

**No external source consulted.** No Amazon Ads data was read, requested or filed.
No Amazon Ads connection exists.

---

## 2. Problem Statement

**Stated from repository evidence only. No speculation.**

**The term is used by committed governance.** It appears in
`decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` and in
`decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md`. Both records are committed. The
first is Owner Approved; the second is committed carrying `Approval Status: DRAFT
— awaiting Owner review`.

**The term is defined by no committed record.** Neither of those records, nor
`decisions/DECISION_PHASE_1B_DEFINITION.md`, nor
`decisions/DECISION_TEST2_VERIFICATION_CRITERION.md`, states what an originating
skill is. None claims to own the question, and none appears in another's
*Authoritative for* statement as owning it.

**No skill is designated as one.** No committed record names any skill as an
originating skill.

**That is the whole of the problem.** This record makes no claim about why the
term went undefined, about what any author intended, or about what the term ought
to have meant before now. **Repository silence is recorded as silence, and is not
converted into governance.**

---

## 3. Definition — What an Originating Skill Is

**This section defines an architectural concept only. It identifies no skill, no
skill type, and no production behaviour.**

> **An Originating Skill is the role occupied, in relation to one particular
> Published Review Output, by the single skill whose own action produced that
> output.**

Three properties follow, and they are the whole of the definition:

1. **It is a role, not a category of skill.** "Originating skill" describes a
   position held in relation to a particular Published Review Output. It is not a
   permanent attribute of any skill, not a classification, and not a property
   recorded in any skill file.
2. **The role is held in relation to one Published Review Output at a time.**
   Occupying the role in relation to one output establishes nothing about any
   other output.
3. **The role is not transferable.** A skill that references a Published Review
   Output does not thereby occupy the originating role for it. Referencing and
   originating are different positions and are never the same position.

**What this definition does not do:**

- **It identifies no skill.** No current, future or hypothetical skill is named,
  designated, qualified or disqualified here.
- **It identifies no skill type.** No skill type is named as originating or as
  not originating.
- **It decides no production.** Whether any given skill produces a Published
  Review Output is a separate question, not answered here. See **6** and **8**.
- **It states no property of a Published Review Output.** That a Published Review
  Output belongs to exactly one skill is owned by
  `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` and is **cited, never
  restated**. This record names the role; that record owns the output.

**A boundary, recorded so it is not mistaken for a decision.** Defining the role
does not establish that the role is occupied by anything today. **A defined role
with no identified occupant is the intended state of this record**, and no
occupant may be inferred from the definition above.

---

## 4. Architectural Relationship

**This section states direction only. It redefines none of the three concepts it
places in order, and each remains owned where it is owned today.**

```
Originating Skill
        ↓   occupies the originating role in relation to
Published Review Output
        ↓   is referenced by
Referencing skills
```

**Reading the relationship, one step at a time:**

- **Originating Skill → Published Review Output.** The role is defined *by* the
  relation to the output. There is no originating skill in the abstract; there is
  only an originating skill *of* some particular Published Review Output.
- **Published Review Output → Referencing skills.** A Published Review Output may
  be referenced. **Which skills reference, and under what obligation, is owned by
  `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md`** and is neither restated
  nor extended here.
- **The relation is directional and does not reverse.** Referencing does not
  originate. The referencing position never becomes the originating position.

**What the relationship is not:**

- **It is not a workflow.** No sequence, hand-off, trigger, interface or process
  between skills is defined, described or implied.
- **It is not a dependency rule.** Nothing here states that any skill must run
  before, after, or at all in relation to any other.
- **It is not a production rule.** The arrow from Originating Skill to Published
  Review Output describes the relation that defines the role. **It does not state
  that any particular skill stands at its tail.**

---

## 5. Ownership

**This decision owns ONLY: Originating Skill** — the architectural concept
defined in **3** and the directional relation stated in **4**. That is the whole
of what it owns.

It owns no skill, no occupant of the role, no production determination, and
nothing downstream of the concept.

**Everything else remains owned exactly where it is owned today:**

| Not owned here | Owned by |
|----------------|----------|
| **Published Review Output** | `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` |
| **Skill Classification** — the Phase 1b skill types, their Test 1 and Test 2 relationships, and the confirmed and unresolved skill mappings | `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` |
| **Test 2 — the verification criterion** | `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` |
| **The term "Phase 1b"** | `decisions/DECISION_PHASE_1B_DEFINITION.md` |
| **Each skill's own execution procedure and its own output** | That skill's own file in `skills/` |
| **Authorisation** | `CLAUDE.md` |

**On any conflict, the owner named above wins.** This record states no skill
classification, no output property, no verification criterion, no phase
definition, no business rule and no authorisation.

---

## 6. Explicit Exclusions

**This decision does NOT determine any of the following.**

| # | Not determined | Status |
|---|----------------|--------|
| 1 | **Which skills qualify** as originating skills | **OPEN `[VERIFY]`** |
| 2 | **Which skills produce** a Published Review Output | **OPEN `[VERIFY]`** |
| 3 | **Publication granularity** — what one Published Review Output covers | **OPEN `[VERIFY]`** |
| 4 | **Carrier** — the surface on which a Published Review Output exposes anything | **OPEN `[VERIFY]`** |
| 5 | **Addressing (M4)** | **OPEN `[VERIFY]`** |
| 6 | **Storage (M3)** | **OPEN `[VERIFY]`** |
| 7 | **Validation Status**, and its relationship to a Published Review Output | **OPEN `[VERIFY]`** |
| 8 | **Implementation** — how any skill occupies, produces, exposes or references anything | **OPEN `[VERIFY]`** |
| 9 | **Repository structure** — no folder, path, layer or location | **OPEN `[VERIFY]`** |

Also not determined, and not defined anywhere in this record: **persistence**,
**lifecycle**, **filenames**, **schema**, **identity**, **output templates** and
**automation**.

**These exclusions are part of the decision, not commentary on it.** A later task
must not treat any of them as settled, as implied, or as derivable from **3** or
**4**.

**In particular: no skill becomes an originating skill by virtue of this
record**, and no skill is excluded from the role by it either.

---

## 7. Relationship to Existing Decisions

**Four records are referenced. Each continues to own its own subject in full.
None is amended, reinterpreted, narrowed, widened or reopened by this record, and
none is restated here.**

| Record | Continues to own | This record's relation to it |
|--------|------------------|------------------------------|
| `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` | Published Review Output — the concept, the meaning of "published", and the ownership model | Cited. This record names a role defined *in relation to* that concept; it states no property of it. |
| `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` | The Phase 1b skill types, their Test 1 and Test 2 relationships, and the confirmed and unresolved skill mappings | Cited. This record supplies the meaning of one term that record uses. **It changes nothing that record decides, and reopens nothing.** |
| `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` | The Test 2 verification criterion | Cited. Not restated, not applied, not affected. |
| `decisions/DECISION_PHASE_1B_DEFINITION.md` | The definition of the term "Phase 1b" | Cited. Not restated, not affected. |

**Where this record and any record above appear to disagree, the record above
wins.**

**A dependency, recorded rather than resolved.**
`decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` is committed carrying `Approval
Status: DRAFT — awaiting Owner review`, with `Approved By` and `Decision Date`
both `[VERIFY]`. This record's **3** and **4** are stated in relation to the
concept that record owns. **Whether that record is approved is not decided here**,
and this record claims no approval on its behalf. `[VERIFY]`

---

## 8. Open Items

**Every item below is OPEN `[VERIFY]`. None is decided, narrowed, or resolved by
implication anywhere in this record.**

| # | Open item | Status |
|---|-----------|--------|
| 1 | **Which existing skills qualify as originating skills** | **OPEN `[VERIFY]`** |
| 2 | **Which existing skills produce a Published Review Output** | **OPEN `[VERIFY]`** |
| 3 | **Publication Granularity** | **OPEN `[VERIFY]`** |
| 4 | **Carrier** | **OPEN `[VERIFY]`** |
| 5 | **Addressing (M4)** | **OPEN `[VERIFY]`** |
| 6 | **Storage (M3)** | **OPEN `[VERIFY]`** |
| 7 | **The Validation Status relationship** | **OPEN `[VERIFY]`** |

**Items 3 to 7 are not owned by this record and are not this record's to close.**
Items 3 to 6 and item 7 are recorded here **as open, by reference only** — their
own governance sits with whichever record does or will own them, and listing them
creates no ownership here.

**No existing `[VERIFY]` anywhere in the repository is resolved by this record.**

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the architectural concept "Originating Skill" — the
role defined in **3** and the directional relation in **4**. That is new truth and
exists nowhere else in the repository.

**What it does NOT own, and never becomes:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window, rule tier or formula appears here. This is
  verifiable by reading the file: it contains none.
- **A second Published Review Output owner.** No property, definition, publication
  meaning or ownership statement from that record is reproduced, paraphrased or
  reinterpreted.
- **A second Skill Classification owner.** No skill type, no Test 1 relationship,
  no Test 2 relationship and no skill mapping is reproduced, and no mapping is
  added, removed or altered.
- **A second Test 2 owner.** The criterion is not restated, not applied, and no
  marketplace / rule-family combination is classified.
- **A second owner of the term "Phase 1b".**
- **A second Test 1 / routing owner.** No routing matrix, no
  authorised-marketplace list and no marketplace authorisation statement appears
  here.
- **An owner of any skill's output, output template or execution procedure.** Each
  skill retains its own; none is restated, standardised or absorbed.
- **A production owner.** No skill is determined to produce anything.
- **A granularity, carrier, addressing, storage, persistence or lifecycle owner.**
- **A Validation Status owner.** No status is created, widened, narrowed or
  redefined.
- **A repository-structure owner.** No folder, path, layer or location is defined
  or implied.
- **An authorisation owner.** Authorisation remains with `CLAUDE.md`.

**No existing `[VERIFY]` is resolved** by this record. No gap is created, closed
or narrowed; `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Known Limitations

Genuine unresolved governance items. None is worked around by inventing data.

1. **The role has no identified occupant.** No skill is named as an originating
   skill, and none may be inferred from **3** or **4**. `[VERIFY]`
2. **Production remains undetermined.** Whether any skill produces a Published
   Review Output is not decided here. `[VERIFY]`
3. **This record depends on a record that is not Owner-approved.**
   `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` is committed as `DRAFT —
   awaiting Owner review`. See **7**. `[VERIFY]`
4. **This record is itself a DRAFT.** It carries no Owner approval and no decision
   date. `[VERIFY]`
5. **No skill is modified by this record**, and no skill states that it occupies
   the originating role. `[VERIFY]`
6. **Every item in 8 remains open**, and none is narrowed by this record.
   `[VERIFY]`
7. **The governance verification that identified this gap is not filed** as a
   repository artefact, consistent with the treatment of prior read-only
   discoveries. `[VERIFY]`
8. **This record is not indexed in `validation/REPOSITORY_GAP_REGISTER.md`.**
   Whether it should be is a separate question for that register's own governance,
   and is not decided here. `[VERIFY]`
9. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
10. **Decision-record filename convention undefined** —
    `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
    here is descriptive, not conventional; the path was specified by the Owner
    before creation. `[VERIFY]`

---

## Review Requirement

**Owner review only.**

- **Owner:** Jathukulan — repository `Owner`.
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01). No reviewer is
  assigned or invented by this record.
- **What review means here:** confirming that the role is defined as the Owner
  intends, that the exclusions in **6** hold, and that nothing beyond the concept
  has been decided. **Review approves no downstream work, because none is
  proposed.**

**This record is a DRAFT.** It carries no Owner approval and no decision date
until the Owner supplies them.

---

## Next Step

**One next action, and it is a decision, not implementation.**

Owner review of this draft.

Everything in **8** remains a separate matter for its own decision. None is made
here, none is pre-empted here, and **this record recommends no implementation.**

---

## Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one file created — this record; no existing file modified | **PASS** |
| 2 | No PPC business-rule value present | **PASS** |
| 3 | "Originating Skill" defined as an architectural concept | **PASS** — **3** |
| 4 | Its architectural purpose stated | **PASS** — **1**, **4** |
| 5 | Its relationship to a Published Review Output stated, without redefining it | **PASS** — **4** |
| 6 | **No current skill identified** as originating | **PASS** — **3**, **6**, **8** |
| 7 | **No skill type identified** as originating | **PASS** — **3** |
| 8 | **No production determined** | **PASS** — **3**, **6**, **8** |
| 9 | Publication granularity, carrier, addressing, storage, Validation Status, implementation and repository structure all left OPEN `[VERIFY]` | **PASS** — **6**, **8** |
| 10 | Published Review Output, Skill Classification, Test 2 and "Phase 1b" each left with their existing owners, unrestated | **PASS** — **5**, **7** |
| 11 | No existing decision reopened | **PASS** — **7** |
| 12 | No schema, identity, output template, lifecycle, persistence, filename or automation defined | **PASS** — **6** |
| 13 | Repository silence recorded as silence, not converted into governance | **PASS** — **2** |
| 14 | No new status vocabulary created | **PASS** |
| 15 | No existing `[VERIFY]` resolved; Gap Register untouched | **PASS** — Duplicate Truth Prevention |
| 16 | Draft status recorded honestly — not presented as Owner Approved | **PASS** — Metadata; Review Requirement |

**Result: PASS** — role defined; nothing downstream decided.

---

## Queryability Test

Using only this record and the paths it references, can another LLM answer:

| # | Question | Answerable? | Answer / Where |
|---|----------|-------------|----------------|
| 1 | What is an Originating Skill? | Yes | The role occupied, in relation to one particular Published Review Output, by the single skill whose own action produced it — **3** |
| 2 | Is it a category of skill? | Yes | **No — it is a role** — **3**, property 1 |
| 3 | Is it a permanent attribute of a skill? | Yes | **No** — **3**, properties 1 and 2 |
| 4 | Can a referencing skill become the originating skill? | Yes | **No** — **3**, property 3; **4** |
| 5 | Which current skills are originating skills? | Yes | **Not determined — OPEN `[VERIFY]`** — **6**, **8** |
| 6 | Which current skills produce a Published Review Output? | Yes | **Not determined — OPEN `[VERIFY]`** — **6**, **8** |
| 7 | Is any skill type named as originating? | Yes | **No** — **3**, **6** |
| 8 | What is the architectural relationship? | Yes | Originating Skill → Published Review Output → Referencing skills — **4** |
| 9 | Does that relationship define a workflow? | Yes | **No** — **4** |
| 10 | Does it state that any particular skill produces an output? | Yes | **No** — **4** |
| 11 | Who owns Published Review Output? | Yes | `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` — **5**, **7** |
| 12 | Who owns Skill Classification? | Yes | `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` — **5**, **7** |
| 13 | Who owns Test 2? | Yes | `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` — **5**, **7** |
| 14 | Who owns the term "Phase 1b"? | Yes | `decisions/DECISION_PHASE_1B_DEFINITION.md` — **5**, **7** |
| 15 | Does this record define publication granularity? | Yes | **No — OPEN `[VERIFY]`** — **6**, **8** |
| 16 | Does it define a carrier, addressing or storage? | Yes | **No — all OPEN `[VERIFY]`** — **6**, **8** |
| 17 | Does it define Validation Status or its relationship? | Yes | **No — OPEN `[VERIFY]`** — **6**, **8** |
| 18 | Does it authorise implementation? | Yes | **No** — **6**; Metadata |
| 19 | Does it define repository structure, schema or identity? | Yes | **No** — **6** |
| 20 | Does it reopen any existing decision? | Yes | **No** — **7** |
| 21 | Does it contain any PPC value? | Yes | **No** — Duplicate Truth Prevention |
| 22 | Is this record approved? | Yes | **No — DRAFT**, awaiting Owner review — Metadata; Review Requirement |
| 23 | Does it depend on an unapproved record? | Yes | **Yes** — `DECISION_PUBLISHED_REVIEW_OUTPUT.md` is DRAFT — **7**; Known Limitations 3 |
| 24 | What is the next action? | Yes | Owner review of this draft — Next Step |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** `[VERIFY]` — not yet approved
- **Decision Date:** `[VERIFY]` — pending Owner approval
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** **DRAFT — awaiting Owner review**
- **Repository HEAD when created:** `696d47cea822759241110b28f68649e96458577f`
- **Authoritative for:** the architectural concept "Originating Skill" only
- **Existing files modified by this task:** **NONE**
- **Skills modified:** **NO**
- **Skills identified as originating:** **NONE**
- **Production determined:** **NO**
- **Publication granularity determined:** **NO**
- **Carrier determined:** **NO**
- **Addressing determined:** **NO**
- **Storage determined:** **NO**
- **Validation Status determined:** **NO**
- **Implementation authorised:** **NO**
- **Repository structure defined:** **NO**
- **Rule files modified:** **NO**
- **Registry modified:** **NO**
- **Validation assets modified:** **NO**
- **`CLAUDE.md` modified:** **NO**
- **Existing decisions reopened:** **NONE**
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

Naming a role changes what governance can **refer to**. It changes nothing about
what a skill is permitted to **do**. Every skill output remains an evidence-backed
DRAFT recommendation only. Amazon Ads changes remain human reviewed and human
executed, applied manually by Jathukulan.

This record is documentation. It performs no Amazon Ads action, holds no
credentials, and produces no recommendation to act. No Amazon Ads connection
exists in this repository.
