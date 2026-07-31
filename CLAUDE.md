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

## Approved Authorisation — Phase 1a Marketplace-Routing Implementation

**Authorised by Jathukulan (Owner) on 2026-07-31. Status: Owner Approved —
authorisation only.**

This clause is a **second, separate and narrower** exception to *Existing Asset
First* ("Never overwrite, delete, rename or move existing files"). It is **not**
part of, and does not extend, amend or interact with, the **Approved Exception —
Marketplace-Specific Rule Architecture Migration** above. That clause governs the
future migration of the four rule families. **This clause governs neither those
files nor that migration.** The two must never be read together as one
authorisation.

### A. What is authorised

A **future, separately-scoped Phase 1a implementation task** is authorised to:

1. create the one canonical marketplace-routing registry, at the approved path
   **`context/marketplace-routing.md`** (see **B**); and
2. modify **`context/README.md`**, only as far as necessary to make that registry
   discoverable from the `context/` folder README (see below); and
3. modify **`skills/hour-budget-check.md`**, only as far as necessary for it to
   consume the approved marketplace-routing model; and
4. modify **`skills/product-pause-check.md`**, only as far as necessary for it to
   consume the approved marketplace-routing model.

**Those four paths are the complete set.** No other existing file may be modified
under this authorisation, and no other file or folder may be created under it.
*Existing Asset First* remains in force, unchanged, for every other skill and
every other file.

The safety wording carried by every skill file remains protected by the
**Repository Safety Rules** above and must not be reworded.

**Scope of the `context/README.md` change — discoverability only.** It may name
the canonical registry, reference its path, state at a high level that the
registry resolves marketplace routing for the approved Phase 1 architecture, and
point readers to the registry as the authoritative operational routing owner.

It must **not** duplicate the registry's routing matrix, duplicate marketplace
authorisation data, duplicate the marketplace-scope decisions, contain PPC rule
values, contain Bid, Budget, Hour Budget or Product Pause rule content, define
routing logic independently, or become a second routing owner.
**`context/README.md` remains descriptive and navigational only; the registry is
the operational routing owner.**

### B. The approved registry path — and the required ordering

**Canonical Phase 1a marketplace-routing registry:
`context/marketplace-routing.md`.**

**Status: OWNER APPROVED** — approved by Jathukulan (Owner) on 2026-07-31,
following an explicit proposal, an *Existing Asset First* check and a
duplicate-truth check. **This supersedes the earlier `[VERIFY]` status** of the
registry path and filename.

**Path approval is not creation.** The registry **has not been created**, and this
clause does not create it. The Phase 1a implementation task may create it **only**
at the approved path above; any other path requires separate Owner approval.

**Registry creation must occur before, or atomically with, the dependent changes**
to `context/README.md`, `skills/hour-budget-check.md` and
`skills/product-pause-check.md`.

**The repository must never be left in a state where either authorised skill, or
`context/README.md`, refers to** a registry that does not exist, a path other than
the approved one, or a registry that was not created as part of the approved
implementation.

This does **not** require the registry, the README update and the skill
integrations to be separate commits. **One bounded implementation task, and one
commit, are permitted** — provided the final validated state contains the approved
registry, the minimal README discoverability update, both authorised skill
integrations, and no broken or unresolved registry reference. Separate commits are
not required unless some other governance requires them.

**This clause executes none of those operations today.**

### C. The two-test model must be preserved

The implementation must preserve the approved separation of two independent
questions:

- **Test 1 — authorisation:** is the marketplace authorised for this
  architecture?
- **Test 2 — content:** does the owning rule source hold the verified content
  the requested activity needs?

Neither answers the other, in either direction, and they must never be collapsed
into a single test.

**The registry owns marketplace authorisation and routing only.** It must **not**
become the owner of PPC rule values, rule-content availability, thresholds,
formulas, marketplace-specific business rules, or evidence sufficiency. Each of
those remains with its existing or future approved owning asset.

### D. Marketplace boundary

The authorised architecture scope remains exactly **UK, DE, FR and IT**.

**US is explicitly excluded. CA is outside scope.**

Existing NL/ES content remains preserved as required by the Owner marketplace-scope
decision, but **NL and ES are not authorised routing marketplaces**.

**The existence of content does not itself grant routing authorisation.**

### E. No default marketplace

Where marketplace is **missing, ambiguous, unsupported, or outside the authorised
scope**, the implementation must **not** default to UK or to any other
marketplace. The outcome remains unresolved — `[VERIFY]` / Insufficient Evidence
— as the owning skill already provides. **No new repository-wide status
vocabulary is introduced.**

### F. What is NOT authorised

This clause does not authorise:

- **implementation during the task that recorded it** — it performs no file
  operation and authorises none today;
- Phase 1b, or modification of any other skill;
- Phase 2, or any marketplace rule-family migration;
- moving, renaming, splitting or restructuring any of the four rule-family files;
- populating marketplace-specific Bid, Budget, Hour Budget or Product Pause rule
  content;
- any change to a PPC business rule, threshold, percentage, currency amount,
  click gate, evaluation window, formula or decision criterion;
- copying, inferring, adapting or currency-converting UK values into DE, FR or
  IT;
- US routing or US rule content;
- adding CA, NL or ES to the authorised architecture;
- creating the registry today, or ever creating it at any path other than the
  approved one;
- modifying `context/README.md` today, or extending that future change beyond
  discoverability;
- modifying any file outside the four paths listed in **A**.

### G. Relation to existing governance

- `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` remains the
  owner of the **approved Phase 1 architecture**.
- `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` remains the owner
  of the **Owner marketplace-scope decisions**.
- **`CLAUDE.md` owns the AI operating and safety authorisation** — what a task
  may and may not do — and nothing else.

This clause therefore states boundaries, not architecture. It does not reproduce
the routing design and holds no PPC rule content. Where it and an owning record
appear to disagree, **the owning record above wins.**

### H. Status of this authorisation

- **Owner:** Jathukulan · **Date:** 2026-07-31 · **Status:** Owner Approved —
  authorisation and registry-path approval only
- **Phase 1a Implementation Started:** NO
- **Registry Created:** NO
- **Registry Path Approved:** YES — `context/marketplace-routing.md`
- **`context/README.md` Modified:** NO — future modification authorised for
  discoverability only, see **A**
- **Phase 1b Authorised:** NO
- **Phase 2 Authorised By This Clause:** NO

**Migration precondition (b) remains OPEN.** This clause neither satisfies nor
affects it. Precondition (b) gates the migration of the four rule families; Phase
1a moves no rule file and is outside that clause's subject matter. Only a separate
approved record may change (b)'s status.

## Owner

Jathukulan

## Status

Active
