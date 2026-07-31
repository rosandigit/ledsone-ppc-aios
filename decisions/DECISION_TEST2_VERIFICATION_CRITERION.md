<!--
Governance decision record — TEST 2 VERIFICATION CRITERION APPROVED;
PHASE 1b IMPLEMENTATION NOT APPROVED.

This file records the Owner's approved criterion for deciding whether
marketplace-specific rule content satisfies marketplace-routing Test 2. The
CRITERION is approved. NOTHING DOWNSTREAM OF IT IS APPROVED: no Phase 1b
implementation, no change to any rule file, no change to any skill, no change to
the routing registry, no evidence filing, and no classification of any current
marketplace / rule-family combination.

PROVENANCE — stated precisely. A read-only Phase 1b discovery IDENTIFIED that no
deterministic Test 2 criterion existed in this repository. The discovery did NOT
derive, prove or supply the criterion, and no such criterion was previously
present in any repository asset. The OWNER supplied and approved the criterion
recorded here. It is new governance truth as of this record.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, ratio, click gate, order count, price band, spend trigger, budget
figure, multiplier, efficiency value, evaluation window, rule tier or formula
appears anywhere in it, and none may be added. It also contains NO routing matrix
and NO Test 2 availability matrix.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename
follows the DECISION_ prefix pattern already used by the sibling records in this
folder. The status inside this document, not the filename, is authoritative.
-->

# Decision — Test 2 Verification Criterion

**Test 2 criterion: APPROVED. Phase 1b implementation: NOT APPROVED. No current
marketplace / rule-family combination is classified by this record.**

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — Test 2 verification criterion |
| Approval Status | **OWNER APPROVED** — criterion only |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | **Jathukulan — repository Owner** |
| Decision Date | 2026-07-31 |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-07-31 |
| Repository HEAD when created | `2bd75686e4c18847493274c50fc9af18a05ae6be` |
| Authoritative for | **The Test 2 verification criterion, and nothing else.** |
| Explicitly NOT authoritative for | Test 1 routing authorisation; any PPC business rule; any rule family's content; evidence-filing governance; the failure-outcome vocabulary; the status of any current marketplace / rule-family combination. |
| Phase 1b Implementation Authorised | **NO** |
| Phase 2 Started | **NO** |

---

## Purpose and Business Question

Phase 1a established two independent routing tests. **Test 1** — is the
marketplace authorised for routing? — is deterministic and owned by
`context/marketplace-routing.md`. **Test 2** — does the owning rule source
contain *verified* marketplace-specific content? — was not deterministic, because
**no repository asset defined what "verified" means in that context.**

**The business question this record answers:**

> What criterion determines whether marketplace-specific rule content satisfies
> marketplace-routing Test 2?

**Why a record is needed.** Without it, each task would have to invent its own
reading of "verified", and two tasks could reach opposite Test 2 answers for the
same marketplace and rule family. Under `CLAUDE.md` → *Queryability First*, a
criterion that exists only in conversation cannot be applied tomorrow.

---

## Source of the Decision

- **Decision source:** Jathukulan, repository Owner, communicated directly and
  recorded here on 2026-07-31.
- **How the gap was found:** a read-only Phase 1b discovery performed at HEAD
  `2bd75686e4c18847493274c50fc9af18a05ae6be` established that no repository asset
  defined a Test 2 criterion. **That discovery identified the gap. It did not
  supply, derive or prove the criterion**, and it is not filed as a repository
  artefact. `[VERIFY]` — whether it should be filed is not decided here.
- **This criterion did not previously exist in the repository.** It is not a
  restatement, clarification or interpretation of any existing asset. It is new
  governance truth as of this record.
- **Relationship to existing Evidence First requirements.** `CLAUDE.md` →
  *Evidence First* already requires that evidence be recorded in `evidence/` with
  its source, date and date range, and that a value not documented from a
  verified source be marked `[VERIFY]`. The criterion below **composes those
  existing requirements into a determinate two-condition test**. It does not
  amend, widen or reinterpret them, and on any conflict `CLAUDE.md` wins.
