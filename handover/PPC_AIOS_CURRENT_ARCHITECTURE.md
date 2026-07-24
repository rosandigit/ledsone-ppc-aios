# PPC AIOS Current Architecture (Version 1)

The authoritative description of the **current** LEDSone PPC AIOS implementation
as it exists in this repository today.

This document is **descriptive only**. It records what is already built and
approved. It is not a redesign, not a proposal, and not a specification for
future work. Where a future idea is mentioned at all, it appears only in
**Section 9 — Potential Future Enhancements** and is clearly labelled as a
proposal requiring separate approval.

Future architectural ideas are outside the scope of this document.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Title | PPC AIOS Current Architecture (Version 1) |
| Document Type | Descriptive architecture record (handover material) |
| Location | `handover/` — per its README, material another person or LLM needs to continue this work without verbal explanation |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | [VERIFY] — no Technical/Queryability Reviewer role is defined anywhere in this repository (see `validation/CONTEXT_REVIEW.md`) |
| Status | Active |
| Version | 1 |
| Scope | The repository as it exists on the date below. No future architecture. |
| Last Updated | 2026-07-24 |
| Source Documents | `README.md`, `CLAUDE.md`, every folder `README.md`, the ten files in `skills/`, and `validation/CONTEXT_REVIEW.md` |

This document **links** to the authoritative files rather than restating their
contents, in keeping with the repository's **No Duplicate Truth** rule
(`CLAUDE.md`). Business rules, KPIs, cadences and thresholds remain owned by
their source files in `context/`; nothing here redefines them.

---

## Section 1 — Purpose

### What the PPC AIOS is

The PPC AIOS is a **documentation and operating-knowledge repository** for
LEDSone Amazon PPC (Pay-Per-Click) advertising work. "AIOS" here means an
AI-operated system of documents: reusable AI context, evidence, repeatable
skill definitions, reports, decisions and handover material, organised so that
an AI (and a human) can prepare evidence-backed PPC work consistently.

It is a knowledge base, not an execution system. It stores documents; it does
not take actions in any advertising platform.

### What business problem it supports

LEDSone runs Amazon PPC campaigns that need regular, evidence-based review —
bids, budgets, keywords, search terms, wasted spend, efficiency (ACoS/ROAS) and
scaling decisions. The AIOS supports this by:

- keeping the **rules and targets** for that work in one authoritative place
  (`context/`);
- keeping the **evidence** those decisions must rest on (`evidence/`);
- defining **repeatable review skills** that turn evidence into structured,
  DRAFT findings (`skills/`);
- capturing the **reports, decisions and handover** that result.

The problem it solves is consistency and traceability: every recommendation is
prepared the same way, traces back to filed evidence, and is presented as a
DRAFT for a human to review — so PPC work does not depend on undocumented
memory or one-off judgement.

### Current scope

- The repository produces **documentation and DRAFT recommendations only**
  (`README.md`, `CLAUDE.md`).
- It has **no connection to Amazon Ads** and holds **no credentials or API
  access** (`README.md`).
- It never automates, applies, or executes any Amazon Ads change.
- All advertising changes are reviewed and applied **manually** by Jathukulan
  (or the authorised PPC Executive) in Amazon Ads.

### Scope of this document

This document describes **only the currently approved repository architecture**.
It does not describe planned features, aspirational layers, or ideas under
consideration as if they were built. Anything not currently implemented and
approved is not documented here as part of the current architecture.

---

## Section 2 — Repository Structure

Every folder below exists in the repository today. Folder names are reproduced
exactly. No folder has been invented, renamed, or added. Each top-level folder
carries its own `README.md` stating its purpose, what belongs in it, what does
not, its owner and its status.

### Top-level files

- **`README.md`** — repository purpose, layout, the AI workflow, and the
  evidence-first / human-approval / no-automation policies.
- **`CLAUDE.md`** — operating instructions for any AI working in the repository
  (Existing Asset First, Evidence First, Queryability First, No Duplicate Truth,
  Human Approval Required, Never Modify Amazon Ads, safety rules).

