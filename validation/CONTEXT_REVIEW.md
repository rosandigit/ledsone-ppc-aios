# Context Review

A read-only validation of the completed Context layer for LEDSone PPC AIOS. This
document reviews existing content; it does not rewrite, correct or extend any
reviewed file. Corrections, if any are approved, belong in the owning file per
`validation/README.md`.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Business Owner | [VERIFY] — undefined repository-wide |
| Technical Reviewer | [VERIFY] — undefined repository-wide |
| Queryability Reviewer | [VERIFY] — undefined repository-wide |
| Review Type | Read-only. No reviewed file was modified. |
| Status | Active |
| Version | 1.0 |
| Last Updated | 2026-07-23 |
| Source Documents | The nine files listed under **Reviewed Files**, plus `context/amazon-vendor-bridge.md`, `skills/` and `reports/README.md` as supporting evidence |

---

## Purpose

This review determines whether the Context layer is internally consistent,
evidence-based, queryable, free from duplicate truth, and ready to support the
Skills layer. It is a validation artefact under `validation/`, which exists to
hold "checks confirming that repository content is accurate, current and
complete" (`validation/README.md`). It contains no business rules and overrides
none.

---

## Reviewed Files

All inspected on 2026-07-23. None modified.

| File | Exists | Role |
|------|--------|------|
| `README.md` | Yes | Repository purpose and workflow |
| `CLAUDE.md` | Yes | Operating governance for any AI in the repo |
| `context/target-metrics.md` | Yes | Canonical PPC target metrics |
| `context/campaign-list.md` | Yes | Canonical campaign register specification |
| `context/keyword-strategy.md` | Yes | Canonical keyword strategy |
| `context/negative-keyword-master.md` | Yes | Canonical negative-keyword governance |
| `context/reporting-schedule.md` | Yes | Canonical reporting governance |
| `context/bid-rules.md` | Yes | Authoritative bid rules |
| `context/budget-rules.md` | Yes | Authoritative budget rules |

Supporting evidence inspected (not in the primary review set): `skills/` (10
skill files + README), `reports/README.md`, `validation/README.md`,
`context/amazon-vendor-bridge.md`.

---

## Repository Completeness

**Complete context documents (7 of the review set):**

- `context/target-metrics.md` — complete; approved KPI values, full Evidence and
  Dependency sections, self-declared Queryability PASS.
- `context/campaign-list.md` — complete; specification with an intentionally
  empty register.
- `context/keyword-strategy.md` — complete; specification with an intentionally
  empty register.
- `context/negative-keyword-master.md` — complete; governance with an
  intentionally empty register.
- `context/reporting-schedule.md` — complete; governance with an intentionally
  empty register; exact cadence intentionally `[VERIFY]`.
- `context/bid-rules.md` — authoritative source document, complete for its scope
  (carries its own internal `[VERIFY]` items).
- `context/budget-rules.md` — authoritative source document, complete for its
  scope (carries its own internal `[VERIFY]` items).

**Placeholders / deferred (outside the primary review set but part of `context/`):**

- `context/amazon-vendor-bridge.md` — **placeholder stub** (`Status: [VERIFY] —
  not yet documented`). Intentionally deferred; referenced as a future product
  bridge by `context/campaign-list.md` and `context/keyword-strategy.md`.

**Empty registers are by design, not incompleteness.** The campaign, keyword,
negative-keyword and reporting registers are intentionally empty because no
verified operational evidence has been imported. This is the correct state for a
specification/governance layer and is not counted as a completeness defect.

**Assessment:** The Context layer as scoped is **complete**. The only outstanding
context artefact is the deferred vendor bridge, which is correctly represented as
a future reference rather than presented as done.

---

## Duplicate Truth Review

Each business fact is expected to live in exactly one authoritative place, with
other documents linking rather than restating (`CLAUDE.md` — No Duplicate Truth).