- **No external source consulted.** No Amazon Ads data was read, requested or
  filed. No Amazon Ads connection exists.

---

# Owner Decision — The Test 2 Criterion

**Approved.**

> **Test 2 PASSES only if BOTH of the following are satisfied:**
>
> **Condition 1 —** the owning rule file contains **marketplace-specific rule
> content** for the requested marketplace and rule family, **supported by a
> verified source**.
>
> **AND**
>
> **Condition 2 —** the supporting source / evidence is **filed in the approved
> repository evidence location**, **and** the owning rule file **does not mark
> that required content or evidence as `[VERIFY]`**.
>
> **If either condition is not satisfied, Test 2 does NOT pass.**

**The relationship is AND, never OR.** One condition satisfied is not a partial
pass and is not a pass.

**Where Test 2 does not pass**, the repository's already-governed handling
applies — `[VERIFY]` / Insufficient Evidence as the owning skill provides, per
`CLAUDE.md` → Phase 1a **§E**. **No new status is created here**, and the
existing definitions of `[VERIFY]`, Insufficient Evidence, No Action, Conflict
and DRAFT are **unchanged**.

---

## Distinctions This Criterion Deliberately Preserves

These are **not** equivalent, and none of them alone satisfies Test 2:

| Statement | Does it alone make Test 2 PASS? |
|-----------|--------------------------------|
| Content **exists** in a rule file | **NO** |
| Content is **marketplace-specific** | **NO** |
| A source is **named or attributed** in the rule file | **NO** |
| Evidence is **filed** in the approved location | **NO** — not if the owning rule file still marks the required content or evidence `[VERIFY]` |
| A marketplace **owns** the content (by Owner decision) | **NO** — marketplace ownership is a scope fact, not a verification fact |
| A marketplace is **authorised for routing** (Test 1) | **NO** — Test 1 and Test 2 are independent |

**Both approved conditions are required, together.**

**Content presence is not verification.** A populated value, a populated table
and a named source are each evidence that content *exists*; none is evidence that
it is *verified* under this criterion.

**Marketplace ownership is not verification.** That an Owner decision assigns
existing content to a marketplace settles **which marketplace it belongs to**. It
does not settle whether that content satisfies Test 2.

**Test 1 and Test 2 remain independent.** Passing Test 1 does not imply Test 2
passes; satisfying Test 2 does not imply routing is authorised. Nothing here
changes that.

---

## No Current Combination Is Classified By This Record

**This record defines the criterion. It does not apply it.**

**No marketplace / rule-family combination is classified PASS or FAIL here**, and
none may be inferred from this record's existence. Specifically, this record does
**not** determine the Test 2 status of UK, DE, FR or IT against Bid Rules, Budget
Rules, Hour Budget Rules or Product Pause Rules — in any combination.

**No availability matrix is created here**, and creating one as a repository
asset is not authorised by this record.

**Applying the criterion to current repository evidence is a separate,
evidence-based validation task**, which must examine each owning rule file and
the evidence layer as they actually stand.

**A caution, recorded so it is not mistaken for a result.** Approving a criterion
does not create verified content. Where an owning rule file currently records
that its supporting source is not confirmed filed, or marks required content
`[VERIFY]`, Condition 2 is not satisfied on that basis alone — but **which files
those are, and what that means per combination, is for the separate validation
task to establish, not this record.**

---

## Ownership Layers

Each layer owns one thing. None absorbs another.

