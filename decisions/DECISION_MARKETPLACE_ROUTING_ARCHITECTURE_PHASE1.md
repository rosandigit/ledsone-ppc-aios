<!--
Governance decision record — PHASE 1 ARCHITECTURE APPROVED; IMPLEMENTATION NOT
APPROVED.

This file records the Owner's approval of Candidate 3 — Routing-Registry First,
No File Movement in Phase 1 — as the canonical Phase 1 marketplace-routing
architecture. The ARCHITECTURE is approved. NOTHING DOWNSTREAM OF IT IS
APPROVED: no implementation, no registry, no registry filename or path, no
marketplace folder or file, no rule-file movement, no skill change, and no rule
population.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, click gate, ratio, price band, evaluation window, formula or
marketplace parameter appears anywhere in it. Rule content remains owned by its
file in context/ and is referenced by path only. See "Duplicate Truth
Prevention".

WHY THIS IS A SEPARATE RECORD, NOT AN EDIT TO THE EXISTING SCOPE RECORD.
decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md declares in four
places that it is authoritative for "the three Owner marketplace-scope
decisions recorded here, and nothing else", and its Decision Type, Approval
Scope, Pass/Fail Rule and Queryability Test are each built around exactly those
three scope decisions. The decision recorded here is a fourth decision of a
DIFFERENT KIND — an architecture approval, not a scope resolution. Recording it
inside that file would contradict that file's own scope statement. The two
records own different things; see "Relationship to Existing Decision Records".

It is NOT filled from decisions/TEMPLATE_DECISION_RECORD.md's section structure.
That template is scoped to an approved operational PPC decision (Evidence
References, Related Report and Rollback Reference do not apply to a governance
architecture approval). This record follows the structure established by the two
sibling governance decision records in this folder and honours the template's
binding discipline: approved decisions only, business rules never restated.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename is
descriptive, not conventional. The status inside this document, not the
filename, is authoritative.
-->

# Decision — Marketplace-Routing Architecture, Phase 1

**Phase 1 architecture: APPROVED. Phase 1 implementation: NOT APPROVED.
Migration: NOT AUTHORISED.**

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — **Phase 1 architecture approved; implementation not approved** |
| Approval Status | **OWNER APPROVED** — architecture only |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | **Jathukulan — repository Owner** |
| Decision Date | 2026-07-31 |
| Approval Date | 2026-07-31 — the date the Owner's approval was communicated and recorded in this repository. If the underlying decision was taken on an earlier date, that date is `[VERIFY]`; none is invented here. |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-07-31 |
| Repository HEAD when created | `9fc36397f746c14587743930093f7a4112e6a3a6` |
| Decision Type | Governance / architecture approval — canonical Phase 1 marketplace-routing design |
| Approval Scope | **The Phase 1 architecture decision recorded here, and nothing else.** |
| Authoritative for | **The approved Phase 1 marketplace-routing architecture, and nothing else.** This record defines no PPC business rule, owns no rule value, originates no marketplace authorisation, names no file path, and authorises no action. |
| Implementation Allowed | **NO** — see **J. Implementation Status** |
| Rule Population Allowed | **NO** — see **J. Implementation Status** |
| Migration Allowed | **NO** — see **K. Precondition Status** |

---

## Purpose and Business Question

`CLAUDE.md` → **Approved Exception — Marketplace-Specific Rule Architecture
Migration** requires, as precondition **(a)**, that *"a canonical
marketplace-routing design has been separately completed and approved"* before
any migration may execute. A read-only discovery task completed that design work
separately and recommended one architecture. The Owner has now approved it.

**The business question this record answers:**

> Which canonical marketplace-routing architecture has the Owner approved for
> Phase 1, what does that approval permit, and — precisely — what does it not
> permit?

**Why a record is needed.** Under `CLAUDE.md` → *Queryability First*, an approval
that exists only in conversation cannot be used by another person or LLM
tomorrow. Two specific risks make a durable record necessary here:

1. **Approval could be mistaken for permission to build.** Without an explicit
   record, a later reader seeing "Candidate 3 approved" could begin creating the
   registry. Section **J** forecloses that.
2. **Deferral could be mistaken for cancellation.** Phase 1 deliberately performs
   no file movement. Without an explicit record, a later reader could conclude
   the Manager-required family → marketplace-specific rule structure was
   rejected. Section **I** forecloses that.

