# Campaign List

Canonical **campaign register specification** for LEDSone Amazon PPC.

This document defines *how* campaigns must be documented, *what* must be
recorded, *where* that information originates, and *how* it is validated and
consumed by AI skills. It is **not** a live campaign inventory. No campaign
records are stored here yet, and none may be added until verified operational
evidence is imported.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — recorded as `Owner` in `README.md`, `CLAUDE.md`, `context/bid-rules.md` and `context/budget-rules.md` |
| Business Owner | [VERIFY] — no governance section exists in `README.md` or `CLAUDE.md`. "MD" appears in `context/budget-rules.md` as a budget **approver**, but is nowhere defined as Business Owner. Do not assume the two are the same role. |
| Technical Reviewer | [VERIFY] — no technical reviewer role is defined anywhere in this repository |
| Queryability Reviewer | [VERIFY] — no queryability reviewer role is defined anywhere in this repository |
| Status | Active — specification approved; the campaign register itself is empty pending evidence, with outstanding items marked `[VERIFY]` |
| Version | 1.0 |
| Last Updated | 2026-07-23 |
| Source Documents | See the **Evidence** section below |

---

## Purpose

This document exists so that every person and every AI skill in this repository
documents campaigns the **same** way, from one canonical definition.

It defines the **canonical campaign register** for LEDSone Amazon PPC: the
single, agreed structure that every campaign record must follow, the fields that
must be captured, the evidence a record must trace back to, and the validation a
record must pass before it can be relied upon.

It answers questions that were previously unanswerable from this repository:

1. How must a campaign be documented?
2. What information must be stored about each campaign?
3. Where must that information originate?
4. How is a campaign record validated?
5. How do AI skills consume campaign information?

**Records are maintained separately from this specification.** This file defines
the register; it does not hold the register's rows. Campaign records are
populated **only** from approved evidence (see **Evidence Requirements**) and are
kept in the campaign documentation area described in `README.md`
(`campaigns/`, organised by lifecycle: active, paused, archived). Until such
evidence is imported, the register defined here is intentionally empty.

**This is a specification, not an inventory.** No campaign name, ID, portfolio,
budget, objective, marketplace or owner is asserted anywhere in this document.

---

## Evidence

Every statement in this document originates from one of the sources below.
Physical existence inside this repository was checked on 2026-07-23 by listing
the repository contents.

| Source | Location | Exists in this repository? | Used for |
|--------|----------|---------------------------|----------|
| `README.md` | repository root | **Yes — verified in-repo document** | Repository purpose; the `campaigns/` lifecycle folders (active/paused/archived); evidence-first and human-approval policy; the `skills/` list |
| `CLAUDE.md` | repository root | **Yes — verified in-repo document** | Governance principles: Existing Asset First, Evidence First, Queryability First, No Duplicate Truth, Human Approval Required, Never Modify Amazon Ads |
| `context/target-metrics.md` | `context/target-metrics.md` | **Yes — verified in-repo document** | Approved campaign types (SP, SB, SD); document format precedent; skill dependency precedent |
| `context/bid-rules.md` | `context/bid-rules.md` | **Yes — verified in-repo document** | Confirms `/bid-check` as a campaign-consuming skill; notes the `[VERIFY]` evidence naming standard (handbook "Section B11") |
| `context/budget-rules.md` | `context/budget-rules.md` | **Yes — verified in-repo document** | **Authoritative campaign naming convention** (`Campaign Type → Product Name → Target`); confirms `/budget-check`; the stock gate governing whether a product may be added to a campaign |
| `context/amazon-vendor-bridge.md` | `context/amazon-vendor-bridge.md` | **Yes — file present, but unpopulated.** The file physically exists and contains only `Status: [VERIFY] — not yet documented`; it defines no product-to-campaign mapping yet. | Named as the intended link target for product-level references (ASIN/SKU). Its contents are **not** invented here. |

**No external source is cited by this document.** Every source above is a
verified in-repository markdown file. Where a source is itself an unpopulated
stub (`context/amazon-vendor-bridge.md`), that is stated rather than worked
around.

---

## Scope

This specification is the shared campaign-documentation reference for the
following processes. It defines their input structure; it does not perform any
of them.

