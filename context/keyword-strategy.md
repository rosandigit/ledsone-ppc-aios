# Keyword Strategy

Canonical **keyword strategy specification** for LEDSone Amazon PPC.

This document defines *how* keywords are classified, discovered, validated and
moved through their lifecycle, *where* keyword data originates, and *how* AI
skills consume it. It is **not** a keyword database and it is **not** the
operational keyword library. No keyword records are stored here, and none may be
added until verified operational evidence is imported.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — recorded as `Owner` in `README.md`, `CLAUDE.md`, `context/bid-rules.md` and `context/budget-rules.md` |
| Business Owner | [VERIFY] — no governance section exists in `README.md` or `CLAUDE.md`. "MD" appears in `context/budget-rules.md` as a budget **approver**, but is nowhere defined as Business Owner. Do not assume the two are the same role. |
| Technical Reviewer | [VERIFY] — no technical reviewer role is defined anywhere in this repository |
| Queryability Reviewer | [VERIFY] — no queryability reviewer role is defined anywhere in this repository |
| Status | Active — specification approved; the keyword register itself is empty pending evidence, with outstanding items marked `[VERIFY]` |
| Version | 1.0 |
| Last Updated | 2026-07-23 |
| Source Documents | See the **Evidence** section below |

---

## Purpose

This document exists so that every person and every AI skill in this repository
treats keywords the **same** way, from one canonical definition.

It defines the **canonical keyword strategy** for LEDSone Amazon PPC: how a
keyword is classified, where it may legitimately come from, how it is validated
against evidence, and how it progresses from a discovery candidate to an active,
optimised or archived keyword.

**How it supports Amazon PPC optimisation.** Bid, budget, waste and expansion
decisions all act on keywords. Without one agreed definition of what a keyword
*is* and how it is *validated*, those decisions drift. This document gives them a
single, evidence-anchored input structure.

**How future AI skills consume it.** Skills in `skills/` read this specification
to learn the keyword categories, the approved discovery sources, the lifecycle
states and the validation rules a keyword record must satisfy — see the
**Dependency Matrix**. They do **not** read keyword rows from this file, because
this file holds none.

**This is a strategy specification, not an operational keyword database.** No
keyword, search volume, CPC, ranking or performance figure is asserted anywhere
in this document.

---

## Evidence

Every statement in this document originates from one of the sources below.
Physical existence inside this repository was checked on 2026-07-23 by listing
the repository contents.

| Source | Location | Exists in this repository? | Used for |
|--------|----------|---------------------------|----------|
| `README.md` | repository root | **Yes — verified in-repo document** | Repository purpose; evidence-first and human-approval policy; the `keywords/` area (master negatives, proven exact-match library, expansion candidates); the `skills/` list |
| `CLAUDE.md` | repository root | **Yes — verified in-repo document** | Governance: Existing Asset First, Evidence First, Queryability First, No Duplicate Truth, Human Approval Required, Never Modify Amazon Ads |
| `context/target-metrics.md` | `context/target-metrics.md` | **Yes — verified in-repo document** | Approved ad types (SP, SB, SD); CTR/CVR/ACoS KPI targets that keyword decisions are judged against (linked, never restated) |
| `context/campaign-list.md` | `context/campaign-list.md` | **Yes — verified in-repo document** | Canonical campaign register and the Campaign → Ad Group → Keyword → Target hierarchy (linked, never restated) |
| `context/bid-rules.md` | `context/bid-rules.md` | **Yes — verified in-repo document** | Sample-size gate (15/25 clicks) before acting on a keyword; **partial competitor-term and brand-term keyword policy**; per-SKU CPC derivation |
| `context/budget-rules.md` | `context/budget-rules.md` | **Yes — verified in-repo document** | Campaign naming convention that uses a targeting element (`Auto`); `/budget-check` as a consuming skill |
| `context/negative-keyword-master.md` | `context/negative-keyword-master.md` | **Yes — file present, but unpopulated.** Contains only `Status: [VERIFY] — not yet documented`; defines no negative keywords yet. | Named as the authoritative home for negative keywords. Its contents are **not** invented here. |

**No external source is cited by this document.** Every source above is a
verified in-repository markdown file. Where a source is itself an unpopulated
stub (`context/negative-keyword-master.md`), that is stated rather than worked
around.

---

## Scope

This specification is the shared keyword reference for the following processes.
It defines their input structure; it does not perform any of them.

