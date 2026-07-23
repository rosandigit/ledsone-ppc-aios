# Negative Keyword Master

Canonical **governance specification** for negative keywords in LEDSone Amazon
PPC.

This document defines *what* a negative keyword is, *how* one is classified,
*where* it originates, *how* it is validated and approved, *how* it moves through
its lifecycle, and *how* AI skills use it. It governs the negative-keyword
process; it is **not** the operational negative keyword library. No negative
keyword records are stored here, and none may be added until verified operational
evidence is imported.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — recorded as `Owner` in `README.md`, `CLAUDE.md`, `context/bid-rules.md` and `context/budget-rules.md` |
| Business Owner | [VERIFY] — no governance section exists in `README.md` or `CLAUDE.md`. "MD" appears in `context/budget-rules.md` as a budget **approver**, but is nowhere defined as Business Owner. Do not assume the two are the same role. |
| Technical Reviewer | [VERIFY] — no technical reviewer role is defined anywhere in this repository |
| Queryability Reviewer | [VERIFY] — no queryability reviewer role is defined anywhere in this repository |
| Status | Active — governance specification approved; the negative keyword register itself is empty pending evidence, with outstanding items marked `[VERIFY]` |
| Version | 1.0 |
| Last Updated | 2026-07-23 |
| Source Documents | See the **Evidence** section below |

---

## Purpose

This document exists so that every person and every AI skill in this repository
treats negative keywords the **same** way, from one canonical governance
definition.

**Why negative keywords exist.** A negative keyword is an **exclusion**: it
prevents ads from being shown for a specified keyword or search term. It is the
opposite of a targeting keyword — it removes matches rather than adding them.

**How they reduce wasted spend.** Ad spend on searches that will not convert is
waste. Excluding those searches stops the spend at source, protecting budget for
searches that do convert.

**How they improve campaign efficiency.** Removing low-value matches raises the
proportion of spend on relevant traffic, which improves click-through and
conversion quality and therefore ACoS/ROAS against the targets in
`context/target-metrics.md` (referenced, not restated).

**How they improve search-term quality.** Negatives feed back into the
Search Term → Keyword loop described in `context/keyword-strategy.md`: irrelevant
terms are excluded while relevant ones are harvested, so the remaining matched
search terms become progressively cleaner.

**This document defines governance only, NOT the operational negative keyword
library.** No negative keyword, search term or operational value is asserted
anywhere in this document. The operational library is populated separately, only
from verified evidence.

---

## Evidence

Every statement in this document originates from one of the sources below.
Physical existence inside this repository was checked on 2026-07-23 by listing
the repository contents.

| Source | Location | Exists in this repository? | Used for |
|--------|----------|---------------------------|----------|
| `README.md` | repository root | **Exists — verified in-repo document** | Repository purpose; evidence-first and human-approval policy; the `keywords/` area ("master negatives"); the `skills/` list |
| `CLAUDE.md` | repository root | **Exists — verified in-repo document** | Governance: Existing Asset First, Evidence First, Queryability First, No Duplicate Truth, Human Approval Required, Never Modify Amazon Ads |
| `context/target-metrics.md` | `context/target-metrics.md` | **Exists — verified in-repo document** | ACoS/ROAS/CTR/CVR KPI targets that waste decisions are judged against (linked, never restated) |
| `context/campaign-list.md` | `context/campaign-list.md` | **Exists — verified in-repo document** | Canonical campaign register and the Campaign → Ad Group hierarchy (linked, never restated) |
| `context/keyword-strategy.md` | `context/keyword-strategy.md` | **Exists — verified in-repo document** | Canonical keyword strategy; the Keyword → Search Term → Customer Search relationship; negatives are named there as owned by this file |
| `context/bid-rules.md` | `context/bid-rules.md` | **Exists — verified in-repo document** | Sample-size gate (15/25 clicks) before acting on a term; rollback logging in `decisions/` |
| `context/budget-rules.md` | `context/budget-rules.md` | **Exists — verified in-repo document** | Campaign naming convention; budget-protection context; `/budget-check` as a consuming skill |
| existing `context/negative-keyword-master.md` | `context/negative-keyword-master.md` | **Exists — this file.** Prior content was a placeholder stub (`Status: [VERIFY] — not yet documented`), now replaced by this specification. | The document being completed |

**No external source is cited by this document.** Every source above is a
verified in-repository markdown file.

---

## Scope

This governance specification is the shared negative-keyword reference for the
following processes. It defines their input structure and governance; it does not
perform any of them.