### `context/`

- **Purpose:** Reusable AI context — the stable reference facts and rules skills
  read before producing any DRAFT recommendation.
- **Contents:** `target-metrics.md`, `campaign-list.md`, `keyword-strategy.md`,
  `negative-keyword-master.md`, `reporting-schedule.md`, `amazon-vendor-bridge.md`,
  and the two authoritative rule files `bid-rules.md` and `budget-rules.md`.
- **Business value:** The single source of PPC truth. It is the authoritative
  home for KPI targets, bid and budget rules, keyword strategy and reporting
  governance, so no downstream document has to restate them.

### `skills/`

- **Purpose:** Definitions of the repeatable PPC checks the AI can run. Every
  skill produces DRAFT recommendations only.
- **Contents:** `README.md` plus ten skill files — `ppc-brief.md`,
  `search-term-check.md`, `bid-check.md`, `acos-check.md`, `budget-check.md`,
  `waste-scan.md`, `keyword-expand.md`, `campaign-audit.md`, `report-draft.md`,
  `scale-check.md`.
- **Business value:** Standardises how a PPC request is scoped, reviewed against
  the rules in `context/`, and turned into validated, evidence-checked findings.

### `evidence/`

- **Purpose:** Source data and exports that recommendations are based on
  (evidence-first: no recommendation without a reference here).
- **Contents:** `README.md`, `TEMPLATE_EVIDENCE_RECORD.md`, plus filed exports
  and their metadata records. Filename and metadata-record conventions are
  documented in `evidence/README.md`.
- **Business value:** Traceability. Every DRAFT recommendation references the
  evidence it derives from, including source, date and date range.

### `intelligence-inbox/`

- **Purpose:** Entry point for raw, unprocessed inputs before they are reviewed
  and filed elsewhere.
- **Contents:** `README.md` and the sub-folders `performance-alerts/`,
  `keyword-wins/`, `waste-log/`, `external-inputs/` and `processed/`. Items are
  triaged and moved to `processed/` once handled, with a pointer to where the
  outcome was filed.
- **Business value:** A single intake point so incoming observations and alerts
  are not lost and are filed to the correct authoritative layer.

### `campaigns/`

- **Purpose:** Documentation of Amazon PPC campaigns by lifecycle state.
  Documentation only — the repository never changes campaigns in Amazon Ads.
- **Contents:** `README.md` and the sub-folders `active/`, `paused/` and
  `archived/`, each with its own `README.md`.
- **Business value:** A per-campaign record organised by lifecycle, separate
  from rules (`context/`) and performance exports (`evidence/`).

### `reports/`

- **Purpose:** Drafted and sent reporting output.
- **Contents:** `README.md`, and the sub-folders `weekly/` and `monthly/` (each
  with a report template) and `sent/`. The report filename convention and report
  lifecycle are documented in `reports/README.md`; `sent/` holds immutable
  copies as an audit trail.
- **Business value:** Consistent, chronologically-sortable reports and a
  tamper-evident record of what was actually issued.

### `keywords/`

- **Purpose:** Keyword reference libraries used when drafting recommendations.
- **Contents:** `README.md` and the sub-folders `master-negatives/`,
  `exact-match-library/` and `expansion-candidates/`.
- **Business value:** Reusable keyword libraries, kept separate from keyword
  *strategy rules* (which live in `context/keyword-strategy.md`) and from raw
  search-term exports (which live in `evidence/`).

### `decisions/`

- **Purpose:** Record of decisions taken and approvals given, including
  rollbacks.
- **Contents:** `README.md` and `TEMPLATE_DECISION_RECORD.md`; one entry per
  decision (date, what was decided, who approved it, the evidence reference, the
  outcome).
- **Business value:** An auditable approval trail — the record that a human
  reviewed and approved a change before it was applied manually in Amazon Ads.

### `validation/`

- **Purpose:** Checks confirming that repository content is accurate, current
  and complete.
- **Contents:** `README.md` and `CONTEXT_REVIEW.md` (a read-only review of the
  Context layer).