| Process | How this document supports it |
|---------|-------------------------------|
| Keyword Expansion | Defines categories, discovery sources and lifecycle so `keyword-expand` proposes candidates against one standard |
| Search Term Review | Defines the Keyword → Search Term relationship and lifecycle so `search-term-check` can classify terms and route them to promotion or negation |
| Bid Optimisation | Provides keyword identity, match type and category that bid logic in `context/bid-rules.md` is applied to |
| Campaign Audits | Provides the keyword-record fields that `campaign-audit` checks for completeness and validity |
| Waste Reduction | Defines the lifecycle and evidence needed before `waste-scan` can recommend pausing or negating a keyword |
| Reporting | Provides a stable keyword classification so reports in `reports/` stay consistent month to month |
| AI Skills | Every keyword-aware skill in `skills/` reads this specification — see the **Dependency Matrix** |

**Out of scope.** This document does not contain bid mechanics, budget rules, KPI
targets, campaign records, negative-keyword lists or any keyword rows. Those live
in their authoritative files and are linked, never restated.

**Safety.** Any output derived from this document that touches bids, budgets,
keywords, campaigns or targeting: **outputs DRAFT recommendations only, never
applies Amazon Ads changes, human approval required** before implementation.
Jathukulan reviews and applies every change manually. If automation of Amazon
Ads is implied, **STOP** and flag it.

---

## Keyword Categories

Two independent axes classify a keyword: its **match type** (how Amazon matches
it to a customer search) and its **category** (what the keyword represents).
Both are recorded per record. Only classifications supported by repository
evidence are asserted; anything else is `[VERIFY]`.

### Match types

| Match type | Purpose |
|------------|---------|
| Broad Match | Widest reach. Matches the keyword in any order plus related variations, synonyms and close terms. Primarily a **discovery** match type — surfaces new search terms to harvest. |
| Phrase Match | Medium reach. Matches the keyword phrase in order, allowing words before/after. Balances discovery against relevance. |
| Exact Match | Narrowest reach. Matches the keyword (and close variants) only. Used for **proven** terms — `README.md` describes a "proven exact-match library" in `keywords/`. Highest control and typically strongest efficiency. |
| Negative Keywords | Not a targeting match type but an **exclusion**. Prevents ads showing for a keyword/term. **Authoritative home: `context/negative-keyword-master.md`** (currently unpopulated). Negatives are referenced here, not listed here. |

### Keyword categories

| Category | Purpose |
|----------|---------|
| Brand Keywords | Terms containing the LEDSone brand. Bid/threshold policy: **[VERIFY]** — `context/bid-rules.md` records the brand-term bid/threshold as `[VERIFY]`. |
| Generic Keywords | Non-brand descriptive/category terms (e.g. product-type words). The primary discovery and volume source. Detailed policy: [VERIFY]. |
| Competitor Keywords | Terms referencing competitor brands/products. **Partial policy exists in `context/bid-rules.md`:** start lower than the standard bid and increase only after proven performance; the exact starting bid (or % below standard) and the definition of "proven" are `[VERIFY]` in that source. |
| Long-tail Keywords | Longer, more specific multi-word terms — lower volume, higher intent. Typically harvested from Broad/Phrase discovery and promoted to Exact when proven. Detailed policy: [VERIFY]. |

Any category or match-type behaviour not stated above (e.g. per-ad-type match
support, close-variant handling specifics) is not documented in this repository:
**[VERIFY]**.

---

## Keyword Discovery Sources

A keyword may enter the pipeline **only** from an approved discovery source. Each
discovered candidate must still pass validation (see **Keyword Validation
Rules**) before it becomes an active keyword.

Approved discovery sources:

- **Amazon Search Term Report** — actual customer search terms that triggered
  ads; the primary harvesting source.
- **Amazon Keyword Report** — targeted-keyword performance.
- **Helium 10** — third-party keyword research and volume tooling.
- **Amazon Brand Analytics** — search-frequency and share data.
- **Approved internal analysis** — analysis documented and approved under the
  repository's evidence-first policy.

**Manual suggestions require validation.** A keyword proposed by a person, with
no approved discovery source behind it, is a candidate only. It must be validated
against approved evidence before it can progress past the Candidate/Review stage.
Manual entry alone is **not** sufficient evidence (see **Evidence
Requirements**).

---

## Keyword Lifecycle

The states a keyword moves through, from discovery to retirement. States marked
as evidenced are supported by repository documents; the remainder are shown for
completeness and marked `[VERIFY]` because no repository document defines them
yet.

```
Candidate     Discovered from an approved source; not yet validated
   ↓
Review        Under validation against evidence
   ↓
Approved      Validated; cleared to add to a campaign (human approval)
   ↓
Active        Live in a campaign/ad group
   ↓
Optimised     Bid/placement tuned per context/bid-rules.md after enough data
   ↓
Paused        Temporarily stopped
   ↓
Archived      Retired from active use
```

