# evidence

## Purpose
Source data and exports that recommendations are based on. Evidence-first: no recommendation without a reference here.

## What belongs here
- Exports, screenshots and data extracts, each with the date, source and date range recorded

## What should NOT be stored here
- Conclusions or recommendations (use `reports/` or `decisions/`)
- Edited or re-cut versions of an original export

## Owner
Jathukulan

## Status
Active

## Evidence Filename Convention

Recommended repository naming patterns for material filed in this layer.

**Evidence export:** `YYYY-MM-DD-source-description.ext`

Examples:

- `2026-07-22-amazon-search-term-report.csv`
- `2026-07-22-amazon-campaign-performance.xlsx`
- `2026-07-22-amazon-budget-export.csv`

**Metadata record:** `YYYY-MM-DD-source-description-record.md`

Examples:

- `2026-07-22-amazon-search-term-report-record.md`

These are **repository naming conventions only. They are NOT business rules.**
They exist so evidence sorts chronologically and each export can be matched to its
metadata record; they define no schedule, threshold or operational requirement.

## Metadata Relationship

Every evidence export should have an associated **metadata record** based on
`evidence/TEMPLATE_EVIDENCE_RECORD.md`. The metadata record documents:

- source
- collection date
- evidence date range
- related skills
- related report

The metadata record provides traceability; the **original evidence files remain
unchanged** (consistent with "What should NOT be stored here" above — no edited or
re-cut versions of an original export). The record points to the original via its
`Source File` / `Evidence References` fields; it never replaces or alters it.

## Evidence Retention Governance

**This section is the owning governance for evidence retention.** It is recorded
here and nowhere else; other documents reference it rather than restating it.

**Approved by the Owner under Scope A — governance facts only.** Recording this
policy authorises no action: no storage was provisioned or accessed, no folder
created, no archive performed, no deletion performed, and no evidence file moved,
copied or uploaded.

| Attribute | Approved value |
|-----------|----------------|
| Scope | Confidential primary evidence stored in the approved **non-Git, company-controlled** storage architecture (architecture direction recorded in `decisions/DRAFT_DECISION_CONFIDENTIAL_BINARY_EVIDENCE_STORAGE.md`) |
| Retention period | **Indefinite** |
| Retention start event | **Upload date** |
| Lifecycle / end action | **Archive** |
| Archive trigger | **[VERIFY]** — not supplied |
| Preservation exception | **[VERIFY]** — not supplied |
| Policy owner | **MD** |
| Approval scope | **Scope A — governance facts only** |

**How to read "Indefinite".** It means **no defined expiry period was supplied**.
It does **not** by itself mean permanent active storage, "never archive", "never
delete", a legal hold, indefinite archive retention, or automatic preservation.
The Owner supplied **Archive** as the lifecycle end action while leaving the
**archive trigger `[VERIFY]`**; that combination is recorded as given and is **not
resolved by inference**.

**What this policy does not establish:**

- **No archive trigger.** When evidence moves to archive is `[VERIFY]`.
- **No preservation exception.** Any condition requiring evidence to be preserved
  or exempted is `[VERIFY]`.
- **No deletion or disposal rule** has been supplied, and none is created here.
- **No archive location is approved** by this policy, and none is named.
- **No storage location, implementation or provisioning is authorised.**
- **Evidence outside the stated scope is not covered.** Retention for evidence
  that is not confidential primary evidence in the approved non-Git architecture
  remains undocumented — see **Known Limitations**.
- **The evidence lifecycle flow** (import → reference → archival) remains
  undefined and is a separate open item — see **Known Limitations**.
- **Supersession** of primary evidence is not addressed here; it is a separate
  open question recorded in
  `decisions/DRAFT_DECISION_CONFIDENTIAL_BINARY_EVIDENCE_STORAGE.md`.

**Policy owner note.** "MD" is recorded exactly as supplied by the Owner. This
document defines no role catalogue, and no reviewer or approver role is
established by recording it.

## Duplicate Truth Prevention

- Evidence files remain the **original source material**.
- Metadata records provide **traceability only** and are never a source of business
  truth.
- Business rules remain in the **Context layer** (`context/`).
- Recommendations remain in **Reports** (`reports/`).
- Approvals remain in **Decisions** (`decisions/`).

Nothing in this document defines or restates a business rule, KPI, cadence or
threshold; those are referenced to their owning documents.

## Known Limitations

Genuine unresolved governance items (documented, not invented):

- **Evidence lifecycle** — no documented flow from import → reference → archival is
  defined for evidence. [VERIFY]
- **Retention policy — partly approved.** Retention governance for **confidential
  primary evidence in the approved non-Git, company-controlled storage
  architecture** is now recorded in **Evidence Retention Governance** above. Three
  things remain open: the **archive trigger** [VERIFY]; any **preservation
  exception** [VERIFY]; and retention for **evidence outside that scope**, for
  which no period or archival rule is documented [VERIFY]. No deletion or disposal
  rule is documented for any evidence. [VERIFY]
- **Reviewer role** — no Technical/Queryability Reviewer is defined
  repository-wide. [VERIFY]
- **Outstanding external evidence** — sources cited elsewhere but not yet filed
  here (e.g. `Amazon_BGCT_PayPerClick.pdf` and the "Approved PPC Metrics
  (2026-07-22)" record noted in `context/target-metrics.md` and
  `validation/CONTEXT_REVIEW.md`) remain un-filed. [VERIFY]