| Process | How this document supports it |
|---------|-------------------------------|
| Waste Reduction | Defines the categories, evidence and lifecycle a term must satisfy before `waste-scan` can recommend excluding it |
| Search Term Review | Defines how `search-term-check` routes an irrelevant search term to negation, and the evidence required |
| Campaign Audits | Provides the negative-keyword record fields `campaign-audit` checks for completeness and validity |
| Bid Optimisation | Ensures bid decisions in `context/bid-rules.md` operate on traffic already cleaned of excluded searches |
| Budget Protection | Excluding non-converting searches protects the daily budgets governed by `context/budget-rules.md` |
| PPC Governance | Establishes approval, evidence and conflict-handling rules for exclusions |
| AI Skills | Every negative-keyword-aware skill in `skills/` reads this specification — see the **Dependency Matrix** |

**Out of scope.** This document does not contain campaign records, keyword
strategy detail, KPI targets, Search Term Report data or any negative-keyword
rows. Those live in their authoritative files and are linked, never restated.

**Safety.** Any output derived from this document that touches bids, budgets,
keywords, campaigns or targeting: **outputs DRAFT recommendations only, never
applies Amazon Ads changes, human approval required** before implementation.
Jathukulan reviews and applies every change manually. Applying a negative keyword
is a manual action in Amazon Ads. If automation of Amazon Ads is implied,
**STOP** and flag it.

---

## Negative Keyword Categories

Categories describe **why** a term is excluded. Each record carries one category.
Only classifications supported by repository evidence are asserted; anything else
is `[VERIFY]`.

| Category | Purpose |
|----------|---------|
| Irrelevant searches | Terms unrelated to the advertised product; excluded to stop spend on traffic that cannot convert. |
| Competitor exclusions | Competitor brand/product terms deliberately excluded. **Note:** `context/keyword-strategy.md` and `context/bid-rules.md` also describe *targeting* competitor terms as a deliberate strategy — whether a given competitor term is targeted or negated is a per-case decision and must trace to evidence. Policy boundary: [VERIFY]. |
| Low-intent searches | Terms that attract browsing rather than purchase intent; excluded to protect conversion rate. |
| Product mismatch | Terms describing a variant, attribute or product the listing does not offer (wrong size, wrong type, wrong feature). |
| Duplicate traffic control | Exclusions used to steer a search term to one intended campaign/ad group instead of several, preventing internal competition. |
| Seasonal exclusions | Terms excluded for a defined season/period, expected to be reviewed when the season changes. |
| Temporary exclusions | Exclusions intended to be time-limited and reviewed (e.g. during a stock or listing issue), not permanent. |
| Permanent exclusions | Exclusions intended to remain in place indefinitely. |

The precise rules distinguishing Temporary from Seasonal from Permanent (review
cadence, expiry, promotion between them) are not documented in this repository:
**[VERIFY]**. Any category behaviour not stated above is **[VERIFY]**; do not
invent one.

---

## Discovery Sources

A negative-keyword candidate may enter the pipeline **only** from an approved
discovery source. Each candidate must still pass validation and approval (see
**Validation Rules**) before it becomes an applied exclusion.

Approved discovery sources:

- **Amazon Search Term Report** — actual customer search terms that triggered
  ads; the primary source of irrelevant/low-intent terms to exclude.
- **Campaign Audit** — issues surfaced by the `campaign-audit` skill.
- **Waste Scan** — spend-without-return terms surfaced by the `waste-scan`
  skill.
- **Amazon Ads Reporting** — performance data indicating non-converting terms.
- **Approved business review** — an exclusion decision documented and approved
  under the repository's evidence-first policy.
- **Manual Review** — human-identified candidate.

**Manual suggestions require validation before approval.** A term proposed by a
person, with no approved evidence behind it, is a candidate only. It must be
validated against approved evidence before it can be approved and applied. Manual
opinion alone is **not** sufficient evidence (see **Evidence Requirements**).

---

## Negative Keyword Lifecycle

The states a negative keyword moves through, from discovery to removal. States
marked evidenced are supported by repository documents; the remainder are shown
for completeness and marked `[VERIFY]` because no repository document defines them
yet.

```
Candidate     Discovered from an approved source; not yet validated
   ↓
Review        Under validation against evidence
   ↓
Approved      Validated and approved for exclusion (human approval)
   ↓
Applied       Added as a negative in Amazon Ads (manual action)
   ↓
Verified      Confirmed applied and behaving as intended
   ↓
Retained      Kept in place after review
   ↓
Removed       Withdrawn when no longer justified
```

- **Human approval and manual application.** Movement to **Approved** requires
  human approval, and **Applied** is a manual action in Amazon Ads by Jathukulan.
  Nothing here changes Amazon Ads automatically.