- **Sample-size gate.** Movement into **Optimised** (or any bid change) is gated
  by the click thresholds in `context/bid-rules.md` — **15 clicks** minimum,
  **25 clicks** for larger moves or Hero SKU campaigns. Acting on less is acting
  on noise.
- **Proven → Exact.** `README.md` describes a "proven exact-match library",
  implying candidates are promoted to Exact once proven. The exact promotion
  criteria are **[VERIFY]**.
- **Transition rules.** The precise conditions and approver for each transition
  (who moves a keyword from Review to Approved, Active to Paused, etc.) are
  **[VERIFY]** — not defined in this repository. Every transition remains a
  human-approved, manually applied action; nothing here changes Amazon Ads.
- Any lifecycle state a downstream process needs but that is not listed above is
  **[VERIFY]**; do not invent one.

---

## Keyword Register Template

The canonical register structure. It is **empty by design**. No row below the
header is populated, and none may be added except from verified evidence.

| Keyword | Match Type | Category | Campaign | Ad Group | Discovery Source | Search Intent | Status | Evidence | Last Verified | Validation Status |
|---------|------------|----------|----------|----------|------------------|---------------|--------|----------|---------------|-------------------|
| *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* | *(empty)* |

> **Keyword records shall only be populated from verified operational evidence.**
> No keyword, match type, category, search volume, CPC, ranking or performance
> value has been entered, because none has yet been imported from verified
> evidence. The single placeholder row above shows the columns only and is not a
> record.
>
> The `Campaign` and `Ad Group` values reference records defined in
> `context/campaign-list.md`; they are linked, not redefined here.

---

## Keyword Validation Rules

Every keyword record should satisfy all of the following before it is treated as
valid:

- **approved evidence** — a source from **Evidence Requirements**;
- a **discovery source** — where the keyword came from (see **Keyword Discovery
  Sources**);
- a **validation date** — recorded in `Last Verified`;
- a **validation status** — recorded in `Validation Status`.

**Conflict handling.** If two or more evidence sources disagree on a keyword's
**classification, match type, or status**, do **not** choose one source over
another without justification. Set **Validation Status = Conflict**, record
**both** sources, and escalate for human resolution.

The full set of allowed Validation Status values (beyond `Conflict`), the
required search-intent taxonomy, and any further validation rules are not
established by repository evidence: **[VERIFY]**.

---

## Evidence Requirements

A keyword record may be created **only** from approved evidence. Approved
evidence includes:

- **Amazon Search Term Reports**
- **Amazon Keyword Reports**
- **Amazon Ads API**
- **Helium 10 exports**
- **Amazon Brand Analytics**
- **Approved operational documentation**

**Manual entry alone is not sufficient evidence.** A keyword typed in without one
of the sources above behind it does not meet the evidence-first policy
(`README.md`, `CLAUDE.md`) and must not be treated as a validated record.

Every imported evidence source must, consistent with `README.md`, be filed with
its **source, date and date range** so the record can be independently checked
later.

---

## Relationship Matrix

The logical chain a keyword sits within. This describes the conceptual
relationship only; no implementation detail (limits, matching internals) is
invented.

```
Campaign
   ↓
Ad Group
   ↓
Keyword
   ↓
Search Term
   ↓
Customer Search
```

- **Campaign → Ad Group** — a campaign contains ad groups. Campaign and ad-group
  identity are defined in `context/campaign-list.md`, not here.
- **Ad Group → Keyword** — an ad group contains the targeted keywords.
- **Keyword → Search Term** — a keyword (via its match type) matches one or more
  actual customer **search terms**. Broad/Phrase keywords surface many search
  terms; Exact keywords match narrowly.
- **Search Term → Customer Search** — a search term is what a real customer
  typed. Search terms are the raw material harvested (from the Search Term
  Report) into new keywords or negatives.

Cardinality, match-behaviour internals and any ad-type-specific variations of
this chain are not documented in this repository: **[VERIFY]**.

---

## Dependency Matrix

Which register fields are consumed by which skills. **Only skills that exist in
`skills/` are listed** (all ten below are present as files). Every skill file is
currently an early-stage stub, and none yet declares the keyword fields it reads.
Dependencies are recorded as confirmed **only** where a source document names the
skill as a consumer of keyword logic, or where the skill's own name states its
function; everything else is `[VERIFY]` and must be filled in as each skill is
defined — not guessed.