---

## Source of the Decision

- **Decision source:** Jathukulan, repository Owner, communicated directly and
  recorded here on 2026-07-31.
- **Design source:** the read-only canonical marketplace-routing architecture
  discovery performed at HEAD `9fc36397f746c14587743930093f7a4112e6a3a6`. That
  discovery modified and created no file. **Its full analysis — the candidate
  comparison, dependency classification and migration impact map — is not filed
  as a repository artefact.** The binding substance of the approved architecture
  is captured in sections **A**–**J** below; the surrounding analysis is not.
  `[VERIFY]` — whether the fuller discovery output should be filed separately is
  not decided here.
- **Governing authorisation:** `CLAUDE.md` → **Approved Exception —
  Marketplace-Specific Rule Architecture Migration** (authorised by the Owner on
  2026-07-30). That clause remains the sole authorisation for any future
  migration. **This record does not amend, widen, narrow or reinterpret it.**
- **Governing marketplace scope:**
  `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` (Owner Approved,
  2026-07-31, committed at `9fc3639`). That record remains the sole owner of the
  marketplace-scope decisions. **This record does not amend, widen, narrow or
  reinterpret them.**
- **No external source consulted.** No Amazon Ads data was read, requested or
  filed. No Amazon Ads connection exists.

---

## Relationship to Existing Decision Records

Three governance records now exist. Each owns something different, and none may
be read as owning another's subject.

| Record | Owns | Does NOT own |
|--------|------|--------------|
| `CLAUDE.md` → Approved Exception | The **migration authorisation** itself: which four rule families, which four marketplaces, US exclusion, the binding conditions, and preconditions (a) and (b). | Any architecture, structure or routing design. It states explicitly that it approves *"no folder or file layout"*. |
| `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` | The **three Owner marketplace-scope decisions**: existing Hour Budget marketplace content and NL/ES treatment; the UK marketplace scope of the existing Bid and Budget rule families; existing US/CA limitation-note treatment. | Any architecture or routing design. It records precondition (a) as OPEN as at its own creation. |
| **This record** | The **approved Phase 1 marketplace-routing architecture**: the Phase 1 structural boundary, the separation of authorisation from content availability, the future registry's responsibilities and prohibitions, and the routing outcome model. | Any marketplace-scope decision, any business-rule value, any file path, and any implementation permission. |

**Conflict rule.** On marketplace scope, `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` **wins**. On migration authorisation and preconditions, `CLAUDE.md` **wins**. On any PPC business rule, the owning file in `context/` **wins** — because this record states none.

---

# Owner Decision

## A. Owner Approval

**Approved.**

> **Candidate 3 — Routing-Registry First, No File Movement in Phase 1 — is
> approved as the canonical Phase 1 marketplace-routing architecture.**

Approved by **Jathukulan, repository Owner**, on **2026-07-31**, as the
**architecture** only.

---

## B. Phase 1 Purpose

Phase 1 introduces a **canonical routing-registry architecture** so that runtime
marketplace routing can distinguish two facts:

1. **whether a marketplace is authorised**; and
2. **whether verified rule content exists for that rule family and that
   marketplace.**

**These are independent facts and must never be collapsed into a single test.**

A marketplace may be authorised while no verified content exists for a given rule
family. Verified content may exist for a marketplace that is not authorised.
Neither fact implies the other, in either direction. Any routing test that
evaluates only one of them is incorrect under this architecture.

---

## C. Phase 1 Structural Boundary

**Phase 1 performs NO structural split of the four rule families.**

The existing rule-family files remain in their current locations during Phase 1:

- `context/bid-rules.md`
- `context/budget-rules.md`
- `context/hour-budget-rules.md`
- `context/product-pause-rules.md`

**This approval does not authorise moving, renaming, splitting or reorganising
those files.** They remain protected by `CLAUDE.md` → *Existing Asset First* and,
for the first two, by the Repository Safety Rules that name them.

---

## D. Routing Registry Responsibility

The future registry, once separately scoped and approved for implementation, may
**operationalise** approved marketplace authorisation and route consumers to
existing authoritative rule owners.

**It does NOT originate marketplace authorisation.**

- Authorisation originates in `CLAUDE.md` → Approved Exception and in
  `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md`. The registry
  **cites and uses** those owners; it never becomes a competing authorisation
  source. If the registry and an authorisation owner ever appear to disagree,
  **the authorisation owner wins.**