| Process | How this document supports it |
|---------|-------------------------------|
| Campaign Audits | Defines the fields every campaign record must carry, so `campaign-audit` can check completeness and validity against one standard |
| Budget Optimisation | Provides the campaign identity and type that budget logic in `context/budget-rules.md` is applied to |
| Bid Optimisation | Provides the campaign identity, type and targeting type that bid logic in `context/bid-rules.md` is applied to |
| Reporting | Defines a stable campaign identity so weekly and monthly reports in `reports/` stay consistent month to month |
| Scaling | Provides the campaign record that the stock gate and scaling checks operate on |
| AI Skills | Every campaign-aware skill in `skills/` reads campaign records described by this standard — see the **Dependency Matrix** |
| Future Automation | Any later automation would consume records structured by this specification. **Note:** this repository never changes Amazon Ads (`CLAUDE.md`, `README.md`); automation here means downstream document processing, not Ads mutation |

**Out of scope.** This document does not contain bid mechanics, budget override
tables, target metrics or product master data. Those live in their authoritative
files and are linked, never restated. It also holds no live campaign rows.

**Safety.** Any output derived from this document that touches bids, budgets,
keywords, campaigns or targeting: **outputs DRAFT recommendations only, never
applies Amazon Ads changes, human approval required** before implementation.
Jathukulan reviews and applies every change manually. If automation of Amazon
Ads is implied, **STOP** and flag it.

---

## Campaign Types

LEDSone actively runs three Amazon advertising types. These three are approved
facts (confirmed by `context/target-metrics.md`, which defines KPI targets for
each). Only functionality supported by repository evidence is described below;
anything not evidenced is marked `[VERIFY]`.

| Type | Code | Evidenced in repository | Notes |
|------|------|-------------------------|-------|
| Sponsored Products | **SP** | KPI targets in `context/target-metrics.md`; £2/day minimum and Special Rule overrides in `context/budget-rules.md`; naming example `SP \| Lamp Shade \| Auto` | Described in `target-metrics.md` as "the primary conversion-driving ad type". Full feature set beyond what those files state: [VERIFY] |
| Sponsored Brands | **SB** | KPI targets in `context/target-metrics.md`; £2/day minimum in `context/budget-rules.md` | Brand-level advertising. Full feature set: [VERIFY] |
| Sponsored Display | **SD** | KPI targets in `context/target-metrics.md` | **No** approved minimum daily budget is documented for SD (`context/target-metrics.md`, section 4). Full feature set: [VERIFY] |

Ad-type internal mechanics (available targeting surfaces, creative formats,
bidding options per type) beyond the statements above are **not** documented in
this repository: [VERIFY].

---

## Campaign Naming Standard

A campaign naming convention **already exists** in this repository. It is
**authoritatively defined in `context/budget-rules.md`** (section "Naming") and
is reproduced here for reference only. If the two ever disagree,
`context/budget-rules.md` wins.

**Structure:** `Campaign Type → Product Name → Target`

**Documented example:** `SP | Lamp Shade | Auto`

**Personal/team tag:** `JD` (as recorded in `context/budget-rules.md`).
[VERIFY] — the exact placement of the `JD` tag within the name string, and
whether it is mandatory, are not specified in the source.

**Not invented here.** No delimiter rules, marketplace segment, portfolio
segment, casing rules or additional fields beyond the three elements above are
asserted. Anything not stated in `context/budget-rules.md` is [VERIFY].

**Related open item.** `context/bid-rules.md` records a separate, undefined
"Section B11 evidence naming standard" (for evidence files, not campaigns) as
[VERIFY]. It is noted here only to avoid confusion; it is not a campaign naming
rule.

---

## Campaign Lifecycle

The repository evidences a lifecycle through the `campaigns/` folder structure,
which `README.md` describes as organised "by lifecycle: active, paused,
archived". Those three states are therefore supported by evidence. A preceding
"Draft" state is **not** evidenced.

```
Draft        [VERIFY] — no repository evidence for a Draft state
   ↓
Active       Evidenced — campaigns/ active (README.md)
   ↓
Paused       Evidenced — campaigns/ paused (README.md)
   ↓
Archived     Evidenced — campaigns/ archived (README.md)
```