| Field | Used By |
|-------|---------|
| Keyword | `search-term-check`, `keyword-expand`, `waste-scan` (all operate on keywords/terms by name); precise dependence [VERIFY] per skill |
| Match Type | `keyword-expand`, `search-term-check` (promotion/negation is match-type aware); others [VERIFY] |
| Category | [VERIFY] — no skill declares this yet |
| Campaign | [VERIFY] — identity defined in `context/campaign-list.md`; consuming skills likely `campaign-audit`, but undeclared |
| Ad Group | [VERIFY] |
| Discovery Source | `keyword-expand` (proposes from approved sources); others [VERIFY] |
| Search Intent | [VERIFY] — no search-intent taxonomy is documented |
| Status | [VERIFY] — likely `waste-scan` and `campaign-audit`, but undeclared |
| Evidence | [VERIFY] — relevant to `campaign-audit` for completeness checks, but undeclared |
| Last Verified | [VERIFY] |
| Validation Status | [VERIFY] |

Skills present in `skills/` with **no confirmed** keyword-field dependency yet:
`ppc-brief`, `bid-check`, `acos-check`, `budget-check`, `campaign-audit`,
`report-draft`, `scale-check`. Note: `bid-check` consumes the sample-size gate
and CPC logic from `context/bid-rules.md`, but its dependence on a specific
keyword-register field is not declared. Each is **[VERIFY]** and should be
completed as that skill is defined, not before. No dependency has been invented.

---

## Duplicate Truth Prevention

**This document defines the canonical keyword strategy.**

- Keyword records must **not** be duplicated across markdown files. This file is
  the single definition of the keyword strategy; other documents link here rather
  than restate it.
- **Operational keyword exports remain the authoritative source for keyword
  records.** The rows themselves live with their verified evidence, not scattered
  through prose files.
- **Do not duplicate Search Term Reports inside this document.** Search Term
  Report data is operational evidence, filed in `evidence/`, not copied here.
- **Do not duplicate campaign information** already defined in
  `context/campaign-list.md`. Reference it for campaign/ad-group identity.
- **Do not duplicate KPI targets** already defined in
  `context/target-metrics.md`. Reference it for ACoS/ROAS/CTR/CVR values.
- **Negative keywords** are owned by `context/negative-keyword-master.md`
  (currently unpopulated). Do not list negatives here.

**Values that live elsewhere and are only linked, never restated here:**

| Fact | Authoritative source |
|------|----------------------|
| Campaign / ad-group identity | `context/campaign-list.md` |
| Target ACoS / ROAS / CTR / CVR | `context/target-metrics.md` |
| Bid mechanics, sample-size gate, competitor/brand bid policy, CPC derivation | `context/bid-rules.md` |
| Budget minimums, overrides, stock gate, campaign naming | `context/budget-rules.md` |
| Negative keywords | `context/negative-keyword-master.md` (once populated) |

---

## Known Limitations

Genuine unresolved items. Each blocks a specific downstream use. None is worked
around by inventing data.

1. **No keyword register populated.** The register is an empty template; no
   keyword is documented.
2. **No Search Term Report imported.** No customer search-term data has been
   filed in the repository.
3. **No Helium 10 export imported.** No third-party keyword/volume data exists.
4. **No Brand Analytics data imported.** No search-frequency/share data exists.
5. **Search intent classifications.** No search-intent taxonomy is defined.
   [VERIFY]
6. **Marketplace keyword strategy.** The repository is GBP/UK-denominated;
   whether keyword strategy differs by marketplace is undocumented. [VERIFY]
7. **Language strategy.** No language/localisation policy for keywords is
   documented. [VERIFY]
8. **Competitor keyword policy — partial.** `context/bid-rules.md` defines the
   direction (start lower, increase after proven performance) but leaves the
   starting bid and the definition of "proven" as [VERIFY].
9. **Brand keyword policy.** `context/bid-rules.md` records the brand-term
   bid/threshold as [VERIFY].
10. **Exact-match promotion criteria.** `README.md` implies a "proven"
    threshold for promoting keywords to the exact-match library, but the exact
    criteria are undocumented. [VERIFY]
11. **Negative-keyword master unpopulated.** `context/negative-keyword-master.md`
    exists but holds no negatives, so negative-keyword references cannot yet be
    resolved. [VERIFY]
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
| What is this document? | Yes | Header; Purpose — a keyword strategy *specification*, not a database |
| Why does it exist? | Yes | Purpose |
| How are keywords classified? | Yes | Keyword Categories — match types and categories |
| Where do keywords originate? | Yes | Keyword Discovery Sources; Evidence Requirements |
| How are keywords validated? | Yes | Keyword Validation Rules, including Conflict handling |
| What evidence is required? | Yes | Evidence Requirements |
| How should AI skills consume this strategy? | Yes | Purpose; Scope; Dependency Matrix |
| What remains unknown? | Yes | Every `[VERIFY]` marker, consolidated in Known Limitations |

**Result: PASS**
