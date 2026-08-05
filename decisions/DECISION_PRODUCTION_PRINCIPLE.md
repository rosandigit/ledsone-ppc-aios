<!--
Governance decision record — PRINCIPLE DECIDED; NOTHING ELSE DECIDED.

This file records the Owner's approved Production Principle for Phase 1b. The
PRINCIPLE is decided. NOTHING DOWNSTREAM OF IT IS DECIDED: no skill is determined
to produce a Published Review Output, no individual skill is addressed, no
production status is established, no publication granularity, no carrier, no
addressing, no storage, no filenames, no lifecycle, no implementation, no
routing, and no marketplace behaviour.

Deciding whether completion constitutes production is not deciding who produces.

This record does NOT redefine Published Review Output, Originating Skill, the
Phase 1b skill types and mappings, the Test 2 verification criterion, or the term
"Phase 1b". Each remains owned exactly where it is owned today, and each is
referenced by path only.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, ratio, click gate, order count, price band, spend trigger, budget
figure, multiplier, efficiency value, evaluation window, rule tier or formula
appears anywhere in it, and none may be added. It contains NO routing matrix, NO
authorised-marketplace list and NO Test 2 availability matrix. No individual
skill is named anywhere in this record.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename
follows the DECISION_ prefix pattern already used by the sibling records in this
folder, and the path was specified by the Owner before creation. The status
inside this document, not the filename, is authoritative.
-->

# Decision — Production Principle

**Principle decided. Which skills produce, and everything downstream: NOT
DECIDED — OPEN `[VERIFY]`.**

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — architectural principle |
| Approval Status | **OWNER APPROVED — the principle in §3 only.** The text of this record has not yet been Owner-reviewed. |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | **Jathukulan — repository Owner** |
| Decision Date | **2026-08-04** |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-08-04 |
| Repository HEAD when created | **`3b570a668468f21d03193722b33beabe0858e7b0`** |
| Path | `decisions/DECISION_PRODUCTION_PRINCIPLE.md` — specified by the Owner before creation |
| Authoritative for | **The Production Principle, and nothing else.** |
| Explicitly NOT authoritative for | Which skills produce a Published Review Output; any individual skill; any skill's production status; publication granularity; carrier; addressing; storage; filenames; persistence; lifecycle; implementation; routing; marketplace behaviour; Published Review Output; Originating Skill; the Phase 1b skill types and mappings; the Test 2 verification criterion; the term "Phase 1b". |
| Skills Determined To Produce By This Record | **NONE** |
| Individual Skills Addressed By This Record | **NONE** |
| Implementation Authorised By This Record | **NO** |
| Existing Files Modified By This Record | **NONE** |

---

## 1. Purpose

**This record gives the repository one canonical Production Principle, and does
nothing else.**

**The architectural question it answers:**

> When a skill completes its own defined artefact, does that completion itself
> mean the skill has produced a Published Review Output — or is production a
> separate governance determination made by the Owner?

**Why this record exists.** Committed governance places an obligation on
referencing skills that is expressed in terms of a Published Review Output
produced by an originating skill. Both of those concepts are defined by their own
records. **The step between them is not.** Nothing states whether a skill arrives
at production simply by finishing what it already does, or whether production is
something the Owner separately determines.

Under `CLAUDE.md` → *Queryability First*, that step cannot be left to the reader:
two tasks could reach opposite conclusions about whether any given skill produces
a Published Review Output, and each could cite governance. Under `CLAUDE.md` → *No
Duplicate Truth*, the answer must live in exactly one place — and before this
record it lived in none.

**This record supplies the principle. It does not apply it.**

---

## 2. Problem Statement

**The repository already defines two of the three concepts involved.**

- **Published Review Output** is defined, and its definition is owned by
  `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md`.
- **Originating Skill** is defined, and its definition is owned by
  `decisions/DECISION_ORIGINATING_SKILL.md`.

Neither is restated here; both are referenced by path only. See **5**.

**The repository does not define the step between artefact completion and
production.**

Every skill states, in its own vocabulary, what it produces when it finishes.
**No record states whether completing that artefact is itself production of a
Published Review Output.** The two readings are:

