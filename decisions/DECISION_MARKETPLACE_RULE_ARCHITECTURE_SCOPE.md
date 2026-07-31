<!--
Governance decision record — MARKETPLACE-SCOPE DECISIONS APPROVED; MIGRATION NOT
APPROVED.

This file records three Owner decisions that resolve marketplace-scope questions
raised by a prior read-only marketplace rule architecture discovery. The three
DECISIONS are approved. NOTHING DOWNSTREAM OF THEM IS APPROVED: no migration, no
folder structure, no routing owner, no marketplace rule file, and no rule value.

This record holds NO PPC business-rule value. No threshold, monetary value,
percentage, click gate, ratio, price band, window or formula appears anywhere in
it. Rule content remains owned by its file in context/ and is referenced by path
only. See "Duplicate Truth Prevention".

It is NOT filled from decisions/TEMPLATE_DECISION_RECORD.md's section structure.
That template is scoped to an approved operational PPC decision (with Evidence
References, Related Report and Rollback Reference fields that do not apply to a
governance scope decision). This record follows the structure already established
by the sibling governance decision record in this folder,
DRAFT_DECISION_CONFIDENTIAL_BINARY_EVIDENCE_STORAGE.md, and honours the
template's binding discipline: approved decisions only, business rules never
restated. Whether governance decisions must be re-issued in the template's
structure is an open repository question — see "Known Limitations".

STATUS RECONCILIATION (2026-07-31). This record was created BEFORE the canonical
Phase 1 marketplace-routing architecture was approved, and it originally recorded
CLAUDE.md migration precondition (a) as OPEN. That was correct at the time. It is
no longer current. Precondition (a) is now SATISFIED, and
decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md is the authoritative
owner of current precondition-(a) status and of the approved architecture. This
record's precondition statements are now scoped to their creation date and point
forward to that record. NO Owner marketplace-scope decision was changed and NO
architecture content was copied here. Precondition (b) remains OPEN, migration
remains NOT AUTHORISED, Phase 1 implementation has NOT STARTED, no registry
exists, and no registry path or filename is chosen.

No decision-record filename convention is defined in this repository
(decisions/TEMPLATE_DECISION_RECORD.md -> Known Limitations). The filename below
is descriptive, not conventional. The status inside this document, not the
filename, is authoritative.
-->

# Decision — Marketplace Rule Architecture Scope

**Marketplace-scope decisions: APPROVED. Architecture migration: NOT APPROVED.**

| Field | Value |
|-------|-------|
| Document Type | Governance decision record — **marketplace-scope decisions approved; migration not approved** |
| Approval Status | **OWNER APPROVED** — scope decisions only |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Approved By | **Jathukulan — repository Owner** |
| Approval Date | 2026-07-31 — the date the Owner's decisions were communicated and recorded in this repository. If the underlying decisions were taken on an earlier date, that date is `[VERIFY]`; none is invented here. |
| Decision Owner | Jathukulan |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Created | 2026-07-31 |
| Repository HEAD when created | `cccf54bf79686653814d2c8dc1e92e3abf1087f5` |
| Revised | 2026-07-31 — **status reconciliation only.** `CLAUDE.md` migration precondition **(a)** moved **OPEN → SATISFIED** to match `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` (Owner Approved, committed at `f70a0a8`), which owns that status. Precondition statements in this record are now scoped to their creation date and point forward to that record. **No Owner marketplace-scope decision was changed, no architecture content was copied here, no registry path or filename was introduced, no PPC value was added, and no gap status was changed.** Precondition **(b)** remains **OPEN**; migration remains **NOT AUTHORISED**. |
| Decision Type | Governance / architecture scope — resolves three marketplace-scope questions |
| Approval Scope | **The three marketplace-scope decisions in this record, and nothing else.** |
| Authoritative for | **The three Owner marketplace-scope decisions recorded here, and nothing else.** This record defines no PPC business rule, owns no rule value, approves no structure and authorises no action. |
| Migration Allowed | **NO** — see **Migration Implications** |
| Rule Population Allowed | **NO** — see **Evidence Implications** |

