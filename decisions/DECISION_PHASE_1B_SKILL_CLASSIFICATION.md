<!--
Governance decision record — PHASE 1b ARCHITECTURE APPROVED;
PHASE 1b IMPLEMENTATION NOT AUTHORISED.

This file records the Owner's approved architecture for how Phase 1b skill types
relate to marketplace-routing Test 1 and Test 2. The ARCHITECTURE is approved.
NOTHING DOWNSTREAM OF IT IS APPROVED: no implementation, no skill modification,
no rule-file change, no registry change, no validation change, no evidence
filing, and no change to CLAUDE.md.

This record does NOT redefine Test 2 and does NOT change Test 2 ownership. The
Test 2 verification criterion remains owned by
decisions/DECISION_TEST2_VERIFICATION_CRITERION.md. Test 1 remains owned by
context/marketplace-routing.md. This record states WHICH KIND OF SKILL PERFORMS
WHICH TEST, AND WHEN. It states nothing about what either test means.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, ratio, click gate, order count, price band, spend trigger, budget
figure, multiplier, efficiency value, evaluation window, rule tier or formula
appears anywhere in it, and none may be added. It contains NO routing matrix, NO
authorised-marketplace list and NO Test 2 availability matrix.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename
follows the DECISION_ prefix pattern already used by the sibling records in this
folder, and the path was proposed to and approved by the Owner before creation.
The status inside this document, not the filename, is authoritative.
-->

# Decision — Phase 1b Skill Classification and Test Relationships

**Phase 1b architecture: APPROVED. Phase 1b implementation: NOT AUTHORISED.
Test 2 is neither redefined nor re-owned by this record.**

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — Phase 1b skill-type architecture |
| Approval Status | **OWNER APPROVED** — architecture only |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | **Jathukulan — repository Owner** |
| Decision Date | **2026-08-04** |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-08-04 |
| Repository HEAD when created | **`f0400c011c17b6a567dd0ad890d493a6125529b1`** |
| Approved path | `decisions/DECISION_PHASE_1B_SKILL_CLASSIFICATION.md` — proposed to, and approved by, the Owner before creation |
| Authoritative for | **The Phase 1b skill-type architecture — the three skill types, their Test 1 relationships, their Test 2 relationships, and the confirmed and unresolved skill mappings. Nothing else.** |
| Explicitly NOT authoritative for | The Test 2 verification criterion; Test 1 routing authorisation; the definition of "Phase 1b"; the approved Phase 1 architecture; Phase 1b authorisation; marketplace scope; PPC rule content; evidence governance; validation governance; implementation; approval of any repository modification. |
| Phase 1b Implementation Authorised By This Record | **NO** |
| Phase 1b Implementation Started | **NO** |
| Phase 2 Authorised By This Record | **NO** |

---

## 1. Purpose

**This record gives the repository one canonical answer to a single
architectural question, and does nothing else.**

**The business question it answers:**

> What is the architectural relationship between a Phase 1b skill's type,
> marketplace-routing Test 1, and marketplace-routing Test 2?

**Why a record is needed.** `decisions/DECISION_PHASE_1B_DEFINITION.md` defines
Phase 1b as extending the marketplace-routing / two-test model to further skills
beyond the two Phase 1a consumers. `CLAUDE.md` → **Approved Authorisation — Phase
1b Marketplace-Routing Skill Extension** names the seven skills that extension may
reach. **Neither settles how the two tests apply to skills that do different kinds
of work.**

A skill that evaluates evidence against a governing source, a skill that
consolidates findings other skills already validated, and a skill that routes or
presents are three different kinds of action. Before this record, no repository
asset stated whether they relate to Test 1 and Test 2 in the same way. Under
`CLAUDE.md` → *Queryability First*, an architecture that exists only in
conversation cannot be applied tomorrow, and two tasks could reach opposite
readings of the same skill and each cite governance.

**The Owner has now supplied the architecture. It is new governance truth as of
this record.**

---

## 2. Ownership

- **Owner:** Jathukulan — repository `Owner`.
- **Approved By:** Jathukulan — repository Owner.
- **Decision Date:** 2026-08-04.
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01). None assigned
  or invented by this record.
- **Decision source:** Jathukulan, repository Owner, communicated directly and
  recorded here on 2026-08-04.
- **How the question was identified:** a read-only architecture assessment
  performed at HEAD `f0400c011c17b6a567dd0ad890d493a6125529b1` established that no
  repository asset defined the relationship between Phase 1b skill types and the
  two tests. **That assessment identified the question. It did not supply, derive
  or prove the architecture**, and it is not filed as a repository artefact.
  `[VERIFY]` — whether it should be filed is not decided here.