- **Business value:** Quality assurance for the knowledge base — confirming
  documents are consistent, evidence-based and free of duplicate truth, and
  recording outstanding `[VERIFY]` items.

### `handover/`

- **Purpose:** Material another person or another LLM needs to continue this
  work without verbal explanation.
- **Contents:** `README.md`, `TEMPLATE_HANDOVER_NOTE.md`, and this document.
- **Business value:** Continuity. It lets a new operator (human or AI) pick up
  the work from the documents alone.

### `github-prompts/`

- **Purpose:** Prompts used to operate this repository, kept so runs are
  repeatable.
- **Contents:** `README.md` plus prompt files, each with the date used and its
  purpose.
- **Business value:** Repeatability and provenance of how the repository was
  operated.

---

## Section 3 — Current Workflow

The workflow below uses only stages that already exist in the repository. It is
the documented AI workflow from `README.md`, expressed against the folders that
implement it. No new stage or layer has been added.

```
Context        (context/ — read the authoritative rules and targets first)
   |
Evidence       (evidence/ — the filed source data a recommendation must rest on)
   |
Skills         (skills/ — a repeatable review turns evidence into DRAFT findings)
   |
Reports        (reports/ — validated findings formatted into a report draft)
   |
Decisions      (decisions/ — a human approves; the record is filed here)
   |
Handover       (handover/ — what is needed to continue the work)
```

Supporting folders feed this flow without adding a new stage:
`intelligence-inbox/` is the raw intake point that is triaged into the layers
above; `campaigns/` and `keywords/` hold reference documentation that skills
consult; `validation/` holds accuracy checks on the content; `github-prompts/`
stores the prompts used to run it.

Within `skills/`, the documented order of use is: `ppc-brief` scopes the request
first; the review skills (`search-term-check`, `bid-check`, `acos-check`,
`budget-check`, `waste-scan`, `keyword-expand`) produce validated findings;
`campaign-audit` consolidates them; `report-draft` formats them; `scale-check`
is the terminal review. This ordering is described in the skill files
themselves; this document does not restate their rules.

----------------------------------------------------

IMPORTANT OPERATIONAL BOUNDARY

The AIOS produces DRAFT recommendations only.

The AIOS never modifies Amazon Ads, executes automations, or applies bid,
budget, keyword, targeting, or campaign changes.

All advertising changes are manually reviewed and implemented in Amazon Ads
by Jathukulan (or the authorised PPC Executive) following the approved
business process.

After implementation, the AIOS uses new evidence from subsequent Amazon Ads
reports to verify outcomes, measure performance, and support future
recommendations.

No part of the AIOS performs automatic execution within Amazon Ads.

----------------------------------------------------

---

## Section 4 — Existing Skills

The ten skills below are the skills that currently exist in `skills/`. Names are
reproduced exactly; none has been added or renamed. Every skill outputs DRAFT
recommendations only, never applies Amazon Ads changes, requires human approval,
and STOPs and flags if automation is implied. Every skill applies the rules in
`context/` **by reference** and never restates them.

Each skill's output is a **completed structured template** (a DRAFT review
record), not an applied change. The "Outputs" below summarise that record.

### `ppc-brief`

- **Purpose:** The entry-point skill. Prepares an evidence-backed work brief that
  scopes a PPC request and routes it to the correct downstream skill. It analyses
  no performance and changes nothing.
- **Inputs:** Business request / user question / objective, campaign, ASIN/SKU,
  marketplace, date range; consults the `context/` documents.
- **Outputs:** A completed brief (objective, scope, campaign, marketplace,
  evidence available vs missing, context documents, known constraints,
  outstanding questions, recommended next skill).

### `search-term-check`

- **Purpose:** Evidence-based review of Amazon Ads Search Term data; prepares
  validated candidate keywords, candidate negatives, irrelevant terms and
  evidence gaps.
- **Inputs:** Search Term Report and related Amazon Ads reporting for the
  campaign, ad group, marketplace and date range.