---

## Purpose and Business Question

A prior **read-only** marketplace rule architecture discovery (conducted at
repository HEAD `cccf54bf79686653814d2c8dc1e92e3abf1087f5`) identified **three
marketplace-scope questions** that could not be answered from the repository, from
evidence, or by design work. Each required an Owner decision.

**The business question this record answers:**

> For the four PPC rule families named in the `CLAUDE.md` approved exception, what
> is the Owner's decision on (1) existing marketplace-specific Hour Budget
> content, (2) the marketplace scope of the existing Bid Rules and Budget Rules
> files, and (3) existing US/CA limitation notes?

**Why a record is needed.** Under `CLAUDE.md` → *Queryability First*, an answer
that exists only in conversation cannot be used by another person or LLM
tomorrow. Under the `CLAUDE.md` approved exception, precondition **(b)** requires
a dedicated migration task to be explicitly scoped, reviewed and approved before
execution — that scoping cannot be completed while these three questions are
open. This record closes them, and does nothing else.

---

## Source of the Decision

- **Decision source:** Jathukulan, repository Owner, communicated directly and
  recorded here on 2026-07-31.
- **Question source:** the read-only marketplace rule architecture discovery
  performed at HEAD `cccf54bf79686653814d2c8dc1e92e3abf1087f5`. That discovery
  modified no file and created no file; it is not itself filed in this
  repository. `[VERIFY]` — whether the discovery output should be filed as a
  separate artefact is not decided here.
- **Governing authorisation:** `CLAUDE.md` → **Approved Exception —
  Marketplace-Specific Rule Architecture Migration** (authorised by the Owner on
  2026-07-30). That clause remains the sole authorisation for any future
  migration. **This record does not amend, widen, narrow or reinterpret it.**
- **No external source consulted.** No Amazon Ads data was read, requested or
  filed. No Amazon Ads connection exists.

---

## The Three Categories This Record Keeps Separate

This record deliberately distinguishes three different kinds of statement. They
must never be merged, and no statement of one kind may be used to manufacture a
statement of another.

| Category | What it is | Who owns it | Where it lives |
|----------|------------|-------------|----------------|
| **OWNER DECISION** | A scope judgement the Owner made. It is new truth, and it is what this record owns. It settles *which marketplace an existing rule family belongs to*, and *what may or may not be done* with existing content. | **This record** | This file |
| **EXISTING BUSINESS-RULE CONTENT** | The PPC rule values, conditions, windows and parameters already committed to the repository. This record **does not own, restate, alter, reinterpret or relocate any of it.** An Owner decision about its *scope* changes no value inside it. | The owning file in `context/` | `context/bid-rules.md`, `context/budget-rules.md`, `context/hour-budget-rules.md`, `context/product-pause-rules.md` |
| **FUTURE MARKETPLACE-SPECIFIC EVIDENCE** | Verified, marketplace-specific source material **still required** for DE, FR or IT rule content that has **not yet been supplied** — specifically DE/FR/IT **Bid Rules and Budget Rules** under **Decision 2**. Until it is filed, that content does not exist and must be treated as `[VERIFY]` / unavailable. **This category does not cover DE/FR/IT rule content that already exists:** verified DE/FR/IT **Hour Budget** content is already in the repository and is **preserved under Decision 1**. "Not yet supplied" is assessed **per rule family and per marketplace** — it is never a statement that no DE/FR/IT material exists anywhere. | `evidence/`, per `evidence/README.md`, once filed | Not yet in the repository, for the families named in this row |

**The critical separation:** deciding that an existing rule family *belongs to a
marketplace* (an **Owner decision**) is not the same as *having rule content for
a marketplace* (**existing business-rule content**), and neither of those creates
*rule content for a different marketplace* (**future marketplace-specific
evidence**). Decision 2 below turns on exactly this distinction.