- **The Owner selected the architecture.** This record does not derive it from
  repository evidence and does not present it as derived. Where this record and an
  owning record named in **5** appear to disagree, **the owning record wins.**
- **No external source consulted.** No Amazon Ads data was read, requested or
  filed. No Amazon Ads connection exists.

---

## 3. Scope

**This record defines Phase 1b architecture only.**

It settles how the three skill types relate to the two tests. It settles nothing
about whether that work may be implemented, when, by whom, to which files, or
under what conditions.

**Defining an architecture is not authorising the work it describes.** The two are
separate acts requiring separate Owner decisions, and only the first has occurred
here.

This record therefore does **not**:

- authorise Phase 1b implementation;
- begin Phase 1b implementation;
- modify any skill;
- modify `context/marketplace-routing.md`;
- modify any `context/` rule file;
- modify `CLAUDE.md`;
- modify any validation asset;
- redefine Test 2;
- change Test 2 ownership;
- change Test 1 ownership;
- encode any executable Test 2 criterion or any executable rule logic;
- file evidence, or resolve any existing `[VERIFY]`;
- approve any repository modification;
- assign ownership where none has been Owner-approved.

**It performs no file operation beyond its own creation.**

---

## 4. What This Record Owns

**This record owns ONLY the following, and each is new truth that exists nowhere
else in the repository:**

1. **The three Phase 1b skill types** — Primary Evaluation, Consolidation, and
   Routing / Reporting.
2. **The canonical Test 1 relationship by skill type**, including the Test 1
   independence rule and the Type 3 Test 1 timing rule.
3. **The canonical Test 2 relationship by skill type.**
4. **The confirmed skill → type mappings.**
5. **The register of unresolved mappings**, and the outstanding Owner decision each
   awaits.

---

## 5. What This Record Does NOT Own

| Not owned here | Owned by |
|----------------|----------|
| **The Test 2 verification criterion** | `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` |
| **Test 2 underlying content, and its status** | The owning rule file: `context/bid-rules.md`, `context/budget-rules.md`, `context/hour-budget-rules.md`, `context/product-pause-rules.md` |
| **Test 1 — marketplace routing authorisation** | `context/marketplace-routing.md` |
| **The definition of the term "Phase 1b"** | `decisions/DECISION_PHASE_1B_DEFINITION.md` |
| **The approved Phase 1 architecture, and the two-test model itself** | `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` |
| **Phase 1b authorisation; authorised and excluded paths** | `CLAUDE.md` → **Approved Authorisation — Phase 1b Marketplace-Routing Skill Extension** |
| **PPC rule content** | The four `context/*-rules.md` files |
| **Marketplace scope** | `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` |
| **Evidence governance** | `evidence/README.md`, per `CLAUDE.md` → *Evidence First* |
| **Validation governance** | `validation/README.md` |
| **Gap navigation** | `validation/REPOSITORY_GAP_REGISTER.md` — untouched by this record |
| **Failure outcome when a test does not pass** | `CLAUDE.md` → Phase 1a **§E** |
| **Each skill's own execution procedure** | That skill's own file in `skills/` |
| **Implementation** | No owner exists; implementation requires its own separately scoped and approved task |

**On any conflict, the owner named above wins.** This record states no business
rule, no routing decision, no content status and no authorisation.

**This record states which kind of skill performs which test, and when. It states
nothing about what either test means.**

---

# 6. Architecture

**Approved by Jathukulan (Owner) on 2026-08-04.**

## A. Skill Types

Three Phase 1b skill types are defined. They are distinguished by the kind of
action the skill performs.

| Type | Name | What distinguishes it |
|------|------|-----------------------|
| **Type 1** | **Primary Evaluation** | Reaches a first-order finding by applying its named primary governing source to evidence. |
| **Type 2** | **Consolidation** | Brings together findings that another skill has already validated. It does not re-derive them. |
| **Type 3** | **Routing / Reporting** | Routes a request onward, or presents findings already validated elsewhere. It performs no evaluation of its own. |

---

## B. Test 1 Relationships

### By skill type

| Type | Test 1 relationship |
|------|---------------------|
| **Type 1** | **Performs Test 1 before beginning its own evaluation.** |
| **Type 2** | **Performs Test 1 before beginning its own consolidation.** |
| **Type 3** | **Performs Test 1 before performing routing or reporting.** |

### Architecture Rule — Test 1 independence

**Each skill performs Test 1 independently for its own action.**

**No skill performs Test 1 on behalf of another.**