- **Outputs:** A validated search-term review with classified findings and a
  recommended downstream skill.

### `bid-check`

- **Purpose:** Reviews bid performance evidence and prepares validated candidate
  findings (candidate increases/decreases, keep-observing, evidence gaps),
  applying the gates in `context/bid-rules.md` by reference.
- **Inputs:** Campaign Performance Report, Bid Report, campaign, ad group,
  marketplace, date range, business request, ASIN/SKU.
- **Outputs:** A completed bid-review record (bid findings, validation status,
  recommended action as DRAFT, recommended next skill).

### `acos-check`

- **Purpose:** Reviews campaign ACoS against the KPI targets in
  `context/target-metrics.md` (by reference) and prepares validated findings
  (within-target, needs-review, insufficient-evidence, conflicting-evidence,
  candidate opportunities).
- **Inputs:** Campaign Performance / Advertising Report (spend, sales, clicks,
  conversions), campaign, marketplace, date range, business request, ASIN/SKU.
- **Outputs:** A completed ACoS-review record with validation status and a
  recommended downstream skill.

### `budget-check`

- **Purpose:** Reviews campaign budget performance against `context/budget-rules.md`
  (by reference) and prepares validated findings (budget-limited, unused-budget,
  needs-investigation, insufficient-evidence, conflicting-evidence).
- **Inputs:** Campaign Performance Report, Budget Report, spend/order-volume/ACoS
  context, campaign, marketplace, date range, business request, ASIN/SKU.
- **Outputs:** A completed budget-review record (budget findings, validation
  status, recommended action as DRAFT, recommended next skill).

### `waste-scan`

- **Purpose:** Reviews campaign evidence to identify potential wasted advertising
  spend and prepares validated findings (candidate waste, needs-investigation,
  insufficient-evidence, conflicting-evidence), applying the sample-size gate in
  `context/bid-rules.md` by reference.
- **Inputs:** Campaign Performance Report, Search Term Report, budget/spend data,
  campaign, ad group, marketplace, date range, business request, ASIN/SKU.
- **Outputs:** A completed waste-scan record with candidate findings and a
  recommended downstream skill.

### `keyword-expand`

- **Purpose:** Reviews campaign and search-term evidence to identify candidate
  keyword expansion opportunities (new keywords, match-type expansion, grouping),
  applying `context/keyword-strategy.md` by reference. It creates no keyword.
- **Inputs:** Search Term Reports, keyword/performance reporting, any approved
  keyword-research export, campaign, marketplace, date range.
- **Outputs:** A validated expansion review with candidate findings and a
  recommended downstream skill.

### `campaign-audit`

- **Purpose:** Consolidates the validated findings from the upstream review
  skills into one structured campaign audit (overall health, validated
  strengths/risks, unresolved gaps, conflicts, follow-ups). It re-decides
  nothing.
- **Inputs:** The validated outputs of the upstream review skills, plus the
  underlying Amazon Ads evidence those reviews cite.
- **Outputs:** A single structured campaign audit for reporting and human review.

### `report-draft`

- **Purpose:** Converts the validated findings from `campaign-audit` and the
  upstream review skills into a structured PPC report **draft**. It performs no
  new analysis and reinterprets nothing.
- **Inputs:** The validated outputs of upstream skills (chiefly `campaign-audit`).
- **Outputs:** A report draft, for human review and (after approval) publication
  under `context/reporting-schedule.md`, filed in `reports/`.

### `scale-check`

- **Purpose:** The terminal review skill. Evaluates whether validated findings
  and approved context support considering a campaign for scaling, and prepares a
  DRAFT scale recommendation (candidate, ready, blocked, conflicting), applying
  the stock gate and efficiency gates by reference.
- **Inputs:** The validated outputs of upstream skills (chiefly `campaign-audit`,
  `acos-check`, `budget-check`) plus the Amazon Ads evidence they cite.
- **Outputs:** A DRAFT scale recommendation for reporting and human review. No
  downstream skill (terminal).

---

## Section 5 — Evidence Flow