| Fact | Authoritative home | Appears elsewhere? | Risk | Explanation |
|------|--------------------|--------------------|------|-------------|
| Campaign naming convention (`Type → Product → Target`) | `context/budget-rules.md` | Quoted in `campaign-list.md` and referenced in `keyword-strategy.md` | **Low Risk** | Reproduced with an explicit "authoritative in `budget-rules.md`; if they disagree, `budget-rules.md` wins" pointer. Controlled reference, not a competing definition. |
| Sample-size gate (15 / 25 clicks) | `context/bid-rules.md` | Restated in `target-metrics.md` (§3) and referenced in keyword/negative docs | **Low Risk** | `target-metrics.md` explicitly labels it "repeated for reference only… `bid-rules.md` wins". Intentional, with authority pointer. |
| Budget minimums (£2/day SP, SB) | `context/budget-rules.md` | Restated in `target-metrics.md` (§4) | **Low Risk** | Same pattern — labelled reference-only with `budget-rules.md` as winner. |
| KPI targets (ACoS/ROAS/CTR/CVR) | `context/target-metrics.md` | Linked (not restated) by campaign/keyword/negative/reporting docs | **No Risk** | Downstream docs link to `target-metrics.md`; values are not copied. |
| Campaign / ad-group identity | `context/campaign-list.md` | Linked by keyword/negative/reporting docs | **No Risk** | Referenced by name, not redefined. |
| Rollback discipline (log in `decisions/`) | `bid-rules.md` / `budget-rules.md` | Referenced in negative-keyword and reporting docs | **No Risk** | Referenced, not restated. |

**No Medium or High Risk duplication found.** All repetition is deliberate,
reference-only, and carries an explicit authority pointer identifying which file
wins on conflict. The numeral-25 overlap between the KPI target (`<25%` ACoS) and
`budget-rules.md` SR-3/SR-4 rule boundaries is explicitly documented in
`target-metrics.md` as *not* duplicate truth (different purpose), which is
correct.

---

## Reference Integrity

Cross-document references verified against files physically present in the
repository on 2026-07-23.

### Healthy References

| Reference | Status |
|-----------|--------|
| `campaign-list.md` → `target-metrics.md` | Healthy — target exists |
| `campaign-list.md` → `budget-rules.md` (naming) | Healthy — target exists |
| `keyword-strategy.md` → `campaign-list.md` | Healthy — target exists |
| `keyword-strategy.md` → `target-metrics.md` | Healthy — target exists |
| `keyword-strategy.md` → `bid-rules.md` (sample size, competitor/brand policy) | Healthy — target exists |
| `negative-keyword-master.md` → `keyword-strategy.md` | Healthy — target exists |
| `negative-keyword-master.md` → `campaign-list.md` | Healthy — target exists |
| `negative-keyword-master.md` → `target-metrics.md` | Healthy — target exists |
| `reporting-schedule.md` → `target-metrics.md` | Healthy — target exists |
| `reporting-schedule.md` → `campaign-list.md` / `keyword-strategy.md` / `negative-keyword-master.md` | Healthy — targets exist |
| `reporting-schedule.md` → `reports/README.md` (`weekly/`, `monthly/`, `sent/`) | Healthy — folders exist |
| All Dependency Matrix skill references (10 skills) | Healthy — every named skill file exists in `skills/` |

### Expected Future References

| Reference | Status |
|-----------|--------|
| `campaign-list.md` → `context/amazon-vendor-bridge.md` (product/ASIN bridge) | **Expected Future Reference.** The file physically exists but is an unpopulated stub. The *link* is healthy (target present); the *content* it points to (product mapping) is intentionally deferred. Both `campaign-list.md` and `keyword-strategy.md`/`negative-keyword-master.md` correctly describe it as "present but unpopulated — [VERIFY]". |
| `target-metrics.md` → `context/reporting-schedule.md` (review frequency) | **Resolved link, unresolved content.** `reporting-schedule.md` now exists (healthy link), but the approved cadence it was expected to supply is still `[VERIFY]`. Not broken; the dependency is real and openly tracked in both files. |

### Broken References

**None.** No reference points to a file that repository evidence shows should
already exist and does not. The vendor bridge is deliberately deferred and is
labelled as such, so it is an Expected Future Reference, not a Broken Reference.

---

## Evidence Quality