| Layer | Owner | Notes |
|-------|-------|-------|
| **Test 1 — routing authorisation** | `context/marketplace-routing.md` | **This record does not reproduce the routing matrix and is not a second routing owner.** |
| **Test 2 — verification criterion** | **This record** | The criterion only — not the answer for any combination. |
| **Test 2 — underlying content and its status** | The owning rule file: `context/bid-rules.md`, `context/budget-rules.md`, `context/hour-budget-rules.md`, `context/product-pause-rules.md` | Each remains the sole authority on its own content, its own `[VERIFY]` markings and its own source statements. |
| **PPC rule content** | The same four rule files | **This record does not change, validate, correct, reinterpret or populate any value in them.** |
| **Evidence-filing governance** | `evidence/README.md`, per `CLAUDE.md` → *Evidence First* | Referenced, never reproduced. **No evidence path is invented here**; "the approved repository evidence location" means whatever that governance already defines. |
| **Failure outcome when Test 2 does not pass** | `CLAUDE.md` → Phase 1a **§E** | Referenced, never redefined. |
| **Skill execution procedure** | Each skill file | Unchanged by this record. |

**On any conflict, the owner named above wins.** This record states no business
rule, no routing decision and no content status.

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the Test 2 verification criterion. That is new truth
and exists nowhere else in the repository.

**What it does NOT own, and never becomes:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window, rule tier or formula appears here. This is
  verifiable by reading the file: it contains none.
- **A second Test 1 / routing owner.** No routing matrix, no
  authorised-marketplace list, no marketplace authorisation statement.
- **A content-status owner.** Whether any given combination satisfies the
  criterion is answered by the owning rule file and the evidence layer, per a
  separate validation task — never here.
- **A second evidence-governance owner.** `evidence/README.md` is referenced, not
  restated, and no evidence path is invented.
- **A status-vocabulary owner.** No status is created, widened, narrowed or
  redefined; `CLAUDE.md` §E continues to own the failure outcome.
- **An implementation authorisation.** See below.