This describes how evidence currently moves through the AIOS. Only behaviour that
exists today is described.

1. **Evidence source.** PPC evidence originates as Amazon Ads exports and reports
   (e.g. Search Term Reports, campaign performance exports, budget exports) and
   documented business requests. Raw, unprocessed inputs may first arrive in
   `intelligence-inbox/` for triage.

2. **Evidence processing (filing).** Evidence is filed in `evidence/` with its
   source, date and date range. Each export has an associated metadata record
   based on `evidence/TEMPLATE_EVIDENCE_RECORD.md`; original exports are kept
   unchanged. Skills consult this filed evidence together with the rules in
   `context/`. If required evidence is missing, a skill records **Insufficient
   Evidence** rather than proceeding.

3. **Reports.** Validated findings from the skills are formatted by `report-draft`
   into a report draft and filed in `reports/` (`weekly/`, `monthly/`), with sent
   copies kept immutably in `reports/sent/`.

4. **Decisions.** A human reviews the DRAFT. If approved, Jathukulan applies the
   change manually in Amazon Ads and logs the decision in `decisions/` (date,
   what was decided, who approved it, evidence reference, outcome). Rollbacks are
   done manually via Amazon Ads Change History and logged here too.

5. **Handover.** What another person or LLM needs to continue the work is kept in
   `handover/`.

6. **Verification via new evidence.** After a change is applied manually, later
   Amazon Ads reports become new evidence filed in `evidence/`, which subsequent
   skill runs use to review outcomes and inform future recommendations. This
   verification uses the *same* evidence flow above; it is not a separate stage
   or layer.

---

## Section 6 — Ownership

Ownership is documented exactly as it currently appears in the repository.

- **Owner:** Jathukulan. Every top-level `README.md`, every skill file, and
  `CLAUDE.md` name Jathukulan as `Owner`. Jathukulan reviews and applies every
  change manually in Amazon Ads.
- **Reviewer / approver roles:** Currently **undefined**. `validation/CONTEXT_REVIEW.md`
  records the **Business Owner**, **Technical Reviewer** and **Queryability
  Reviewer** roles as `[VERIFY]` — undefined repository-wide. Every skill file
  likewise carries `Reviewer: [VERIFY]`.

No Coordinator, Business Reviewer, Technical Reviewer, Queryability Reviewer,
"Claude Code governance" or "LLM governance" role is defined in the repository
today. This document does not invent any. The only governance model currently in
force is: **Owner = Jathukulan; approver roles are open `[VERIFY]` items; every
change requires human approval and is applied manually.**

---

## Section 7 — Validation

The validation currently implemented consists of:

- **The `validation/` folder**, whose purpose is checks confirming repository
  content is accurate, current and complete, holding validation checklists/results
  and records of `[VERIFY]` items resolved or outstanding (`validation/README.md`).
- **`validation/CONTEXT_REVIEW.md`**, a completed read-only review of the Context
  layer. It assesses completeness, duplicate truth, reference integrity, evidence
  quality, queryability, dependencies and governance consistency, and lists
  outstanding `[VERIFY]` items. It is read-only: it modifies no reviewed file and
  records corrections belong in the owning file.
- **Per-document self-checks.** Each skill file and each reviewed context document
  carries its own **Queryability Test** table ending in **PASS**, and uses the
  `[VERIFY]` marker for anything not yet documented from a verified source
  (required by `CLAUDE.md`).
- **The `[VERIFY]` discipline itself.** Unverified values are marked `[VERIFY]`
  and left unanswered rather than guessed, which functions as an ongoing
  correctness check across the repository.

No validation stage beyond the above currently exists. This document does not add
one.

---

## Section 8 — Current Limitations

Known limitations of the current implementation, taken from what the repository
already documents. These are stated, not solved; this document proposes no fixes.

- **No Amazon Ads connection or execution.** By design, the repository holds no
  credentials and cannot apply, automate or verify changes directly in Amazon
  Ads; all application and rollback is manual.