| Document | Evidence section | Sources listed | Unsupported claims avoided | `[VERIFY]` used for unknowns |
|----------|------------------|----------------|----------------------------|------------------------------|
| `target-metrics.md` | ✓ | ✓ (with in-repo existence check; 2 external sources flagged as not in repo) | ✓ | ✓ |
| `campaign-list.md` | ✓ | ✓ (per-source existence check) | ✓ | ✓ |
| `keyword-strategy.md` | ✓ | ✓ (per-source existence check) | ✓ | ✓ |
| `negative-keyword-master.md` | ✓ | ✓ (per-source existence check) | ✓ | ✓ |
| `reporting-schedule.md` | ✓ | ✓ (per-source existence check) | ✓ | ✓ |
| `bid-rules.md` | N/A — **primary source** | Header (Owner/date); it *is* the evidence | ✓ | ✓ (own internal items) |
| `budget-rules.md` | N/A — **primary source** | Header (Owner/date); it *is* the evidence | ✓ | ✓ (own internal items) |

**Notes.**
- The five derived context documents each carry a full Evidence section with a
  per-source in-repository existence check — strong practice.
- `bid-rules.md` and `budget-rules.md` are **authoritative primary sources**;
  they legitimately have no derived-Evidence section because they are the
  origin, not a derivation. `CLAUDE.md` protects them from reformatting.
- **Open evidence gap (from `target-metrics.md`):** two cited sources —
  `Amazon_BGCT_PayPerClick.pdf` and the "Approved PPC Metrics (2026-07-22)"
  record — are **external and not filed in `evidence/`**. Any KPI target resting
  on them currently cannot be independently opened by a future reader. This is
  the single most material evidence weakness in the layer and is already
  self-documented.

**Assessment:** Evidence quality is **high**, with one known, documented gap
(external metric sources not filed in `evidence/`).

---

## Queryability

Could another LLM, using only these documents, answer the core questions?

| Question | Answerable? | Basis |
|----------|-------------|-------|
| What is each document? | Yes | Every document opens with a one-line identity and a Purpose section |
| Why does each exist? | Yes | Purpose sections throughout |
| Which document is canonical for X? | Yes | Each declares itself canonical for its domain; Duplicate-Truth tables name the winner on conflict |
| Where should operational data live? | Yes | `evidence/` for raw data, `reports/` for reports, `decisions/` for approvals — stated consistently |
| How do documents relate? | Yes | Relationship and Dependency matrices in each spec; cross-links resolve |

Each derived document additionally carries its own **Queryability Test** table
ending in **PASS**.

**Result: PASS**

---

## Dependency Review

Skills referenced across all Dependency Matrix sections, checked against
`skills/`.

| Skill referenced | Exists in `skills/`? |
|------------------|----------------------|
| `ppc-brief` | Yes |
| `search-term-check` | Yes |
| `bid-check` | Yes |
| `acos-check` | Yes |
| `budget-check` | Yes |
| `waste-scan` | Yes |
| `keyword-expand` | Yes |
| `campaign-audit` | Yes |
| `report-draft` | Yes |
| `scale-check` | Yes |

**Every referenced skill exists.** No dependency references a non-existent skill;
no skill was invented.

**Unsupported (unconfirmed) dependencies:** The great majority of field→skill
mappings are marked `[VERIFY]`. This is correct and expected: all ten skill files
are early-stage stubs (`target-metrics.md` records them at "Status: Not started")
and none yet declares what it consumes. Confirmed mappings are limited to the few
a source document names explicitly (e.g. `bid-check`←`bid-rules.md`,
`budget-check`←`budget-rules.md`, `acos-check`←`target-metrics.md`) or where the
skill's name states its function (`report-draft`, `campaign-audit`). No mapping
has been asserted beyond that evidence.

**Assessment:** Dependency declarations are **sound and honest** — confirmed only
where evidenced, `[VERIFY]` everywhere else.

---

## Governance Consistency