**No existing `[VERIFY]` is resolved** by this record. No gap is created, closed
or narrowed; `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Implementation Boundary

**Defining a criterion is not implementing it.**

This record does **not** authorise, and nothing in it may be read as
authorising:

- Phase 1b implementation of any kind;
- modifying any rule file, or adding verification metadata to one;
- modifying any skill, including the two that consume the routing model;
- modifying `context/marketplace-routing.md` or `context/README.md`;
- modifying `CLAUDE.md`;
- creating a Test 2 availability matrix as a repository asset;
- filing evidence, or resolving any existing `[VERIFY]`;
- creating or populating marketplace-specific PPC rule content;
- copying, inferring, adapting or currency-converting UK values into DE, FR or
  IT;
- Phase 2, or any rule-family migration.

**`CLAUDE.md` records Phase 1b Authorised: NO, and this record does not change
that.** Phase 1b implementation requires its own Owner approval and, on current
wording, a `CLAUDE.md` amendment. Neither is performed here.

---

## Authorisation Status

- **Test 2 Criterion Owner Decision:** **APPROVED**
- **Test 2 Criterion Recorded:** **YES**
- **Phase 1b Implementation Authorised:** **NO**
- **Phase 1b Implementation Started:** **NO**
- **Rule Files Modified:** **NO**
- **Skills Modified:** **NO**
- **Registry Modified:** **NO**
- **Evidence Filed By This Task:** **NO**
- **Current Test 2 Cell Status Revalidated:** **NO**
- **Phase 2 Started:** **NO**

---

## Known Limitations

Genuine unresolved items. None is worked around by inventing data.

1. **The criterion is not yet applied.** No combination's Test 2 status is
   established. A separate evidence-based validation task is required. `[VERIFY]`
2. **Phase 1b implementation is not authorised.** Encoding this criterion into
   skills or rule files requires separate Owner approval and, on current wording,
   a `CLAUDE.md` amendment. `[VERIFY]`
3. **"Supported by a verified source" is not further decomposed.** Condition 1
   relies on the owning rule file's own source statements; this record does not
   prescribe how a rule file must express them. `[VERIFY]`
4. **Where the criterion's inputs live is unchanged.** Content and `[VERIFY]`
   markings stay with the owning rule file; filing status stays with the evidence
   layer. Whether either needs a more machine-queryable form is not decided here.
   `[VERIFY]`
5. **The Phase 1b discovery is not filed** as a repository artefact. `[VERIFY]`
6. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. `[VERIFY]`

---

## Next Step

**One next action.** Scope a separate, read-only **validation task** that applies
this approved criterion to the current repository — examining each owning rule
file and the evidence layer — and reports, per marketplace and rule family,
whether Test 2 is satisfied.

That task **applies** the criterion; it does not implement it in any skill or
rule file, and it is not Phase 1b.

---

## Pass / Fail Rule

This record is **PASS** only if **all** hold. Any single failure makes it
**FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one new `decisions/` record; no other file created or modified | **PASS** |
| 2 | No PPC business-rule value present | **PASS** |
| 3 | Both conditions recorded, joined by **AND** | **PASS** |
| 4 | Content presence / marketplace ownership / source attribution / evidence filing each stated as insufficient alone | **PASS** |
| 5 | No routing matrix reproduced; not a second Test 1 owner | **PASS** |
| 6 | No Test 2 availability matrix created | **PASS** |
| 7 | No marketplace / rule-family combination classified | **PASS** |
| 8 | No status created, widened or redefined; §E retained as failure-outcome owner | **PASS** |
| 9 | Rule files, skills, registry, evidence and Gap Register untouched | **PASS** |
| 10 | Phase 1b and Phase 2 not authorised and not started | **PASS** |
| 11 | Provenance stated accurately — discovery identified the gap; Owner supplied the criterion | **PASS** |
| 12 | Owner, date and status recorded | **PASS** — Jathukulan, 2026-07-31, OWNER APPROVED |

**Result: PASS** — criterion recorded; nothing downstream authorised.

---

## Queryability Test

| # | Question | Answer / Where |
|---|----------|----------------|
| 1 | What is Test 2? | Does the owning rule source contain verified marketplace-specific content for the requested marketplace and rule family? — Purpose |
| 2 | What two conditions are required to PASS? | Condition 1 (marketplace-specific content supported by a verified source) and Condition 2 (source filed in the approved evidence location **and** not marked `[VERIFY]` by the owning rule file) — The Criterion |
| 3 | AND or OR? | **AND**, always |
| 4 | Does content presence alone PASS? | **No** — Distinctions |
| 5 | Does marketplace ownership alone PASS? | **No** — Distinctions |
| 6 | Does naming a source alone PASS? | **No** — Distinctions |
| 7 | Does filing evidence alone necessarily PASS? | **No** — not if the owning rule file still marks the required content or evidence `[VERIFY]` |
| 8 | What if the owning rule file still marks it `[VERIFY]`? | Condition 2 fails, so **Test 2 does not pass**; §E handling applies |
| 9 | Who owns Test 1? | `context/marketplace-routing.md` |
| 10 | Who owns the Test 2 criterion? | **This record** |
| 11 | Who owns PPC rule content? | The four `context/*-rules.md` files |
| 12 | Where is evidence-filing governance? | `evidence/README.md`, per `CLAUDE.md` → *Evidence First* — referenced, not restated |
| 13 | Did this decision change any PPC rule value? | **No** |
| 14 | Did this decision determine which current combinations PASS? | **No** — none is classified |
| 15 | Does this authorise Phase 1b implementation? | **No** |
| 16 | Has Phase 1b started? | **No** |
| 17 | May UK content be copied to DE/FR/IT? | **No** |
| 18 | What is the next safe task? | A separate read-only validation task applying this criterion — Next Step |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** Jathukulan — repository Owner
- **Decision Date:** 2026-07-31
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** **Owner Approved** — criterion only
- **Phase 1b Implementation Authorised:** **NO**
- **Phase 2 Started:** **NO**

---

## Safety Boundary

Per `CLAUDE.md`:

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

This record is documentation. It performs no Amazon Ads action, holds no
credentials, and produces no recommendation to act. No Amazon Ads connection
exists in this repository.