- **Empty operational registers.** The campaign, keyword, negative-keyword and
  reporting registers in `context/` are intentionally empty pending verified
  Amazon Ads exports (`validation/CONTEXT_REVIEW.md`).
- **Vendor bridge unpopulated.** `context/amazon-vendor-bridge.md` is a stub
  (`Status: [VERIFY]`), so ASIN/SKU-to-campaign resolution cannot currently be
  completed. This is a recurring `[VERIFY]` limitation across skills.
- **Governance roles undefined.** Business Owner, Technical Reviewer and
  Queryability Reviewer are `[VERIFY]`; the repository has an owner but no defined
  approver role.
- **No approved reporting cadence.** `context/reporting-schedule.md` marks the
  cadence `[VERIFY]`, which cascades into undefined review frequencies elsewhere.
- **External evidence not filed.** Sources cited elsewhere (e.g.
  `Amazon_BGCT_PayPerClick.pdf` and the "Approved PPC Metrics (2026-07-22)"
  record) are not yet filed in `evidence/`.
- **No approved retention policy.** No retention/archival period is defined for
  evidence or for weekly/monthly report drafts; only `reports/sent/` immutability
  is documented.
- **No central numeric waste threshold.** `waste-scan` relies on the sample-size
  gate and evidence; no approved numeric waste cut-off exists in `context/`.
- **Approval workflow undocumented.** Beyond "human approval required", the
  specific reviewer/approver path is `[VERIFY]`.
- **Skill→field dependencies largely `[VERIFY]`.** Many skill dependency mappings
  remain unconfirmed pending resolved inputs.

---

## Section 9 — Potential Future Enhancements

The ideas below are proposals only.

They are NOT part of the current approved PPC AIOS architecture.

They require separate design review and formal approval before implementation.

The following are examples of possible future work, listed to record that they
are *not yet built*. They must not be read as current architecture, and none has
been designed or approved here. Each corresponds to a documented open item, and
resolving any of them is future work, not existing behaviour:

- *(Future idea)* Filing the outstanding external evidence sources into
  `evidence/`.
- *(Future idea)* Defining the currently `[VERIFY]` governance/approver roles.
- *(Future idea)* Approving a reporting cadence in `context/reporting-schedule.md`.
- *(Future idea)* Populating `context/amazon-vendor-bridge.md` to enable
  product↔campaign resolution.
- *(Future idea)* Documenting approved retention policies for evidence and report
  drafts.

Any of the above would require its own design review and formal approval, and
would be documented separately at that time — not in this current-architecture
record.

---

## Section 10 — Queryability Check

Using only this document, another LLM can answer the required questions:

| Question | Answerable? | Where |
|----------|-------------|-------|
| What is the PPC AIOS? | Yes | Section 1 |
| What business problem does it solve? | Yes | Section 1 |
| What folders currently exist? | Yes | Section 2 |
| What does each folder do? | Yes | Section 2 |
| How does work currently flow? | Yes | Section 3 |
| Which skills currently exist? | Yes | Section 4 |
| How is evidence currently used? | Yes | Section 5 |
| Who owns the work? | Yes | Section 6 |
| What are the current limitations? | Yes | Section 8 |

**Result: PASS** — each question is answerable from this document without verbal
explanation. For the authoritative *values* behind any rule, KPI, cadence or
threshold, this document links to the owning file in `context/` rather than
restating it (No Duplicate Truth).

---

## Final Quality Check

- ✓ Describes only the current repository as it exists today.
- ✓ No new architecture, folder, workflow stage or layer introduced (no Finding,
  Intelligence, Learning or Verification layer added).
- ✓ No duplicate truth — rules, KPIs and thresholds are linked to their owning
  files, not restated.
- ✓ No new governance model invented; roles left as the documented `[VERIFY]`
  items.
- ✓ No repository restructuring proposed; no existing file modified.
- ✓ No implementation code generated.
- ✓ Future ideas confined to Section 9 and clearly labelled as proposals
  requiring separate approval.
- ✓ Descriptive, not prescriptive.

**Output: PASS**