| Governance requirement | Result | Basis |
|------------------------|--------|-------|
| No operational campaign data | ✓ Clean | Campaign register empty by design |
| No operational keyword data | ✓ Clean | Keyword register empty by design |
| No operational reports | ✓ Clean | No report rows; reports belong in `reports/` |
| No invented KPIs | ✓ Clean | KPI values trace to `target-metrics.md`; unknowns `[VERIFY]` |
| No invented campaigns | ✓ Clean | No names/IDs/portfolios asserted |
| No invented keywords | ✓ Clean | No keywords/search volumes/CPCs asserted |
| No invented search terms | ✓ Clean | None present |
| No invented report schedules | ✓ Clean | All cadence marked `[VERIFY]`; only folder-evidenced categories acknowledged |
| No governance conflicts | ✓ Clean | Safety wording (DRAFT-only, never modify Amazon Ads, human approval) consistent across all docs; no rule contradicts another |

**Safety wording is uniform.** Every derived document repeats the required
posture: outputs DRAFT recommendations only, never applies Amazon Ads changes,
human approval required, STOP-and-flag on implied automation. This matches
`CLAUDE.md` and `README.md` and is not reworded.

**Assessment:** Governance is **consistent and conflict-free**.

---

## Outstanding VERIFY Items

Consolidated across the Context layer, grouped by category. (Source documents
retain the authoritative wording; this is an index, not a restatement of rules.)

**A. Governance roles (repository-wide)**
- Business Owner — undefined
- Technical Reviewer — undefined
- Queryability Reviewer — undefined

**B. Evidence gaps**
- `Amazon_BGCT_PayPerClick.pdf` not filed in `evidence/`
- "Approved PPC Metrics (2026-07-22)" record not filed in `evidence/`

**C. Metrics (`target-metrics.md`)**
- ACoS/ROAS warning and critical thresholds
- No CPC target range (derived per-SKU by design)
- No TACoS target
- Sponsored Display minimum daily budget
- Marketplace-specific KPI overrides; non-UK values
- Campaign/SKU-specific (Hero SKU) KPI overrides
- Review frequency for every metric (pending approved reporting cadence)
- No defined action for CTR 0.5–0.3% and CVR 10–7% monitoring bands

**D. Campaigns (`campaign-list.md`)**
- Register unpopulated; no Amazon Ads export imported; no Campaign IDs
- Portfolio model; objectives; per-campaign owners
- `JD` naming-tag placement / mandatory status
- Draft lifecycle state; transition rules
- Marketplace-specific campaign rules; relationship cardinality
- Full Validation Status vocabulary (only `Conflict` defined)

**E. Keywords (`keyword-strategy.md`)**
- Search-intent taxonomy
- Competitor starting bid and definition of "proven" (partial in `bid-rules.md`)
- Brand-term bid/threshold (`bid-rules.md` `[VERIFY]`)
- Exact-match promotion criteria
- Match-type/category behaviour specifics; language strategy
- Marketplace keyword strategy

**F. Negative keywords (`negative-keyword-master.md`)**
- Match-type policy; approval workflow; removal criteria
- Shared negative-list policy; campaign-vs-ad-group scoping
- Competitor targeting-vs-negation boundary
- Temporary/Seasonal/Permanent distinctions

**G. Reporting (`reporting-schedule.md`)**
- No approved schedule/cadence (daily/weekly/monthly/quarterly timing)
- No report templates; no reporting calendar
- Per-report ownership and reviewer; executive reporting process
- KPI distribution rules; exception-report triggers; automation workflow

**H. Rule-file internal items**
- `budget-rules.md`: budget approval thresholds (£ bands); Stock Pause vs
  Re-Activation priority; SR-3/SR-4 tiebreaker; non-UK Spend Pause values
- `bid-rules.md`: brand/competitor bid figures; "Section B11" evidence naming
  standard

**I. Cross-layer**
- `context/amazon-vendor-bridge.md` unpopulated (blocks product references)
- Skill→field dependencies mostly `[VERIFY]` pending skill definition

---

## AIOS Readiness Score