- **The registry must not own, duplicate or restate PPC business-rule values,
  thresholds, conditions, formulas, evaluation windows or marketplace
  parameters.** Those remain owned solely by the rule files in `context/`.

**The registry's exact filename and path remain `[VERIFY]`** until separately
scoped and approved for implementation. **No path is chosen, proposed, reserved
or implied by this record.**

---

## E. Routing Model

Approved routing behaviour, stated conceptually. **This section records
architecture behaviour only. It contains no code, no mapping, no registry row and
no business-rule content.**

| Input state | Outcome |
|-------------|---------|
| Marketplace **authorised** and verified rule content **exists** | **Route** to the existing authoritative rule owner |
| Marketplace **authorised**, verified rule content **unavailable** | **`[VERIFY]` / Insufficient Evidence** |
| Marketplace **missing** or **ambiguous** | **`[VERIFY]` / Insufficient Evidence** |
| Marketplace **outside authorised scope** | **Unsupported / out of scope** |
| **Rule family unsupported** | **No route invented** |

`[VERIFY]` / Insufficient Evidence and unsupported / out of scope are **distinct
outcomes** and must not be merged: the first records an evidence gap within
authorised scope, the second records an authorisation boundary.

---

## F. No UK Fallback

**Missing, ambiguous, unsupported or unverified marketplace state must never
default to UK.**

**Existing UK content must not be used to manufacture another marketplace's
content.**

This applies without exception, to every rule family, at every point in the
routing model above. There is no condition under which a request that is not an
explicit, authorised UK request resolves to UK content.

---

## G. NL / ES

- **Existing verified NL/ES Hour Budget content must remain preserved.**
  Preservation is owned by
  `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` → Decision 1 and is
  not restated, widened or narrowed here.
- **NL and ES are not thereby authorised routing destinations** under the
  approved UK/DE/FR/IT architecture.
- **Content existence does not equal marketplace authorisation.**

This is the routing consequence of the separation established in section **B**,
and it is what this record owns. A routing test keyed only to whether content
exists would treat NL and ES as valid destinations. Under this architecture it
must not, because the authorisation fact is evaluated independently and NL and ES
are not authorised.

---

## H. US / CA

The already approved scope treatment in
`decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` → Decision 3 is
**preserved unchanged**. It is **not widened and not reinterpreted** here, and it
remains authoritative; if this record and that record ever appear to disagree,
**that record wins.**

**No US or CA routing destination, rule owner or rule content is authorised by
this Phase 1 approval.**

US and CA reach the same outcome for **different reasons**, and that distinction
is owned by the record named above and is not collapsed here.

---

## I. Manager Requirement / Phase 2

**The Manager-required family → marketplace-specific rule structure remains the
intended Phase 2 direction.**

**Candidate 3 does NOT cancel, reject, replace or supersede that requirement.**

Phase 1 **deliberately defers** file movement and splitting until a separate
Phase 2 design and migration task is approved **and** the relevant marketplace
evidence and structural questions are resolved.

Deferral is not cancellation. A later reader who finds that Phase 1 moved no file
must not conclude that the marketplace-specific structure was rejected. It was
**postponed**, and it remains the intended direction.

**Phase 2 is not designed in this record**, and nothing here approves any Phase 2
structure, layout, path or sequence.

---

## J. Implementation Status

**Architecture approval does NOT equal implementation approval.**

**Nothing may be built on the strength of this record.** Specifically, this
approval does not permit:

- creating the routing registry;
- choosing, proposing or reserving the registry's filename or path;
- creating any marketplace folder or file;
- moving, renaming, splitting or reorganising any rule file;
- changing any skill's routing, validation or marketplace behaviour;
- changing any document's routing behaviour;
- populating DE, FR or IT rule content;
- creating any US, CA, NL or ES routing destination;
- modifying `CLAUDE.md`, any `context/` file, any `skills/` file, or
  `validation/REPOSITORY_GAP_REGISTER.md`.

**A separate bounded implementation task must be explicitly scoped, reviewed and
approved before Phase 1 implementation begins.** None exists.

**Phase 1 implementation status: NOT STARTED.**

---

## K. Precondition Status

`CLAUDE.md` → *Preconditions — both required before any migration executes*
states that the authorised migration may execute **only after both** of the
following are complete:

> **(a)** a canonical marketplace-routing design has been separately completed
> and approved; **and**
>
> **(b)** a dedicated migration task has been explicitly scoped, reviewed and
> approved before execution.

| Precondition | Status |
|--------------|--------|
| **(a)** Canonical marketplace-routing design separately completed and approved | **SATISFIED** — by Owner approval of the canonical Phase 1 design recorded in sections **A**–**J**. The design was **separately completed** by a discovery task that was not the authorising clause and not the migration, and it is now **approved** by the Owner. |
| **(b)** Dedicated migration task explicitly scoped, reviewed and approved | **OPEN** — no migration task is scoped, reviewed or approved. Not satisfied here, and this record must never be read as satisfying it. |

**Qualification on (a), stated plainly.** (a) is recorded as satisfied on the
basis that sections **A**–**J** of this record durably capture the **binding
substance** of the approved architecture — the Phase 1 boundary, the separation
of authorisation from content availability, the registry's responsibilities and
prohibitions, and the routing outcome model. The **surrounding discovery
analysis** that led to the recommendation is not filed as a repository artefact
(see **Source of the Decision** and **Known Limitations**). A reader who requires
that comparative analysis will not find it in this repository.

**Migration Allowed: NO.** Both preconditions are required. (b) is OPEN,
therefore the migration may not execute, and the four rule files remain
untouched.

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the approved Phase 1 marketplace-routing architecture,
and nothing else. That is new truth, and it exists nowhere else in the
repository.

**What this record does NOT own, and never becomes:**

- **No PPC business-rule value appears anywhere in this record** — no threshold,
  monetary value, currency amount, percentage, ratio, click gate, order count,
  price band, spend trigger, budget figure, multiplier, ACoS/ROAS value,
  evaluation window, formula or marketplace parameter. This is verifiable by
  reading the file: it contains none.
- **Rule content remains owned by its file** in `context/`. Owning files are
  referenced **by path only**, never quoted, summarised, paraphrased or restated.
  If this record and an owning `context/` file ever appear to disagree about a
  business rule, **the owning `context/` file wins** — because this record states
  no business rule at all.
- **Marketplace authorisation is not originated here.** It remains owned by
  `CLAUDE.md` and `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md`,
  which are cited and never restated as independent truth. The future registry
  operationalises that authorisation; neither it nor this record becomes a
  competing authorisation source.
- **No marketplace-scope decision is made, amended or reinterpreted here.**
  Sections **G** and **H** point to the owning record and change nothing in it.
- **No file path, filename, folder or structure is defined, named, chosen,
  reserved or implied**, including the registry's own. All remain `[VERIFY]`.
- **No Phase 2 structure is designed or approved.**
- **No existing `[VERIFY]` is resolved** other than the architecture question the
  Owner explicitly answered. No gap is created, closed or narrowed;
  `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Known Limitations

Genuine unresolved items. None is worked around by inventing data.

1. **Precondition (b) remains OPEN.** No migration task is scoped or approved.
   Migration may not execute. `[VERIFY]`
2. **Phase 1 implementation is not scoped.** A separate bounded task is required
   before anything is built. `[VERIFY]`
3. **Stale precondition label in the sibling scope record.**
   `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` records
   precondition (a) as **OPEN**, which was accurate when that record was created
   and is superseded by section **K** of this record. That file was deliberately
   **not** edited by this task, which was bounded to a single `decisions/` asset.
   **This record is authoritative for precondition (a) status.** Reconciling the
   older record's label is a separate documentation task. `[VERIFY]`
4. **The fuller discovery analysis is not filed.** The candidate comparison,
   dependency classification and migration impact map exist only outside the
   repository. Whether they should be filed is not decided here. `[VERIFY]`
5. **Registry filename and path undecided.** Deliberately `[VERIFY]`; not chosen
   here. `[VERIFY]`
6. **Phase 2 design does not exist.** Deferred, not cancelled — see section
   **I**. `[VERIFY]`
7. **Decision-record filename convention undefined** —
   `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
   here is descriptive, not conventional. `[VERIFY]`
8. **Approval-status vocabulary undefined** repository-wide (same source).
   `OWNER APPROVED` is used descriptively. `[VERIFY]`
9. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
10. **Structural questions blocking Phase 2 remain open**, including which
    content inside the existing rule files is marketplace-scoped and which is
    marketplace-agnostic. Not resolved here. `[VERIFY]`

---