**A Type 2 or Type 3 skill performing Test 1 does NOT discharge, replace or
satisfy the Test 1 that any downstream skill must perform for itself.**

**Every skill remains independently responsible for its own Test 1.**

### Architecture Rule — Type 3 Test 1 timing

**For Type 3 skills:**

**A Test 1 failure does NOT block production of the routing or reporting
output.**

**The outcome is reflected only through the existing Downstream Readiness
mechanism.**

**No new status vocabulary.**

**No routing block.**

**This introduces no new behaviour.** The outcome of a Test 1 failure for a Type 3
skill is the outcome that skill's own Decision Rules already provide, expressed
through the mechanism that skill already has. `CLAUDE.md` → Phase 1a **§E**
remains the owner of the failure outcome, and it states that no new
repository-wide status vocabulary is introduced. Nothing here creates, widens,
narrows or redefines any status.

---

## C. Test 2 Relationships

| Type | Test 2 relationship |
|------|---------------------|
| **Type 1** | **Performs Test 2 against its named primary governing source.** |
| **Type 2** | **References the originating skill's published review output only.** |
| **Type 3** | **References the originating skill's published review output only.** |

### What Type 2 and Type 3 must never create

A **Type 2** skill creates:

- **no Test 2 field**
- **no Test 2 store**
- **no Test 2 status**

A **Type 3** skill creates:

- **no Test 2 field**
- **no Test 2 store**
- **no Test 2 status**

**Referencing a published upstream result is consumption, not ownership.** A Type
2 or Type 3 skill neither answers Test 2 nor holds a Test 2 answer. It reads what
the originating skill published and carries it forward unchanged.

**Test 2 ownership is unchanged by this section.** The criterion remains owned by
`decisions/DECISION_TEST2_VERIFICATION_CRITERION.md`. The underlying content and
its status remain owned by the owning `context/` rule file. This section assigns
performance, not ownership.

---

## D. Confirmed Mappings

| Skill | Type |
|-------|------|
| **`skills/keyword-expand.md`** | **Type 1 — Primary Evaluation** |
| **`skills/campaign-audit.md`** | **Type 2 — Consolidation** |
| **`skills/report-draft.md`** | **Type 3 — Routing / Reporting** |
| **`skills/ppc-brief.md`** | **Type 3 — Routing / Reporting** |

**These four mappings are confirmed by Owner decision.** No further mapping is
confirmed, and none may be inferred from this table.

---

## E. Unresolved Mappings

**No classification is assigned below.** Each item awaits an explicit Owner
decision. **No classification, and no ownership, may be inferred from the absence
of one here.**

### `skills/scale-check.md`

**Status: UNRESOLVED.**

**Outstanding Owner decision:** Is `context/budget-rules.md` the governing source,
or is `campaign-audit` the governing gate?

---

### `skills/search-term-check.md`

**Status: UNRESOLVED.**

**Outstanding Owner decision:** Which source is the primary governing source?

**No classification until explicitly designated.**

---

### `skills/waste-scan.md`

**Status: UNRESOLVED.**

**Blocked by GAP-S02** — `validation/REPOSITORY_GAP_REGISTER.md` → GAP-S02, owned
by `skills/waste-scan.md` → *Known Limitations*.

**Classification deferred.** No authoritative threshold exists.

---

### `keyword-expand` Test 2 owner

**Status: UNRESOLVED.**

**No Test 2 owner assigned.**

**No ownership inferred.**

**Requires separate future Owner decision.**

`skills/keyword-expand.md` is confirmed **Type 1** in **D**, and a Type 1 skill
performs Test 2 against its named primary governing source. **Which source owns
Test 2 for that skill is not decided here, is not assumed, and is not inferred.**

**`context/marketplace-routing.md` is not extended by this record**, and nothing
here adds any rule family, any owning source or any routing entry to it. It
remains the Test 1 owner and nothing more.

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the five items listed in **4**. That is new truth and
exists nowhere else in the repository.

**What it does NOT own, and never becomes:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window, rule tier or formula appears here. This is
  verifiable by reading the file: it contains none.
- **A second Test 2 owner.** The criterion is not restated, not paraphrased and
  not reinterpreted. No marketplace / rule-family combination is classified, and
  no Test 2 availability matrix is created.
- **A second Test 1 / routing owner.** No routing matrix, no
  authorised-marketplace list and no marketplace authorisation statement is
  reproduced.
- **A second architecture owner for Phase 1.** The approved Phase 1 architecture,
  including the two-test model itself, remains owned by
  `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md`, which is cited
  and never restated as independent truth.