| Category | Score | Rationale |
|----------|-------|-----------|
| Context Completeness | 84 / 100 | Seven review-set docs complete; registers correctly empty. Held back by the deferred vendor bridge and the absence of an approved reporting cadence. |
| Evidence Quality | 88 / 100 | Strong, per-source Evidence sections with in-repo checks. Held back by two external metric sources not filed in `evidence/`. |
| Duplicate Truth Prevention | 92 / 100 | Only deliberate, authority-pointed, reference-only repetition. No Medium/High risk. |
| Queryability | 95 / 100 | Every document self-identifies, declares canonical scope, and passes its own Queryability Test. |
| Governance Consistency | 93 / 100 | Uniform safety posture, no conflicts. Held back only by undefined governance roles (owner without approver). |
| Repository Consistency | 90 / 100 | Structure intact, naming and style consistent, LF/UTF-8, no unauthorised changes. Minor drag from many open `[VERIFY]` cross-links. |

**Overall Score: 88 / 100.**

**Largest remaining risks.**
1. **External evidence not filed (`evidence/`).** KPI targets rest on two sources
   a future reader cannot open — the highest-value single fix.
2. **No approved reporting cadence.** Cascades into every metric's undefined
   review frequency, weakening any time-based skill.
3. **Governance roles undefined.** The layer has an owner but no approver, so no
   document has a formal sign-off path.
4. **Vendor bridge unpopulated.** Any skill needing campaign↔product resolution
   is blocked until it is documented.

---

## Overall Readiness

**Ready for Skills Layer: YES.**

**Justification.** The Context layer is internally consistent, evidence-based,
highly queryable, and free of duplicate truth. Every canonical document declares
its scope, links rather than restates, and marks unknowns `[VERIFY]` instead of
inventing them. All skills referenced by dependency matrices exist. The empty
registers are the correct state for a specification layer awaiting verified
operational evidence.

The `YES` is qualified: individual skills will hit real `[VERIFY]` blockers where
they depend on unresolved inputs — most notably approved reporting cadence,
undefined governance sign-off, and the unpopulated vendor bridge. These are
**inputs to resolve as each skill is built**, not structural defects in the
Context layer. The foundation is sound enough to begin building skills against,
provided each skill respects the `[VERIFY]` markers and does not fabricate the
missing inputs.

---

## Recommendations

In priority order:

1. **File the two external metric sources into `evidence/`** (with source, date,
   date range) to close the `target-metrics.md` evidence gap.
2. **Define the three governance roles** (Business Owner, Technical Reviewer,
   Queryability Reviewer) so documents have an approver, not just an owner.
3. **Approve a reporting cadence** in `context/reporting-schedule.md`, which
   unblocks the review-frequency `[VERIFY]` items throughout `target-metrics.md`.
4. **Populate `context/amazon-vendor-bridge.md`** to enable campaign↔product and
   keyword↔product references.
5. **Resolve the rule-file `[VERIFY]` items** in `budget-rules.md` (approval £
   bands, tiebreakers, non-UK values) and `bid-rules.md` (brand/competitor bid
   figures, evidence naming standard) — these gate `budget-check` and `bid-check`.
6. **Confirm skill→field dependencies** in each context Dependency Matrix as each
   skill is defined, replacing `[VERIFY]` with evidenced mappings — not before.
7. **Keep registers empty** until verified Amazon Ads exports / approved
   operational evidence are imported; populate strictly from that evidence.

---

## Final Validation

- ✓ Only `validation/CONTEXT_REVIEW.md` created
- ✓ No existing files modified
- ✓ Repository structure unchanged
- ✓ No governance rewritten
- ✓ Evidence-based review only

**Output: PASS**

**Summary.** The Context layer passes review: consistent, evidence-based,
queryable, free of duplicate truth, and ready to support the Skills layer at an
overall readiness of **88/100**, with four tracked risks (external evidence
filing, reporting cadence, governance roles, vendor bridge) to resolve as skills
are built.

**Files reviewed:** `README.md`, `CLAUDE.md`, `context/target-metrics.md`,
`context/campaign-list.md`, `context/keyword-strategy.md`,
`context/negative-keyword-master.md`, `context/reporting-schedule.md`,
`context/bid-rules.md`, `context/budget-rules.md` (supporting: `skills/`,
`reports/README.md`, `validation/README.md`,
`context/amazon-vendor-bridge.md`).

**Files modified:** none. **File created:** `validation/CONTEXT_REVIEW.md`.