- **Active / Paused / Archived** — supported by the `campaigns/` lifecycle
  folders in `README.md`.
- **Draft** — shown for completeness only; [VERIFY], no repository evidence
  defines it.
- The precise transition rules between states (what moves a campaign from Active
  to Paused, or Paused to Archived, and who authorises it) are **not** documented
  in this repository: [VERIFY]. Note that a pause **decision** may originate from
  metric thresholds in `context/target-metrics.md`, but the pause itself is
  applied manually in Amazon Ads by Jathukulan after approval — never
  automatically.

---

## Campaign Relationships

The logical hierarchy an Amazon PPC campaign record sits within. This describes
the conceptual relationship only; no implementation detail (IDs, cardinality
limits, matching behaviour) is invented.

```
Campaign
   ↓
Ad Group
   ↓
Keyword  /  Product Target
   ↓
Advertised Product
```

- **Campaign → Ad Group** — a campaign contains one or more ad groups.
- **Ad Group → Keyword / Product Target** — an ad group contains targets, which
  are either keywords or product targets depending on the targeting type. The
  exact rules governing which target kinds are permitted per campaign type:
  [VERIFY].
- **Keyword / Product Target → Advertised Product** — targets drive traffic to
  the advertised products in the ad group.
- **Advertised Product → product master data** — the advertised product's
  identifiers (ASIN, SKU, Parent/Child ASIN) are **product-level data**. They
  are **not** stored here; they belong in `context/amazon-vendor-bridge.md` (see
  **Duplicate Truth Prevention**).

Cardinality, limits, and any campaign-type-specific variations of this hierarchy
are not documented in this repository: [VERIFY].

---

## Campaign Register Template

The canonical register structure. It is **empty by design**. No row below the
header is populated, and none may be added except from verified evidence.

| Campaign Name | Campaign ID | Campaign Type | Marketplace | Portfolio | Status | Objective | Daily Budget | Bid Strategy | Targeting Type | Launch Date | Owner | Primary Evidence | Last Verified | Validation Status |
|---------------|-------------|---------------|-------------|-----------|--------|-----------|--------------|--------------|----------------|-------------|-------|------------------|---------------|-------------------|
| *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* |

> **Campaign records shall only be populated from verified Amazon Ads exports or
> approved operational evidence.** No campaign name, ID, portfolio, status,
> budget, objective, marketplace or owner has been entered, because none has yet
> been imported from verified evidence. The single placeholder row above shows
> the columns only and is not a record.

---

## Mandatory Fields

Definition and requirement level for every register column. "Mandatory" means a
record cannot be considered valid without it. Where the requirement level is not
established by repository evidence, it is marked `[VERIFY]` rather than assumed.

| Field | Meaning | Mandatory? |
|-------|---------|------------|
| Campaign Name | The campaign's name, following the **Campaign Naming Standard** above | **Mandatory** — every record must be named |
| Campaign ID | The unique Amazon-assigned campaign identifier | **Mandatory** — required for uniqueness (see **Validation Rules**) |
| Campaign Type | One of SP, SB, SD (see **Campaign Types**) | **Mandatory** — must be a valid type |
| Marketplace | The Amazon marketplace the campaign runs in | [VERIFY] — repository is GBP/UK-denominated but no marketplace field is formally required anywhere; requirement level undocumented |
| Portfolio | The Amazon Ads portfolio the campaign belongs to, if any | [VERIFY] — no portfolio model is documented in this repository; may be optional |
| Status | Lifecycle state (see **Campaign Lifecycle**) | **Mandatory** — a record must state its lifecycle state |
| Objective | The campaign's advertising objective | [VERIFY] — no objective taxonomy is documented in this repository |
| Daily Budget | The campaign's daily budget | [VERIFY] on requirement level. Budget **minimums** live in `context/budget-rules.md`; this field records the value, it does not restate the rule |
| Bid Strategy | The campaign's bid strategy | [VERIFY] — bid **mechanics** live in `context/bid-rules.md`; the strategy taxonomy for this field is undocumented |
| Targeting Type | e.g. automatic vs manual targeting (the naming example uses `Auto`) | [VERIFY] on requirement level; the value vocabulary beyond the `Auto` example is undocumented |
| Launch Date | The date the campaign launched | [VERIFY] — requirement level undocumented |
| Owner | The person accountable for the campaign | [VERIFY] — repository Owner is Jathukulan, but per-campaign ownership is undocumented |
| Primary Evidence | The single authoritative source the record traces to (see **Evidence Requirements**) | **Mandatory** — evidence-first policy (`README.md`, `CLAUDE.md`) requires it |
| Last Verified | The date the record was last checked against its evidence | **Mandatory** — required by **Validation Rules** |
| Validation Status | The record's validation outcome (see **Validation Rules**) | **Mandatory** — required by **Validation Rules** |