- **A second owner of the term "Phase 1b".** That remains with
  `decisions/DECISION_PHASE_1B_DEFINITION.md`.
- **A second marketplace-scope owner.** No marketplace is named, added, removed or
  reclassified.
- **A second evidence-governance owner.** `evidence/README.md` is referenced, not
  restated, and no evidence path is invented.
- **A second authorisation owner.** Authorisation remains with `CLAUDE.md`.
- **A status-vocabulary owner.** No status is created, widened, narrowed or
  redefined.
- **An owner of any skill's execution procedure.** Each skill file remains the
  owner of its own.

**No existing `[VERIFY]` is resolved** by this record. No gap is created, closed
or narrowed; `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Known Limitations

Genuine unresolved governance items. None is worked around by inventing data.

1. **Three of the seven Phase 1b skills remain unclassified** — `scale-check`,
   `search-term-check` and `waste-scan`. Each awaits its own Owner decision per
   **E**. No classification is inferred. `[VERIFY]`
2. **The `keyword-expand` Test 2 owner is not assigned.** Per **E**, this requires
   a separate future Owner governance decision. `context/marketplace-routing.md` is
   not extended, and no owning source is inferred. Until that decision is taken,
   the confirmed Type 1 mapping in **D** stands as a classification, while the
   source its Test 2 runs against remains undecided. `[VERIFY]`
3. **`waste-scan` classification is gated on GAP-S02**, which is open and owned by
   `skills/waste-scan.md` → *Known Limitations*. This record neither resolves nor
   narrows it. `[VERIFY]`
4. **Phase 1b implementation is not authorised and has not started.** `CLAUDE.md`
   records `Phase 1b Implementation Started: NO`, and this record does not change
   that. Implementation requires its own separately scoped and approved task.
   `[VERIFY]`
5. **No skill file is modified by this record.** The seven Phase 1b skills remain
   exactly as committed; none yet consumes the marketplace-routing model. `[VERIFY]`
6. **`context/marketplace-routing.md` is not updated.** Its consumer list and its
   phase-status statements remain exactly as committed, owned by that file.
   `[VERIFY]`
7. **The architecture assessment that identified this question is not filed** as a
   repository artefact, consistent with the treatment of prior read-only
   discoveries. `[VERIFY]`
8. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
9. **Decision-record filename convention undefined** —
   `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
   here is descriptive, not conventional; the approved path was confirmed by the
   Owner before creation. `[VERIFY]`

---

## Review Requirement

**Owner review only.**

- **Owner:** Jathukulan — repository `Owner`.
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01). No reviewer is
  assigned or invented by this record.
- **What review means here:** confirming that the Owner's architecture is recorded
  as approved and that the boundaries in this record hold. **Review approves no
  downstream work, because none is proposed.**

---

## Next Step

**One next action, and it is a decision, not implementation.**

Separate Owner decisions on the four unresolved items in **E** — the `scale-check`
governing source, the `search-term-check` primary governing source, the
`waste-scan` classification once GAP-S02 is resolved, and the `keyword-expand`
Test 2 owner.

Phase 1b implementation remains separately gated. It is not made here, not
pre-empted here, and not recommended here. **This record recommends no
implementation.**

---

## Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one file created — this record; no other file created or modified | **PASS** |
| 2 | No PPC business-rule value present | **PASS** |
| 3 | Three skill types recorded, with Test 1 and Test 2 relationships stated per type | **PASS** — **6 A**, **6 B**, **6 C** |
| 4 | Test 1 independence rule recorded — no skill performs Test 1 on behalf of another | **PASS** — **6 B** |
| 5 | Type 3 Test 1 timing recorded — no routing block, no new status, existing Downstream Readiness mechanism only | **PASS** — **6 B** |
| 6 | Type 2 and Type 3 recorded as creating no Test 2 field, store or status | **PASS** — **6 C** |
| 7 | Test 2 **not** redefined; the criterion not restated, paraphrased or reinterpreted | **PASS** |
| 8 | Test 2 ownership unchanged | **PASS** — **5** |
| 9 | Test 1 ownership unchanged; no routing matrix reproduced; registry not extended | **PASS** — **5**, **6 E** |
| 10 | Exactly the four confirmed mappings recorded | **PASS** — **6 D** |
| 11 | The four unresolved items recorded as UNRESOLVED, with no classification or ownership inferred | **PASS** — **6 E** |
| 12 | No implementation authorised; no skill, rule file, registry, validation asset or `CLAUDE.md` modified | **PASS** — **3** |
| 13 | No new status vocabulary created | **PASS** |
| 14 | No marketplace named, added, removed or reclassified | **PASS** |
| 15 | Owner, decision date, HEAD and status recorded | **PASS** — Jathukulan, 2026-08-04, `f0400c0`, Owner Approved |