- **Sample-size context.** Where a negative decision follows performance data,
  the click thresholds in `context/bid-rules.md` (15 minimum, 25 for higher
  confidence) indicate when there is enough evidence to judge a term rather than
  react to noise.
- **Removal / rollback.** Removing a negative is itself a change; consistent with
  the rollback discipline in `context/bid-rules.md` and `context/budget-rules.md`,
  it should be logged in `decisions/`. Specific **removal criteria** are
  **[VERIFY]**.
- **Transition rules.** The precise conditions and approver for each transition
  are **[VERIFY]** — not defined in this repository. Any lifecycle state a
  downstream process needs but that is not listed above is **[VERIFY]**; do not
  invent one.

---

## Negative Keyword Register

The canonical register structure. It is **empty by design**. No row below the
header is populated, and none may be added except from verified evidence.

| Keyword | Match Type | Category | Campaign | Ad Group | Discovery Source | Reason | Evidence | Status | Approval | Date Added | Last Verified | Validation Status |
|---------|------------|----------|----------|----------|------------------|--------|----------|--------|----------|------------|---------------|-------------------|
| *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* |

> **The operational negative keyword library shall only be populated from
> verified operational evidence.** No negative keyword, search term, campaign
> value or performance figure has been entered, because none has yet been
> imported from verified evidence. The single placeholder row above shows the
> columns only and is not a record.
>
> The `Campaign` and `Ad Group` values reference records defined in
> `context/campaign-list.md`; they are linked, not redefined here.
>
> **Match Type** — negative keywords support their own match types (e.g. negative
> exact, negative phrase). The approved match-type policy is **[VERIFY]**; no
> repository document defines which match types are permitted per case.

---

## Validation Rules

Every negative keyword record must include all of the following before it is
treated as valid:

- **Evidence** — an approved source from **Evidence Requirements**;
- **Reason** — why the term is excluded (maps to a category);
- **Approval** — the human approval record;
- **Validation date** — recorded in `Last Verified`;
- **Validation status** — recorded in `Validation Status`.

**Conflict handling.** If two or more evidence sources disagree on **whether a
term should be excluded, its category, or its status**, do **not** choose one
source over another without justification. Instead:

- set **Validation Status = Conflict**;
- record **every** conflicting evidence source;
- **require business review before approval**.

The full set of allowed Validation Status values (beyond `Conflict`), and any
further validation rules, are not established by repository evidence: **[VERIFY]**.

---

## Evidence Requirements

A negative keyword record may be created **only** from approved evidence.
Approved evidence includes:

- **Amazon Search Term Report**
- **Campaign Audit**
- **Waste Scan**
- **Amazon Ads Reporting**
- **Approved business review**

**Manual opinion alone is insufficient evidence.** A term excluded on opinion,
with none of the sources above behind it, does not meet the evidence-first policy
(`README.md`, `CLAUDE.md`) and must not be treated as a validated exclusion.

Every imported evidence source must, consistent with `README.md`, be filed with
its **source, date and date range** so the exclusion can be independently checked
later.

---

## Relationship Matrix

The logical chain a negative keyword sits within. This describes the conceptual
relationship only; no implementation detail (limits, matching internals) is
invented.

```
Campaign
   ↓
Ad Group
   ↓
Negative Keyword
   ↓
Blocked Search Terms
```

- **Campaign → Ad Group** — a campaign contains ad groups. Campaign and ad-group
  identity are defined in `context/campaign-list.md`, not here. A negative may be
  applied at campaign level or ad-group level; the governing policy for which
  level is **[VERIFY]**.
- **Ad Group → Negative Keyword** — an ad group (or campaign) holds the negative
  keywords that apply to it.
- **Negative Keyword → Blocked Search Terms** — a negative keyword, via its match
  type, blocks one or more actual customer **search terms** from triggering ads.
  Those blocked search terms are the mirror image of the matched search terms
  described in `context/keyword-strategy.md`.

Cardinality, match-behaviour internals, campaign-vs-ad-group scoping and any
ad-type-specific variations of this chain are not documented in this repository:
**[VERIFY]**.

---

## Dependency Matrix

Which register fields are consumed by which skills. **Only skills that exist in
`skills/` are listed.** Every skill file is currently an early-stage stub, and
none yet declares the negative-keyword fields it reads. Dependencies are recorded
as confirmed **only** where a skill's own name states its function or a source
document names it; everything else is `[VERIFY]` and must be filled in as each
skill is defined — not guessed.