Any field marked `[VERIFY]` above must have its requirement level confirmed from
approved documentation before the register is populated.

---

## Evidence Requirements

A campaign record may be created **only** from approved evidence. Approved
evidence includes:

- **Amazon Ads Bulk Export**
- **Campaign Manager Export**
- **Amazon Ads API**
- **Approved Operational Documentation**

**Manual entry alone is not sufficient evidence.** A value typed in by a person
without one of the sources above behind it does not meet the evidence-first
policy (`README.md`, `CLAUDE.md`) and must not be treated as a verified record.

Every imported evidence source must, consistent with `README.md`, be filed with
its **source, date and date range** so the record can be independently checked
later.

---

## Validation Rules

Every campaign record must satisfy all of the following before it is treated as
valid:

- a **unique Campaign ID** — no two records may share an ID;
- a **valid Campaign Type** — one of SP, SB, SD;
- **approved evidence** — a Primary Evidence source from **Evidence
  Requirements**;
- a **Last Verified date** — when the record was last checked against that
  evidence;
- a **Validation Status** — the outcome of validation.

**One authoritative source per record.** Every campaign record must trace to
**one** authoritative source. If two or more sources disagree about a record's
values:

- set **Validation Status = Conflict**;
- do **not** choose one source over another without evidence establishing which
  is authoritative;
- record both sources and escalate for human resolution.

The full set of allowed Validation Status values (beyond `Conflict`), and any
further validation rules, are not established by repository evidence: [VERIFY].

---

## Dependency Matrix

Which register fields are consumed by which skills. **Only skills that exist in
`skills/` are listed** (all ten below are present as files). Every skill file is
currently an early-stage stub, and none yet declares the campaign fields it
reads. Dependencies are therefore recorded as confirmed **only** where a source
document names the skill as a consumer of campaign logic; everything else is
`[VERIFY]` and must be filled in as each skill is defined — not guessed.

| Field | Used By |
|-------|---------|
| Campaign Name | [VERIFY] — no skill declares this yet |
| Campaign ID | [VERIFY] |
| Campaign Type | `bid-check` (bid logic is type-aware, `context/bid-rules.md`); `budget-check` (budget minimums/overrides are type-specific, `context/budget-rules.md`); `acos-check` (KPI targets are per-type, `context/target-metrics.md`). All other consumers [VERIFY] |
| Marketplace | [VERIFY] |
| Portfolio | [VERIFY] |
| Status | [VERIFY] — likely consumed by `campaign-audit` and `scale-check`, but neither skill declares it yet |
| Objective | [VERIFY] |
| Daily Budget | `budget-check` — `context/budget-rules.md` explicitly names `/budget-check` as the consumer of its budget logic. Other consumers [VERIFY] |
| Bid Strategy | [VERIFY] — `bid-check` consumes bid logic (`context/bid-rules.md`), but its dependence on this specific field is not declared |
| Targeting Type | [VERIFY] |
| Launch Date | [VERIFY] |
| Owner | [VERIFY] |
| Primary Evidence | [VERIFY] — relevant to `campaign-audit` for completeness checking, but not yet declared |
| Last Verified | [VERIFY] |
| Validation Status | [VERIFY] |

Skills present in `skills/` with **no confirmed** campaign-field dependency yet:
`ppc-brief`, `search-term-check`, `waste-scan`, `keyword-expand`,
`campaign-audit`, `report-draft`, `scale-check`. Each is [VERIFY] and should be
completed as that skill is defined, not before. No dependency has been invented.

---

## Duplicate Truth Prevention

**This document defines the canonical campaign register.**