---

# Owner Decisions

## Decision 1 — Hour Budget: Existing Marketplace-Specific Content Is Preserved

**Approved.**

- The currently approved future marketplace architecture covers **UK, DE, FR and
  IT**.
- **Existing verified marketplace-specific Hour Budget content already present
  for DE, FR and IT must be preserved** during any future approved migration.
- **Existing verified DE/FR/IT Hour Budget content must NOT be replaced with
  empty or `[VERIFY]` placeholders.** Where verified marketplace-specific content
  already exists, it is preserved as it is.
- **Existing NL and ES Hour Budget content must not be deleted, rewritten,
  relocated, orphaned or otherwise altered** under the current UK/DE/FR/IT
  migration authorisation.
- **NL and ES remain outside the currently authorised marketplace architecture**
  until separately reviewed and approved.
- **This decision does NOT add NL or ES to the authorised marketplace
  architecture.**

**What this settles.** The `CLAUDE.md` exception states as a binding condition
that *"DE, FR and IT rule files are created empty or `[VERIFY]` and remain so
until real, verified, marketplace-specific evidence exists for that
marketplace."* That condition prohibits **inventing** DE, FR or IT marketplace
content. The discovery found that, for the **Hour Budget family**, verified
DE/FR/IT marketplace-specific content **already exists** in
`context/hour-budget-rules.md`. **Owner Decision 1 requires that existing
verified content be preserved, and not be replaced with empty or `[VERIFY]`
placeholders.**

**Scope of this decision.** The paragraph above records what the Owner decided
about the existing Hour Budget content, and nothing more. It states no general
principle, establishes no reusable interpretation of `CLAUDE.md`, and is not
applied to any other rule family. Every other rule family remains governed by the
`CLAUDE.md` condition exactly as written.

**What this does NOT settle.** How preserved NL/ES content is physically
positioned relative to any future structure is **not decided here**. NL and ES
have no authorised marketplace owner, no authorised parameter file and no
authorised routing destination. If a proposed migration structure cannot preserve
NL/ES content unaltered, that migration is **not** permitted to alter it — the
migration must instead be re-scoped, or NL/ES separately approved, in a later
task.

---

## Decision 2 — Bid Rules and Budget Rules Belong to the UK Marketplace

**Approved.**

- The Owner confirms that the existing **`context/bid-rules.md`** and
  **`context/budget-rules.md`** belong to the **UK marketplace**.
- This is an **Owner decision** resolving the previously undocumented marketplace
  scope of these two existing rule families.
- The existing verified content is therefore the **UK rule content** for those
  families.
- **DE, FR and IT Bid Rules and Budget Rules will be supplied separately** from
  marketplace-specific sources and evidence.
- **No UK Bid Rule or Budget Rule value may be copied, inferred, adapted,
  currency-converted, used as a placeholder, or otherwise used to manufacture a
  DE, FR or IT rule.**
- Until verified DE/FR/IT marketplace-specific rule evidence is supplied, those
  marketplace rule contents **must remain `[VERIFY]` / unavailable**.
- **Those marketplace rule files are not created or populated by this task.**

**What this settles.** The discovery found that neither file states a marketplace
scope anywhere; UK was implied by currency denomination only, and
`context/target-metrics.md` records that same gap independently. Without an Owner
decision, labelling their content "UK" during a migration would have asserted an
undocumented fact about two files that `CLAUDE.md` protects from rewriting. The
Owner has now supplied that fact directly. **It is an Owner decision, recorded
here — it is not derived from the files, and it is not evidence.**

**What this changes inside those two files: nothing.** No value, condition,
wording, ordering or formatting in `context/bid-rules.md` or
`context/budget-rules.md` is altered, reinterpreted or relocated by this
decision. `CLAUDE.md` → *Repository Safety Rules* continues to protect them in
full. The decision establishes **which marketplace the existing content belongs
to**, not **what the existing content says**.