## Next Step

**One next action.** Scope a **bounded Phase 1 implementation task** for separate
Owner review and approval — covering the registry's creation and the consumers
that would route through it — with its filename and path proposed for approval
rather than assumed.

That task is **not** the migration. Migration remains gated on precondition
**(b)**, which stays OPEN.

---

## Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one `decisions/` asset created or changed; no other file modified | **PASS** |
| 2 | No PPC business-rule value copied into this record | **PASS** |
| 3 | Candidate 3 Phase 1 recorded as **Owner Approved** | **PASS** — section **A** |
| 4 | Authorisation and verified-content availability recorded as **independent** facts | **PASS** — section **B** |
| 5 | Phase 1 structural boundary explicit — no split, no movement | **PASS** — section **C** |
| 6 | Registry recorded as **not** originating authorisation, and **not** owning rule values | **PASS** — section **D** |
| 7 | Registry filename/path left `[VERIFY]`, not invented | **PASS** — section **D** |
| 8 | Routing model records all five outcome states | **PASS** — section **E** |
| 9 | No UK fallback, and no UK content used to manufacture another marketplace | **PASS** — section **F** |
| 10 | NL/ES preserved; **not** authorised destinations; content ≠ authorisation | **PASS** — section **G** |
| 11 | US/CA treatment preserved, not widened or reinterpreted; no US/CA routing authorised | **PASS** — section **H** |
| 12 | Manager Phase 2 requirement explicitly **preserved**, not cancelled | **PASS** — section **I** |
| 13 | Implementation explicitly **not** authorised; Phase 1 **NOT STARTED** | **PASS** — section **J** |
| 14 | Precondition (a) SATISFIED with its basis stated; (b) OPEN; migration **not** allowed | **PASS** — section **K** |
| 15 | Owner, date and status recorded | **PASS** — Jathukulan, 2026-07-31, OWNER APPROVED |

**Result: PASS** — Phase 1 architecture approved; nothing downstream authorised.

---

## Queryability Test

Using only this record and the repository owners it references by path, can
another LLM answer:

| # | Question | Answerable? | Answer / Where |
|---|----------|-------------|----------------|
| 1 | Which architecture did the Owner approve? | Yes | **Candidate 3 — Routing-Registry First, No File Movement in Phase 1** — section **A** |
| 2 | Is it Phase 1 or Phase 2? | Yes | **Phase 1** — sections **A**, **I** |
| 3 | Does Phase 1 move or split the rule files? | Yes | **No** — section **C** |
| 4 | What two independent states must routing evaluate? | Yes | **Marketplace authorised?** and **verified content exists?** — section **B** |
| 5 | Does content existence alone authorise routing? | Yes | **No** — sections **B**, **G** |
| 6 | Can NL/ES route merely because Hour Budget content exists? | Yes | **No** — section **G** |
| 7 | Can a missing marketplace default to UK? | Yes | **No** — sections **E**, **F** |
| 8 | Does the registry own PPC rule values? | Yes | **No** — section **D** |
| 9 | Does the registry originate marketplace authorisation? | Yes | **No** — it cites and uses the existing owners — section **D** |
| 10 | Are US or CA authorised by this decision? | Yes | **No** — section **H** |
| 11 | Does Candidate 3 cancel the Manager-required marketplace-file structure? | Yes | **No — deferred to Phase 2, not cancelled** — section **I** |
| 12 | Is Phase 1 implemented yet? | Yes | **No — NOT STARTED** — section **J** |
| 13 | Is migration currently authorised to execute? | Yes | **No** — precondition (b) OPEN — section **K** |
| 14 | What remains before implementation? | Yes | A separately scoped, reviewed and approved bounded Phase 1 implementation task — sections **J**, **Next Step** |
| 15 | What remains for Phase 2? | Yes | The family → marketplace-specific rule structure, pending its own design and migration approval plus marketplace evidence and structural questions — sections **I**, Known Limitations 6 and 10 |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** Jathukulan — repository Owner
- **Decision Date:** 2026-07-31
- **Approval Date:** 2026-07-31
- **Reviewer:** `[VERIFY]` — no Technical / Queryability Reviewer role is defined
  repository-wide (`validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01)
- **Status:** **Owner Approved** — architecture only
- **Implementation Allowed:** **NO**
- **Rule Population Allowed:** **NO**
- **Migration Allowed:** **NO**

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