- **Reading one —** completion is production. A skill that finishes its own
  artefact has, by that act, produced a Published Review Output.
- **Reading two —** completion is not production. Production is a separate
  determination, and finishing an artefact establishes nothing about it.

**Both readings are available from committed governance, and no committed record
selects between them.** Until one is selected, the obligation placed on
referencing skills has no determinate subject, because whether anything has been
produced for them to reference cannot be answered.

**This record makes no claim about why the step went undefined**, about what any
author intended, or about what the answer ought to have been before now.
**Repository silence is recorded as silence, and is not converted into
governance.**

---

## 3. Owner Decision — The Production Principle

**This is an Owner governance decision.** It was supplied and approved by
Jathukulan, repository Owner, on 2026-08-04. **It is not derived from repository
evidence, is not inferred from any committed record, and is not presented as
derived.** It is new governance truth as of this record.

**Approved:**

> **Completion of a skill's own defined artefact does NOT itself constitute
> production of a Published Review Output.**
>
> **Repository evidence informs a production determination.**
>
> **Repository evidence alone does NOT determine production.**
>
> **Production is a separate governance determination, made by the Owner.**

**Three consequences follow, and they are part of the principle:**

1. **No skill produces a Published Review Output by virtue of completing its own
   artefact.** Finishing an artefact and producing a Published Review Output are
   different facts, and the first never establishes the second.
2. **Production is never established by inference.** It is not established by
   artefact completion, by a skill's own description of its output, by a skill
   type, by an architectural relationship, by a routing position, or by the
   absence of a statement to the contrary.
3. **Each production determination requires its own Owner decision.** Where no
   such decision exists, production is **undetermined** — not absent, and not
   present.

**Undetermined is not a verdict.** That production has not been determined for
something does not mean it has been determined negatively. The existing
repository-wide handling for an unanswered question applies, and **no new status
vocabulary is created by this record.**

**This principle is authoritative.**

---

## 4. Production Principle

### What this principle governs

**The relationship between artefact completion and production, in general.**

It settles one thing: that the first does not entail the second, and that
production is separately determined by the Owner. It applies to that relationship
wherever it arises, without exception and without regard to which skill is
involved.

### What this principle does not govern

**It governs no skill.** It makes no determination about any skill, and no skill
is named anywhere in this record.

**It governs no production determination.** It states that production requires an
Owner decision; it makes none, and it prescribes no form, procedure, criterion,
sequence or evidence standard for making one.

**It governs nothing downstream of production.** Publication granularity, carrier,
addressing, storage, filenames, persistence, lifecycle, implementation, routing
and marketplace behaviour are all outside it. See **6**.

**Deciding a principle is not applying it.** The two are separate acts requiring
separate Owner decisions, and only the first has occurred here.

**This record performs no file operation beyond its own creation, and resolves no
existing `[VERIFY]`.**

---

## 5. Relationship to Existing Decisions

**Five records are referenced. Each continues to own its own subject in full.
None is amended, reinterpreted, narrowed, widened or reopened by this record, and
none is restated here.**

| Record | Continues to own | This record's relation to it |
|--------|------------------|------------------------------|
| `decisions/DECISION_PHASE_1B_DEFINITION.md` | The definition of the term "Phase 1b" | Cited. **The term is not redefined, narrowed or widened here.** This record states a principle that arises within Phase 1b; it does not state what Phase 1b is. |
| `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` | The Phase 1b skill types, their Test 1 and Test 2 relationships, and the confirmed and unresolved skill mappings | Cited. **No type, relationship or mapping is reproduced, added, removed or altered.** A skill's type is not a production determination under **3**, and this record changes nothing that record decides. |
| `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` | Published Review Output — the concept, the meaning of "published", and the ownership model | Cited. This record states when something is *produced*; that record states what the thing *is*. **No property of it is stated here.** |
| `decisions/DECISION_ORIGINATING_SKILL.md` | Originating Skill — the role, and its directional relation to a Published Review Output | Cited. This record states that occupying no role follows from artefact completion; that record states what the role is. **No property of it is stated here.** |
| `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` | The Test 2 verification criterion | Cited. Not restated, not applied, not affected. Production and Test 2 are different questions and neither answers the other. |