**Scope caution for a future migration.** The discovery observed that
`context/budget-rules.md` is also the authoritative owner of content that is not
a budget rule and not marketplace-scoped (it is cited as authoritative by
`context/campaign-list.md`), and that `context/bid-rules.md` carries at least one
open item that is not a bid rule. **This decision assigns the UK marketplace to
these two rule families. It does not assert that every statement inside those two
files is marketplace-scoped.** Determining what is marketplace-scoped and what is
marketplace-agnostic remains work for the separately-approved migration task, and
is `[VERIFY]` here.

---

## Decision 3 — Existing US/CA Limitation Notes May Be Preserved

**Approved.**

- Existing documentation stating that **US/CA values are unavailable,
  undocumented, `[VERIFY]`, unsupported, or must not be inferred may be
  preserved.**
- Such statements are **exclusion / limitation documentation only**.

**These notes do NOT authorise:**

- US or CA marketplace rule owners;
- US or CA parameter files;
- US or CA PPC business-rule values;
- US or CA routing destinations;
- copying UK, DE, FR or IT values into US or CA;
- adding US or CA to the approved marketplace architecture.

**US remains explicitly outside the current marketplace architecture
authorisation. CA is likewise not authorised by this decision.**

**What this settles.** The `CLAUDE.md` exception states that *"No task acting
under this exception may create, populate or reference US rule content."* The
discovery flagged that existing rule files already carry notes recording that US
and CA values are undocumented and must not be inferred, and asked whether
preserving such a note counts as prohibited referencing. The Owner's decision:
**a statement that content does not exist and must not be invented is a
prohibition, not content.** Preserving it is permitted; it creates nothing.

**A distinction this record deliberately does not collapse.** US and CA reach the
same outcome — **not authorised** — for **different reasons**, and the reasons
must not be merged:

| Marketplace | Reason it is not authorised |
|-------------|------------------------------|
| **US** | **Explicitly excluded.** `CLAUDE.md` names US and states it is excluded by name. |
| **CA** | **Outside scope by omission.** `CLAUDE.md` never names CA. It falls under *"Any marketplace not named above is outside this exception entirely."* |

Treating CA as "excluded like US" would misstate `CLAUDE.md`. Treating CA as
"unmentioned, therefore permissible" would contradict it. Both are wrong; the
table above is the accurate position.

---

## Affected Rule Families

The four rule families named in the `CLAUDE.md` approved exception. Each remains
the sole owner of its own business-rule content; this record changes none of it.

| Rule family | Owning file | Touched by which decision | Content changed by this record |
|-------------|-------------|---------------------------|-------------------------------|
| Bid Rules | `context/bid-rules.md` | Decision 2 (scope = UK) | **None** |
| Budget Rules | `context/budget-rules.md` | Decision 2 (scope = UK) | **None** |
| Hour Budget Rules | `context/hour-budget-rules.md` | Decision 1 (preservation); Decision 3 (existing US/CA notes) | **None** |
| Product Pause Rules | `context/product-pause-rules.md` | Decision 3 (existing US/CA notes) | **None** |

**Product Pause Rules and Decision 2.** Decision 2 names only `context/bid-rules.md`
and `context/budget-rules.md`. It does **not** extend to
`context/product-pause-rules.md`, whose existing content already states its own
marketplace basis. Nothing here restates or reinterprets that.

---

## Affected Marketplaces