**Result: PASS** — architecture recorded; nothing downstream authorised.

---

## Queryability Test

Using only this record and the paths it references, can another LLM answer:

| # | Question | Answerable? | Answer / Where |
|---|----------|-------------|----------------|
| 1 | What are the three Phase 1b skill types? | Yes | Primary Evaluation, Consolidation, Routing / Reporting — **6 A** |
| 2 | When does a Type 1 skill perform Test 1? | Yes | Before beginning its own evaluation — **6 B** |
| 3 | When does a Type 2 skill perform Test 1? | Yes | Before beginning its own consolidation — **6 B** |
| 4 | When does a Type 3 skill perform Test 1? | Yes | Before performing routing or reporting — **6 B** |
| 5 | May one skill perform Test 1 on behalf of another? | Yes | **No** — **6 B**, Test 1 independence |
| 6 | Does a Type 2 or Type 3 Test 1 discharge a downstream skill's Test 1? | Yes | **No** — **6 B** |
| 7 | Does a Test 1 failure block a Type 3 skill from producing its output? | Yes | **No** — **6 B**, Type 3 Test 1 timing |
| 8 | How is a Type 3 Test 1 failure reflected? | Yes | Only through the existing Downstream Readiness mechanism; no new status, no routing block — **6 B** |
| 9 | Which type performs Test 2? | Yes | **Type 1 only**, against its named primary governing source — **6 C** |
| 10 | What do Type 2 and Type 3 do about Test 2? | Yes | Reference the originating skill's published review output only — **6 C** |
| 11 | May a Type 2 or Type 3 skill create a Test 2 field, store or status? | Yes | **No** — **6 C** |
| 12 | Which skills are confirmed, and as what type? | Yes | `keyword-expand` Type 1; `campaign-audit` Type 2; `report-draft` Type 3; `ppc-brief` Type 3 — **6 D** |
| 13 | Which items are unresolved? | Yes | `scale-check`, `search-term-check`, `waste-scan`, and the `keyword-expand` Test 2 owner — **6 E** |
| 14 | Why is `waste-scan` unresolved? | Yes | Blocked by GAP-S02; no authoritative threshold exists — **6 E** |
| 15 | Who owns the Test 2 criterion? | Yes | `decisions/DECISION_TEST2_VERIFICATION_CRITERION.md` — **5** |
| 16 | Does this record redefine Test 2? | Yes | **No** — **3**, **5**, **6 C** |
| 17 | Does this record change Test 2 ownership? | Yes | **No** — **5** |
| 18 | Who owns Test 1? | Yes | `context/marketplace-routing.md` — **5** |
| 19 | Was `context/marketplace-routing.md` extended by this record? | Yes | **No** — **6 E** |
| 20 | Does this record authorise implementation? | Yes | **No** — **3**; Metadata |
| 21 | Has Phase 1b implementation started? | Yes | **No** — Metadata; Known Limitations 4 |
| 22 | Does this record contain any PPC value? | Yes | **No** — Duplicate Truth Prevention |
| 23 | Does this record change marketplace scope or routing? | Yes | **No** — **5**; Duplicate Truth Prevention |
| 24 | What is the next action? | Yes | Separate Owner decisions on the four unresolved items — Next Step |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** Jathukulan — repository Owner
- **Decision Date:** 2026-08-04
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** **Owner Approved** — architecture only
- **Repository HEAD when created:** `f0400c011c17b6a567dd0ad890d493a6125529b1`
- **Authoritative for:** the Phase 1b skill-type architecture only
- **Existing files modified by this task:** **NONE**
- **Skills modified:** **NO**
- **Rule files modified:** **NO**
- **Registry modified:** **NO**
- **Validation assets modified:** **NO**
- **`CLAUDE.md` modified:** **NO**
- **Phase 1b Implementation Authorised:** **NO**
- **Phase 1b Implementation Started:** **NO**
- **Phase 2 Authorised:** **NO**
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

**Extending the routing model changes what a skill checks before it reports. It
changes nothing about what a skill is permitted to do.** Every output of every
Phase 1b skill remains an evidence-backed DRAFT recommendation only. Amazon Ads
changes remain human reviewed and human executed, applied manually by Jathukulan.

This record is documentation. It performs no Amazon Ads action, holds no
credentials, and produces no recommendation to act. No Amazon Ads connection
exists in this repository.