**Where this record and any record above appear to disagree, the record above
wins.** This record states no skill classification, no output property, no role
property, no verification criterion, no business rule and no authorisation.

**A dependency, recorded rather than resolved.** Two of the records above —
`decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` and
`decisions/DECISION_ORIGINATING_SKILL.md` — are committed carrying `Approval
Status: DRAFT — awaiting Owner review`. This record's **3** is stated in relation
to concepts those records own. **Whether either is approved is not decided here**,
and this record claims no approval on their behalf. `[VERIFY]`

---

## 6. Explicit Exclusions

**This record does NOT determine any of the following.**

| # | Not determined | Status |
|---|----------------|--------|
| 1 | **Which skills produce** a Published Review Output | **OPEN `[VERIFY]`** |
| 2 | **Any individual skill** — none is named, addressed, qualified or disqualified | **OPEN `[VERIFY]`** |
| 3 | **Production status** — of anything, for any skill, at any time | **OPEN `[VERIFY]`** |
| 4 | **Implementation** — how production is determined, recorded, exposed or consumed | **OPEN `[VERIFY]`** |
| 5 | **Addressing** | **OPEN `[VERIFY]`** |
| 6 | **Storage** | **OPEN `[VERIFY]`** |
| 7 | **Publication granularity** | **OPEN `[VERIFY]`** |

Also not determined, and not defined anywhere in this record: **carrier**,
**filenames**, **persistence**, **lifecycle**, **schema**, **identity**, **output
templates**, **automation**, **routing** and **marketplace behaviour**.

**These exclusions are part of the decision, not commentary on it.** A later task
must not treat any of them as settled, as implied, or as derivable from **3**.

**In particular: no skill acquires or loses production status by virtue of this
record.** Under **3**, every production question that had not been separately
determined before this record remains undetermined after it.

---

## 7. OPEN `[VERIFY]`

**Questions this record intentionally leaves open. Each is open by design, not by
omission.**

| # | Open question | Status |
|---|---------------|--------|
| 1 | **Which skills produce a Published Review Output** — for every skill, without exception | **OPEN `[VERIFY]`** |
| 2 | **What form a production determination takes** — how the Owner records one, and what a valid one consists of | **OPEN `[VERIFY]`** |
| 3 | **Whether production determinations are made per skill, per skill type, or collectively** | **OPEN `[VERIFY]`** |
| 4 | **Whether a production determination is permanent or per-run** | **OPEN `[VERIFY]`** |
| 5 | **What follows when production is undetermined** for something a referencing skill would otherwise reference | **OPEN `[VERIFY]`** |

**Items open under other records remain open under those records.** They are not
re-listed here, are not adopted here, and listing them elsewhere creates no
ownership in this record.

**No existing `[VERIFY]` anywhere in the repository is resolved by this record.**

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the Production Principle stated in **3**. That is new
truth and exists nowhere else in the repository.

**What it does NOT own, and never becomes:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window, rule tier or formula appears here. This is
  verifiable by reading the file: it contains none.
- **A second Published Review Output owner.** No property, definition, publication
  meaning or ownership statement from that record is reproduced, paraphrased or
  reinterpreted.
- **A second Originating Skill owner.** No property of that role is reproduced or
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
- **A production-status owner.** No skill's production status is established.
- **An owner of any skill's output, output template or execution procedure.** Each
  skill retains its own; none is restated, standardised or absorbed.
- **A granularity, carrier, addressing, storage, persistence or lifecycle owner.**
- **A status-vocabulary owner.** No status is created, widened, narrowed or
  redefined.
- **An authorisation owner.** Authorisation remains with `CLAUDE.md`.