| Marketplace | Status after this record | Established by |
|-------------|--------------------------|----------------|
| **UK** | In the currently authorised architecture. Existing Bid Rules and Budget Rules content is UK rule content. | `CLAUDE.md` exception; **Decision 2** |
| **DE** | In the currently authorised architecture. Existing verified Hour Budget content is preserved, not replaced with placeholders. Bid / Budget content does not exist and remains `[VERIFY]` / unavailable pending separate verified evidence. | `CLAUDE.md` exception; **Decisions 1 and 2** |
| **FR** | As DE. | `CLAUDE.md` exception; **Decisions 1 and 2** |
| **IT** | As DE. | `CLAUDE.md` exception; **Decisions 1 and 2** |
| **NL** | **Not** in the currently authorised architecture. Existing content is preserved unaltered. Not added by this record. | **Decision 1** |
| **ES** | **Not** in the currently authorised architecture. Existing content is preserved unaltered. Not added by this record. | **Decision 1** |
| **US** | **Not** authorised — **explicitly excluded** by name. Existing limitation notes may be preserved; they authorise nothing. | `CLAUDE.md` exception; **Decision 3** |
| **CA** | **Not** authorised — **outside scope by omission**; never named in `CLAUDE.md`. Existing limitation notes may be preserved; they authorise nothing. | `CLAUDE.md` exception; **Decision 3** |
| Any other marketplace | Outside this exception entirely. Not addressed by this record. | `CLAUDE.md` exception |

---

## Boundaries

The binding boundaries established or restated by this record.