- Campaign information must **not** be duplicated across multiple markdown
  documents. This file is the single definition of how campaigns are documented;
  other documents link here rather than restate it.
- **Operational exports remain the authoritative source for campaign records.**
  The rows themselves live with their verified evidence, not scattered through
  prose files.
- **Product-level information — ASIN, SKU, Parent ASIN, Child ASIN — must never
  be duplicated here.** This register is about campaigns, not products.
- Where a campaign record needs to reference a product, it must **link to**
  `context/amazon-vendor-bridge.md` rather than copy any product identifier into
  the register.

**Bridge status.** `context/amazon-vendor-bridge.md` is **present in the
repository but not yet populated** — it currently contains only
`Status: [VERIFY] — not yet documented`. Until it is populated, product
references cannot yet be resolved through it: **Bridge file present but
unpopulated — [VERIFY].** Its contents are not invented here.

**Values that live elsewhere and are only linked, never restated here:**

| Fact | Authoritative source |
|------|----------------------|
| Campaign naming convention | `context/budget-rules.md` |
| Target ACoS / ROAS / CTR / CVR | `context/target-metrics.md` |
| Bid mechanics, floors, ceilings, triggers | `context/bid-rules.md` |
| Budget minimums, overrides, stock gate | `context/budget-rules.md` |
| Product identifiers (ASIN/SKU/Parent/Child) | `context/amazon-vendor-bridge.md` (once populated) |

---

## Known Limitations

Genuine unresolved items. Each blocks a specific downstream use. None is
worked around by inventing data.

1. **Campaign register not yet populated.** The register is an empty template.
   No campaign is documented.
2. **No Amazon Ads export imported.** No Bulk Export, Campaign Manager Export or
   API pull has been filed in the repository.
3. **No Campaign IDs verified.** No unique identifier exists to validate against.
4. **No Portfolio mapping verified.** No portfolio model is documented; the
   Portfolio field's meaning and requirement level are undefined. [VERIFY]
5. **Campaign Naming Convention — partial.** The structure and one example are
   documented in `context/budget-rules.md`, but the placement/mandatory status
   of the `JD` tag, delimiters, and any marketplace/portfolio segment are
   [VERIFY].
6. **Marketplace-specific campaign rules.** The repository is GBP/UK-denominated;
   whether campaign rules differ by marketplace is undocumented. [VERIFY]
7. **Campaign ownership.** Per-campaign Owner is undefined; only the repository
   Owner (Jathukulan) is known. [VERIFY]
8. **Campaign objectives.** No objective taxonomy is documented. [VERIFY]
9. **Campaign relationship verification.** The Campaign → Ad Group → Target →
   Product hierarchy is stated conceptually; cardinality, limits and
   type-specific variations are unverified. [VERIFY]
10. **Governance roles undefined.** Business Owner, Technical Reviewer and
    Queryability Reviewer are undefined repository-wide, consistent with
    `context/target-metrics.md`. Until defined, this document has an owner but no
    approver. [VERIFY]
11. **Vendor bridge unpopulated.** `context/amazon-vendor-bridge.md` exists but
    holds no mapping, so product references cannot yet be resolved. [VERIFY]
12. **Validation Status vocabulary.** Only `Conflict` is defined by this
    document; the full set of allowed statuses is undocumented. [VERIFY]

---

## Queryability Test

Verification that another LLM can answer the required questions using only this
document.

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is this document? | Yes | Header; Purpose — a campaign register *specification*, not an inventory |
| Why does it exist? | Yes | Purpose |
| Which campaign types are supported? | Yes | Campaign Types — SP, SB, SD |
| How should campaigns be documented? | Yes | Campaign Naming Standard; Campaign Register Template; Mandatory Fields |
| Which fields are mandatory? | Yes | Mandatory Fields |
| Where must campaign data originate? | Yes | Evidence Requirements |
| How should campaign data be validated? | Yes | Validation Rules |
| How are campaign records related to products? | Yes | Campaign Relationships; Duplicate Truth Prevention |
| Which bridge document should be referenced? | Yes | Duplicate Truth Prevention — `context/amazon-vendor-bridge.md` (present but unpopulated) |
| What information remains unknown? | Yes | Every `[VERIFY]` marker, consolidated in Known Limitations |

**Result: PASS**