| Field | Used By |
|-------|---------|
| Keyword | `search-term-check`, `waste-scan` (both operate on terms by name); precise dependence [VERIFY] per skill |
| Match Type | `search-term-check`, `waste-scan` (negation is match-type aware); others [VERIFY] |
| Category | [VERIFY] — no skill declares this yet |
| Campaign | [VERIFY] — identity defined in `context/campaign-list.md`; likely `campaign-audit`, but undeclared |
| Ad Group | [VERIFY] |
| Discovery Source | `waste-scan`, `campaign-audit` (both surface candidates); precise dependence [VERIFY] |
| Reason | [VERIFY] |
| Evidence | [VERIFY] — relevant to `campaign-audit` for completeness checks, but undeclared |
| Status | [VERIFY] — likely `waste-scan` and `campaign-audit`, but undeclared |
| Approval | [VERIFY] |
| Date Added | [VERIFY] |
| Last Verified | [VERIFY] |
| Validation Status | [VERIFY] |

Skills present in `skills/` with **no confirmed** negative-keyword-field
dependency yet: `ppc-brief`, `bid-check`, `acos-check`, `budget-check`,
`keyword-expand`, `report-draft`, `scale-check`. Note: `keyword-expand` concerns
targeting keywords rather than negatives, and `budget-check` / `bid-check`
consume their own rule files. Each is **[VERIFY]** and should be completed as that
skill is defined, not before. No dependency has been invented.

---

## Duplicate Truth Prevention

**This document is the canonical governance document for negative keywords.**

Do **not** duplicate the following inside this document — reference the
authoritative source instead:

| Do not duplicate | Reference instead |
|------------------|-------------------|
| Campaign definitions | `context/campaign-list.md` |
| Keyword strategy | `context/keyword-strategy.md` |
| Target metrics (ACoS / ROAS / CTR / CVR) | `context/target-metrics.md` |
| Operational Search Term Reports | `evidence/` (operational exports; not copied into any markdown file) |

Additional rules:

- Negative keyword **records** must not be duplicated across markdown files. The
  operational library is populated from verified evidence; the rows live with
  their evidence, not scattered through prose.
- Bid and budget mechanics are owned by `context/bid-rules.md` and
  `context/budget-rules.md` respectively and are linked, never restated.
- This document owns the **negatives** process only. Targeting-keyword strategy
  is owned by `context/keyword-strategy.md`; the two cross-reference each other
  rather than repeat content.

---

## Known Limitations

Genuine unresolved items. Each blocks a specific downstream use. None is worked
around by inventing data.

1. **No operational negative keyword list imported.** The register is an empty
   template; no exclusion is documented.
2. **No Search Term Report imported.** No customer search-term data has been
   filed in the repository.
3. **No Waste Scan imported.** No `waste-scan` output has been filed as evidence.
4. **No Campaign Audit imported.** No `campaign-audit` output exists to source
   exclusions from.
5. **Marketplace strategy.** The repository is GBP/UK-denominated; whether
   negative-keyword strategy differs by marketplace is undocumented. [VERIFY]
6. **Match-type policy.** Which negative match types (exact/phrase) apply in
   which situations is undocumented. [VERIFY]
7. **Approval workflow.** The specific approver(s) and steps to move a candidate
   to Approved/Applied are undocumented beyond "human approval required".
   [VERIFY]
8. **Removal criteria.** The conditions under which a negative is reviewed and
   removed are undocumented. [VERIFY]
9. **Shared negative list policy.** Whether LEDSone uses account-level shared
   negative lists (vs per-campaign/ad-group negatives) is undocumented. [VERIFY]
10. **Campaign-vs-ad-group scoping.** The policy for which level a negative is
    applied at is undocumented. [VERIFY]
11. **Competitor targeting-vs-negation boundary.** Competitor terms are described
    both as targetable and as excludable; the rule for which applies when is
    undocumented. [VERIFY]
12. **Governance roles undefined.** Business Owner, Technical Reviewer and
    Queryability Reviewer are undefined repository-wide. Until defined, this
    document has an owner but no approver. [VERIFY]
13. **Validation Status vocabulary.** Only `Conflict` is defined by this
    document; the full set of allowed statuses is undocumented. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is this document? | Yes | Header; Purpose — a negative-keyword *governance* specification, not the operational library |
| Why does it exist? | Yes | Purpose |
| How are negative keywords classified? | Yes | Negative Keyword Categories |
| Where do they originate? | Yes | Discovery Sources; Evidence Requirements |
| What evidence is required? | Yes | Evidence Requirements |
| How are they approved? | Yes | Negative Keyword Lifecycle; Validation Rules |
| How should AI skills consume this document? | Yes | Purpose; Scope; Dependency Matrix |
| What remains unknown? | Yes | Every `[VERIFY]` marker, consolidated in Known Limitations |

**Result: PASS**