| # | Boundary |
|---|----------|
| **A** | **UK, DE, FR and IT** are the marketplaces covered by the currently approved future architecture. |
| **B** | Existing **Bid Rules** belong to **UK**. |
| **C** | Existing **Budget Rules** belong to **UK**. |
| **D** | Future **DE/FR/IT Bid and Budget rule content requires separate verified marketplace-specific evidence.** |
| **E** | **UK values must NEVER be used to manufacture DE/FR/IT values** — not by copying, inference, adaptation, currency conversion, placeholder use, example, default or starting point. |
| **F** | **Existing verified DE/FR/IT Hour Budget content must be preserved** — never replaced with empty or `[VERIFY]` placeholders. |
| **G** | **Existing NL/ES Hour Budget content remains preserved** — not deleted, rewritten, relocated, orphaned or altered — **but stays outside the currently authorised architecture.** |
| **H** | **This decision does not authorise NL/ES architecture or routing.** |
| **I** | **Existing US/CA limitation / exclusion / `[VERIFY]` notes may remain.** |
| **J** | **Those notes do not authorise US/CA rules, files, values or routing**, and do not add US or CA to the approved architecture. |
| **K** | **No marketplace architecture migration is authorised for execution by this task.** |
| **L** | **No rule population is authorised by this task.** |

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*, and per
`decisions/TEMPLATE_DECISION_RECORD.md` → *Duplicate Truth Prevention* ("This
template never becomes a source of business rules").

**What this record owns:** the three Owner marketplace-scope decisions above, and
nothing else. That is new truth, and it exists nowhere else in the repository.

**What this record does NOT own, and never becomes:**

- **No PPC business-rule value appears anywhere in this record** — no threshold,
  monetary value, currency amount, percentage, ratio, click gate, order count,
  price band, spend trigger, budget figure, multiplier, ACoS/ROAS value,
  evaluation window or formula. This is verifiable by reading the file: it
  contains none.
- **Rule content remains owned by its file** in `context/`. Owning files are
  referenced **by path only**, never quoted, summarised, paraphrased or restated.
  If this record and an owning `context/` file ever appear to disagree about a
  business rule, **the owning `context/` file wins** — because this record states
  no business rule at all.
- **The `CLAUDE.md` exception remains the sole migration authorisation.** This
  record points to it and does not restate its terms as independent truth. If
  this record and `CLAUDE.md` ever appear to disagree about what is authorised,
  **`CLAUDE.md` wins.**
- **No routing architecture, structure, folder, path, filename or owner is
  defined, named, implied or reserved here.** Those remain entirely for the
  separate design and migration tasks.
- **No marketplace-specific rule is invented.** DE, FR and IT rule content that
  does not exist is described as not existing.
- **No existing `[VERIFY]` is resolved**, other than the three scope questions the
  Owner explicitly answered. No gap is created, closed or narrowed;
  `validation/REPOSITORY_GAP_REGISTER.md` is untouched.

---

## Evidence Implications

- **These decisions are Owner decisions, not evidence.** Decision 2 in particular
  records the Owner's determination of marketplace scope. It is not derived from
  a source document, and it must not be cited as though a source document stated
  it. Its provenance is: **Owner, Jathukulan, 2026-07-31, recorded in this file.**
- **No evidence was filed, ingested, altered or removed by this task.**
  `evidence/` is untouched.
- **DE, FR and IT Bid and Budget rule content requires verified,
  marketplace-specific evidence before it may exist.** Until that evidence is
  supplied and filed in `evidence/` with its source, date and date range per
  `evidence/README.md`, that content is `[VERIFY]` / unavailable. Boundary **E**
  applies without exception.
- **Existing evidence-filing gaps are unchanged.** The rule files that record
  their own primary-source filing status as `[VERIFY]` continue to do so. This
  record neither resolves nor worsens that; it is a live gate on any future rule
  population and remains owned by those files.
- **No rule value may be populated for any marketplace without verified evidence
  for that marketplace** — including UK. Decision 2 assigns existing UK content
  its marketplace scope; it does not add, change or newly verify any UK value.

---

## Migration Implications

**No migration is authorised or performed by this record.**

`CLAUDE.md` requires **both** preconditions before the authorised migration may
execute:

- **(a)** a canonical marketplace-routing design separately completed and
  approved; **and**
- **(b)** a dedicated migration task explicitly scoped, reviewed and approved
  before execution.

**Status as at this record's creation, and current status.** The left column
records the position when this record was created (2026-07-31, HEAD `cccf54b`).
The right column records the position now. **Read the right column for current
state.**

| Precondition | Status as at this record's creation | Current status |
|--------------|--------------------------------------|-----------------|
| **(a)** Canonical marketplace-routing design completed and approved | **OPEN.** A design recommendation existed from the discovery, but it was not approved and was not filed as a repository asset. **Not approved by this record.** | **SATISFIED** — owned by `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md`. **That record is authoritative for this status; this record is not.** |
| **(b)** Dedicated migration task scoped, reviewed and approved | **OPEN.** Not scoped and not approved here. | **OPEN** — unchanged. |

**Migration Allowed: NO.** Both preconditions are required, and **(b)** is OPEN.

**What this record does for the migration:** it removes the three scope blockers
that made precondition **(b)** impossible to scope. That is its entire effect on
migration readiness.

**What a future approved migration must carry forward** — binding, from the
decisions above:

- Existing verified DE/FR/IT Hour Budget content is **preserved**, not
  placeholdered (**F**).
- Existing NL/ES content is **preserved unaltered** and gains **no** authorised
  home, owner or route (**G**, **H**). A structure that cannot preserve it
  unaltered must be re-scoped rather than applied.
- Existing UK content is **preserved by relocation only** where relocation is
  authorised — never deleted, rewritten, summarised or reinterpreted, per
  `CLAUDE.md`.
- **No UK value may seed DE/FR/IT** in any form (**E**).
- **No US or CA owner, file, value or route may be created** (**J**).
- **Routing safety — inherited from `CLAUDE.md`.** Where marketplace is missing,
  ambiguous, or outside the supported scope (including US), the outcome is
  `[VERIFY]` / Insufficient Evidence — **never a UK fallback**. This condition is
  `CLAUDE.md`'s and is restated here by reference only.
- **Evidence boundary — established by Decision 2.** Where a supported
  marketplace has no verified rule content — DE, FR and IT **Bid and Budget**
  rules today — that content remains `[VERIFY]` / unavailable, and **no UK value
  may substitute for it** (**E**). This boundary comes from **Decision 2, not from
  `CLAUDE.md`.** It creates no new rule: the outcome is the same `[VERIFY]` /
  Insufficient Evidence, and never a UK fallback.

**Not authorised by this record:** creating any `context/` folder or marketplace
rule file; designing or creating a canonical routing owner; moving, renaming or
splitting any file; populating DE/FR/IT rule content; modifying any skill;
modifying `CLAUDE.md`; modifying any rule file; modifying
`validation/REPOSITORY_GAP_REGISTER.md`. **None was performed.**

---

## Known Limitations

Genuine unresolved items. None is worked around by inventing data.

1. **Precondition (b) remains OPEN. Precondition (a) is now SATISFIED.** As at
   this record's creation both were OPEN — this record closed scope blockers
   only, and approved no design and no migration task. Precondition **(a)** has
   since been satisfied by
   `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md`, which owns
   that status. Precondition **(b)** is unchanged and still gates migration.
   `[VERIFY]`
2. **Marketplace-agnostic content inside the Bid and Budget rule files is not
   classified.** Decision 2 assigns the two rule *families* to UK; it does not
   assert that every statement inside those files is marketplace-scoped. At least
   one is cited as authoritative by another `context/` file for a
   non-marketplace-scoped purpose. Classification is migration-task work.
   `[VERIFY]`
3. **NL/ES physical treatment under a future structure is undecided.**
   Preservation is binding; positioning is not decided. If a proposed structure
   cannot preserve NL/ES unaltered, it must be re-scoped or NL/ES separately
   approved. `[VERIFY]`
4. **Product Pause marketplace scope is not addressed.** No decision here
   assigns, confirms or alters the marketplace scope of
   `context/product-pause-rules.md` beyond what that file already states.
   `[VERIFY]`
5. **The discovery that raised these questions is not filed** as a repository
   artefact. Whether it should be is not decided here. `[VERIFY]`
6. **Decision-record filename convention undefined** —
   `decisions/TEMPLATE_DECISION_RECORD.md` → Known Limitations. The filename used
   here is descriptive, not conventional. `[VERIFY]`
7. **Approval-status vocabulary undefined** repository-wide (same source).
   `OWNER APPROVED` is used descriptively. `[VERIFY]`
8. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`
9. **Whether governance decisions must be re-issued in the structure of
   `decisions/TEMPLATE_DECISION_RECORD.md`** is an open repository question,
   already raised by the sibling governance record in this folder. `[VERIFY]`
10. **Existing evidence-filing `[VERIFY]` status** on the rule files' primary
    sources is unchanged by this record and remains a gate on any future rule
    population. `[VERIFY]`

---

## Next Step

**Recorded next action — COMPLETED.** The next action recorded by this record was
to produce the **canonical marketplace-routing design** as a separate, reviewable
artefact for Owner approval — satisfying `CLAUDE.md` precondition **(a)** —
incorporating the three decisions recorded here as binding constraints, in
particular the preservation requirements (**F**, **G**), the no-seeding
prohibition (**E**), and the no-US/CA prohibition (**J**). That design has since
been produced and Owner-approved; see
`decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md`.

**For the current next action, read that record. This record does not own it.**

The dedicated migration task (precondition **(b)**) is scoped only **after** that
design is approved. **No migration step may be taken before both preconditions
are satisfied**, and **(b)** is still **OPEN**.

---

## Pass / Fail Rule

This record is **PASS** only if **all** of the following hold. Any single failure
makes it **FAIL**.

| # | Condition | Result |
|---|-----------|--------|
| 1 | Exactly one new decision record created; no existing file modified | **PASS** |
| 2 | No PPC business-rule value copied into this record — no threshold, monetary value, percentage, click gate, window, price band or formula | **PASS** |
| 3 | Bid Rules = UK recorded as an **Owner decision** | **PASS** — Decision 2, Boundary **B** |
| 4 | Budget Rules = UK recorded as an **Owner decision** | **PASS** — Decision 2, Boundary **C** |
| 5 | DE/FR/IT future-evidence requirement explicit | **PASS** — Decision 2, Boundaries **D**, **E** |
| 6 | DE/FR/IT Hour Budget preservation explicit | **PASS** — Decision 1, Boundary **F** |
| 7 | NL/ES preservation **and** out-of-current-scope status both explicit | **PASS** — Decision 1, Boundaries **G**, **H** |
| 8 | US/CA limitation-note preservation explicit | **PASS** — Decision 3, Boundary **I** |
| 9 | No US/CA rule, file, value, route or architecture authorisation exists | **PASS** — Decision 3, Boundary **J** |
| 10 | No marketplace routing file, folder or owner created, named or reserved | **PASS** — none created; no path defined |
| 11 | No rule content moved, renamed, split or populated | **PASS** — Boundaries **K**, **L** |
| 12 | Migration remains **NOT EXECUTED**; both preconditions OPEN *(as at this record's creation — **(a)** is now SATISFIED and **(b)** remains OPEN; see Migration Implications)* | **PASS** — Migration Implications |
| 13 | Owner, date and status recorded | **PASS** — Jathukulan, 2026-07-31, OWNER APPROVED |
| 14 | Owner Decision, Existing Business-Rule Content and Future Marketplace-Specific Evidence kept distinct | **PASS** — "The Three Categories This Record Keeps Separate" |

**Result: PASS** — scope decisions recorded; nothing downstream authorised.

---

## Queryability Test

Using only this record and the files it references by path, can another LLM
answer:

| Question | Answerable? | Where |
|----------|-------------|-------|
| What did the Owner decide, and when? | Yes | Decision Metadata; Owner Decisions |
| Which marketplaces are in the currently approved architecture? | Yes | Affected Marketplaces; Boundary **A** |
| Which marketplace do the existing Bid and Budget rules belong to? | Yes | Decision 2; Boundaries **B**, **C** |
| May UK values be used to create DE/FR/IT rules? | Yes | **No** — Decision 2; Boundary **E** |
| What happens to existing verified DE/FR/IT Hour Budget content? | Yes | **Preserved** — Decision 1; Boundary **F** |
| What happens to existing NL/ES content? | Yes | **Preserved, but outside the authorised architecture** — Decision 1; Boundaries **G**, **H** |
| Are NL, ES, US or CA added to the architecture? | Yes | **No** — Affected Marketplaces; Boundaries **H**, **J** |
| Why are US and CA not authorised — same reason? | Yes | **No** — Decision 3, the US/CA distinction table |
| May existing US/CA limitation notes stay? | Yes | **Yes**, and they authorise nothing — Decision 3; Boundaries **I**, **J** |
| Does this record authorise the migration? | Yes | **No** — Migration Implications; Boundary **K** |
| Does this record authorise populating any rule content? | Yes | **No** — Evidence Implications; Boundary **L** |
| Where do the actual PPC business rules live? | Yes | Duplicate Truth Prevention; Affected Rule Families — the owning `context/` files |
| Does this record contain any rule value? | Yes | **No** — Duplicate Truth Prevention |
| Is precondition (a) still OPEN? | Yes | **No — now SATISFIED**, owned by `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` — Migration Implications |
| Is precondition (b) still OPEN, and is migration allowed? | Yes | **(b) OPEN; migration NOT allowed** — Migration Implications |
| What is the next step? | Yes | Next Step — the recorded next action is **completed**; the current next action is owned by `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` |
| What remains unresolved? | Yes | Known Limitations |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Approved By:** Jathukulan — repository Owner
- **Approval Date:** 2026-07-31
- **Reviewer:** `[VERIFY]` — no Technical / Queryability Reviewer role is defined
  repository-wide (`validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01)
- **Status:** **Owner Approved** — scope decisions only
- **Migration Allowed:** **NO**
- **Rule Population Allowed:** **NO**

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
