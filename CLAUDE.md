# CLAUDE.md — LEDSone PPC AIOS

Operating instructions for any AI working in this repository.

## Repository purpose

This repository stores documentation, reusable AI context, evidence and
operating knowledge for LEDSone Amazon PPC work.

It never performs Amazon Ads changes. It never automates Amazon PPC. It only
generates documentation and DRAFT recommendations.

## Existing Asset First

Check what already exists before creating anything. If a file, folder or
document already exists, leave it as it is and report `Already exists.`

Never overwrite, delete, rename or move existing files. Never reorganise the
repository. Never regenerate existing documentation.

One narrow, named exception to this rule exists — see **Approved Exception —
Marketplace-Specific Rule Architecture Migration** below. It authorises no file
operation today, and applies to nothing outside the scope defined there.

## Evidence First

Every recommendation must trace back to evidence in `evidence/`, recorded with
its source, date and date range.

Never invent Amazon PPC rules, business processes, metrics or thresholds. If a
value is not documented from a verified source, mark it `[VERIFY]` and leave it
unanswered.

## Queryability First

Write so another LLM can use the file tomorrow with no verbal explanation.
State the source and the date. Spell out what a term means. Prefer plain,
explicit statements over shorthand.

## No Duplicate Truth

Each fact lives in exactly one place. Link to it instead of restating it.

No duplicate documents. No alternative versions. No summaries of the
authoritative rule files.

## Human Approval Required

Every recommendation involving bids, budgets, keywords, campaigns or targeting
must state:

- Outputs DRAFT recommendations only.
- Never applies Amazon Ads changes.
- Human approval required.

Jathukulan reviews and applies every change manually.

## Never Modify Amazon Ads

This repository has no connection to Amazon Ads and holds no credentials. It
produces documents, not actions.

## Never Execute Automation

Do not write or run anything that changes Amazon Ads. If a request implies
automation, **STOP** and report it rather than proceeding.

## Repository Safety Rules

- Create files only if they are missing.
- `context/bid-rules.md` and `context/budget-rules.md` are authoritative
  business documents. Never rewrite, improve, summarise, reorder or reformat
  them. If they exist, leave them untouched. (One narrow, named exception
  permits a future, separately-approved relocation of these files — see
  **Approved Exception — Marketplace-Specific Rule Architecture Migration**. It
  authorises no change today, and never permits rewriting their content.)
- Every skill file in `skills/` carries identical safety wording. Do not
  reword it.
- Use UTF-8 encoding and LF line endings.
- Do not create binary files.
- Report what was created, what already existed and what was left untouched.

## Approved Exception — Marketplace-Specific Rule Architecture Migration

**Authorised by Jathukulan (Owner) on 2026-07-30.**

This clause is a **narrow, named exception** to *Existing Asset First* ("Never
overwrite, delete, rename or move existing files. Never reorganise the
repository.") and to the Repository Safety Rule protecting
`context/bid-rules.md` and `context/budget-rules.md`. It applies to nothing
outside the scope defined here.

### What is authorised

A **future, separately-scoped migration task** is authorised to move,
reorganise and split **exactly these four rule families, and only these four**:

1. Bid Rules
2. Budget Rules
3. Hour Budget Rules
4. Product Pause Rules

into a marketplace-specific structure covering **exactly these four
marketplaces, and only these four**:

**UK, DE, FR, IT.**

**US is excluded.** No task acting under this exception may create, populate or
reference US rule content. Any marketplace not named above is outside this
exception entirely.

### What is NOT authorised

- **This clause performs no file operation and authorises none today.** It
  moves, renames, splits, creates and deletes nothing. Recording it changes no
  file in `context/`.
- **It is not the migration design.** The canonical marketplace-routing design
  is a separate task; it is neither performed nor pre-empted here, and no folder
  or file layout is approved by this clause.
- **It does not relax the general rule.** *Existing Asset First* remains in
  force, unchanged, for every other file and every other case. This exception is
  not precedent for any other reorganisation.

### Preconditions — both required before any migration executes

The authorised migration may execute **only after both** of the following are
complete:

**(a)** a canonical marketplace-routing design has been separately completed and
approved; **and**

**(b)** a dedicated migration task has been explicitly scoped, reviewed and
approved before execution.

Until both hold, the four rule files remain untouched.

### Binding conditions on the migration when it occurs

- **Existing verified UK content is preserved.** It is relocated or
  restructured only — never deleted, rewritten, summarised or reinterpreted.
- **No UK value may be copied, inferred or used as a placeholder for DE, FR or
  IT** — not as a default, not as a starting point, not as an example.
- **DE, FR and IT rule files are created empty or `[VERIFY]`** and remain so
  until real, verified, marketplace-specific evidence exists for that
  marketplace.
- **No routing mechanism may default to UK.** Where marketplace is missing,
  ambiguous, or outside the supported scope above (including US), the outcome is
  `[VERIFY]` / Insufficient Evidence — never a UK fallback.

### Status of this authorisation

This clause records the Owner's authorisation of the exception only. It is
**not** the migration, **not** the routing design, and **not** approval of any
particular structure. Each remains a separate task requiring its own scope and
approval.

## Owner

Jathukulan

## Status

Active