**No existing `[VERIFY]` is resolved** by this record. No gap is created, closed
or narrowed; `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## 8. Known Limitations

Genuine unresolved governance items. None is worked around by inventing data.

1. **No production determination exists for anything.** The principle requires
   one; none has been made. Every production question is therefore undetermined.
   `[VERIFY]`
2. **The form of a production determination is undefined.** How the Owner records
   one, and what makes one valid, is not established. `[VERIFY]`
3. **This record depends on two records that are not Owner-approved.**
   `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` and
   `decisions/DECISION_ORIGINATING_SKILL.md` are each committed as `DRAFT —
   awaiting Owner review`. See **5**. `[VERIFY]`
4. **The text of this record has not been Owner-reviewed.** The principle in **3**
   is Owner-supplied and approved; the surrounding text is not yet reviewed.
   `[VERIFY]`
5. **No skill is modified by this record**, and no skill states anything about
   production in these terms. `[VERIFY]`
6. **Every item in 7 remains open**, and none is narrowed by this record.
   `[VERIFY]`
7. **This record is not indexed in `validation/REPOSITORY_GAP_REGISTER.md`.**
   Whether it should be is a separate question for that register's own governance,
   and is not decided here. `[VERIFY]`
8. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
9. **Decision-record filename convention undefined** —
   `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
   here is descriptive, not conventional; the path was specified by the Owner
   before creation. `[VERIFY]`

---

## Review Requirement

**Owner review only.**

- **Owner:** Jathukulan — repository `Owner`.
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01). No reviewer is
  assigned or invented by this record.
- **What review means here:** confirming that the principle in **3** is recorded as
  the Owner stated it, that the exclusions in **6** hold, and that nothing beyond
  the principle has been decided. **Review approves no downstream work, because
  none is proposed.**

---

## Next Step

**One next action, and it is a decision, not implementation.**

Owner review of this record's text.

Everything in **7** remains a separate matter for its own decision. None is made
here, none is pre-empted here, and **this record recommends no implementation.**

---

## Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one file created — this record; no existing file modified | **PASS** |
| 2 | No PPC business-rule value present | **PASS** |
| 3 | The Production Principle recorded, and stated clearly | **PASS** — **3** |
| 4 | Recorded as an **Owner governance decision**, not derived from repository evidence | **PASS** — **3** |
| 5 | **No individual skill named anywhere** in the record | **PASS** |
| 6 | **No skill determined to produce** | **PASS** — **3**, **6**, **7** |
| 7 | **No production status established** for anything | **PASS** — **6** |
| 8 | Publication granularity, addressing, storage, filenames, implementation, routing and marketplace behaviour all left undefined | **PASS** — **6** |
| 9 | Published Review Output, Originating Skill, Skill Classification, Test 2 and "Phase 1b" each left with their existing owners, unrestated | **PASS** — **5** |
| 10 | No existing decision reopened | **PASS** — **5** |
| 11 | Repository silence recorded as silence, not converted into governance | **PASS** — **2** |
| 12 | No new status vocabulary created | **PASS** — **3** |
| 13 | No existing `[VERIFY]` resolved; Gap Register untouched | **PASS** — Duplicate Truth Prevention |
| 14 | Approval status recorded honestly — principle approved; record text not yet reviewed | **PASS** — Metadata; Review Requirement |
| 15 | Owner, decision date and HEAD recorded | **PASS** — Jathukulan, 2026-08-04, `3b570a6` |

**Result: PASS** — principle decided; nothing downstream decided.

---

## Queryability Test

Using only this record and the paths it references, can another LLM answer:

| # | Question | Answerable? | Answer / Where |
|---|----------|-------------|----------------|
| 1 | **What is the Production Principle?** | Yes | Completion of a skill's own defined artefact does **not** itself constitute production of a Published Review Output; production is a separate governance determination made by the Owner — **3** |
| 2 | **Why does it exist?** | Yes | Two concepts were defined, the step between them was not; both readings were available and no record selected between them — **1**, **2** |
| 3 | **What does it decide?** | Yes | That completion does not entail production, and that production is separately Owner-determined — **3** |
| 4 | **What does it deliberately NOT decide?** | Yes | Which skills produce; any individual skill; production status; implementation; addressing; storage; publication granularity; carrier; filenames; persistence; lifecycle; routing; marketplace behaviour — **6** |
| 5 | **Which decision records remain authoritative?** | Yes | `DECISION_PHASE_1B_SKILL_CLASSIFICATION.md`, `DECISION_PUBLISHED_REVIEW_OUTPUT.md`, `DECISION_ORIGINATING_SKILL.md`, `DECISION_TEST2_VERIFICATION_CRITERION.md` — **5**, **10** |
| 6 | **What remains OPEN `[VERIFY]`?** | Yes | Five questions — **7**; plus the exclusions in **6** |
| 7 | Is production established by a skill type? | Yes | **No** — **3**, consequence 2 |
| 8 | Is production established by an architectural relationship? | Yes | **No** — **3**, consequence 2 |
| 9 | Does a skill produce one by finishing its artefact? | Yes | **No** — **3**, consequence 1 |
| 10 | If production has not been determined, has it been determined negatively? | Yes | **No — it is undetermined**, which is not a verdict — **3** |
| 11 | Does this record name any skill? | Yes | **No** — **4**, **6**; Pass/Fail 5 |
| 12 | Is this an Owner decision or a derivation? | Yes | **An Owner governance decision**, supplied and approved by the Owner — **3** |
| 13 | Does this record create a new status? | Yes | **No** — **3** |
| 14 | Does it authorise implementation? | Yes | **No** — **4**, **6**; Metadata |
| 15 | Does it depend on unapproved records? | Yes | **Yes** — two, both committed as DRAFT — **5**; Known Limitations 3 |
| 16 | Is this record's text approved? | Yes | **No** — the principle is; the text awaits review — Metadata; Review Requirement |

**Result: PASS**

---

## 9. Safety Boundary

Per `CLAUDE.md`:

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

Deciding when something counts as produced changes what governance can **assert**.
It changes nothing about what a skill is permitted to **do**. Every skill output
remains an evidence-backed DRAFT recommendation only. Amazon Ads changes remain
human reviewed and human executed, applied manually by Jathukulan.

**This record establishes no routing behaviour and no marketplace behaviour**, and
neither is affected by it in any way.

This record is documentation. It performs no Amazon Ads action, holds no
credentials, and produces no recommendation to act. No Amazon Ads connection
exists in this repository.

---

## 10. References

Referenced by path only. **None is restated, redefined, amended or reopened.**

| Path | Owns |
|------|------|
| `decisions/DECISION_PHASE_1B_DEFINITION.md` | The definition of the term "Phase 1b" |
| `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` | The Phase 1b skill types, their Test 1 and Test 2 relationships, and the confirmed and unresolved skill mappings |
| `decisions/DECISION_PUBLISHED_REVIEW_OUTPUT.md` | Published Review Output |
| `decisions/DECISION_ORIGINATING_SKILL.md` | Originating Skill |
| `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` | The Test 2 verification criterion |
| `CLAUDE.md` | AI operating and safety authorisation |
| `validation/REPOSITORY_GAP_REGISTER.md` | Repository-wide gap navigation — **untouched by this record** |

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** Jathukulan — repository Owner
- **Decision Date:** 2026-08-04
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** **OWNER APPROVED — principle only; record text awaiting Owner review**
- **Repository HEAD when created:** `3b570a668468f21d03193722b33beabe0858e7b0`
- **Authoritative for:** the Production Principle only
- **Existing files modified by this task:** **NONE**
- **Skills modified:** **NO**
- **Skills named in this record:** **NONE**
- **Skills determined to produce:** **NONE**
- **Production status established:** **NO**
- **Publication granularity determined:** **NO**
- **Addressing determined:** **NO**
- **Storage determined:** **NO**
- **Implementation authorised:** **NO**
- **Routing determined:** **NO**
- **Marketplace behaviour determined:** **NO**
- **Rule files modified:** **NO**
- **Registry modified:** **NO**
- **Validation assets modified:** **NO**
- **`CLAUDE.md` modified:** **NO**
- **Existing decisions reopened:** **NONE**
- **Evidence filed by this task:** **NO**
- **`[VERIFY]` items resolved by this task:** **NONE**
- **Gap Register modified:** **NO**
