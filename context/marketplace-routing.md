# Marketplace Routing

The **canonical operational owner of marketplace routing** for the approved Phase 1
marketplace architecture in the LEDSone Amazon PPC AIOS.

This file answers exactly one question: **is a given marketplace authorised for
Phase 1 routing?** It answers nothing else. It holds **no PPC business-rule
content** — no threshold, monetary value, percentage, ratio, click gate, order
count, price band, spend trigger, budget figure, multiplier, efficiency value,
evaluation window or formula appears anywhere in it, and none may ever be added.

**Safety wording (AIOS boundary — do not reword):**

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## Document Metadata

| Field | Value |
|-------|-------|
| Document Type | Canonical operational routing registry — marketplace authorisation only |
| Owner | Jathukulan — repository `Owner` in `README.md` and `CLAUDE.md` |
| Reviewer | `[VERIFY]` — no Technical / Queryability Reviewer role is defined anywhere in this repository (see `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01). None is assigned or invented here. |
| Status | Active |
| Created | 2026-07-31 |
| Authoritative for | **Marketplace routing authorisation (Test 1) and nothing else.** |
| Explicitly NOT authoritative for | Any PPC business rule; whether verified rule content exists for a marketplace (Test 2); evidence sufficiency; marketplace scope decisions; the Phase 1 architecture itself. |
| Phase | Phase 1a. Phase 1b and Phase 2 are not implemented. |

---

## Purpose

**The business question this file answers:**

> Given a marketplace, is that marketplace authorised for routing under the
> approved Phase 1 marketplace architecture?

**Why it exists.** Before this file, no asset in the repository could answer that
question. The nearest thing was a per-skill check that asked whether *values were
defined* for a marketplace — a different question, and one that produces the wrong
answer where content exists for a marketplace that was never authorised.

This file separates the two questions permanently. See **The Two-Test Model**.

---

## What This File Owns — and What It Does Not

| | |
|---|---|
| **Owns** | **Test 1 — routing authorisation.** Whether a marketplace is authorised for Phase 1 routing, and what outcome applies when it is not. |
| **Does NOT own** | **Test 2 — content availability.** Whether the owning rule source actually holds verified content for a marketplace. That remains with the owning `context/` rule file, at evaluation time. |
| **Does NOT own** | Any PPC business-rule value, threshold, formula, window or marketplace parameter. Those remain with the owning `context/` rule file. |
| **Does NOT own** | Evidence sufficiency. That remains with the consuming skill's own `Required Evidence` rules. |
| **Does NOT originate** | Marketplace authorisation itself. It **operationalises** authorisation granted elsewhere — see **Where Authorisation Comes From**. |

**If this file and an owning source ever appear to disagree, the owning source
wins.** This file states no business rule, so on any business rule there is
nothing here to win with.

---

## Where Authorisation Comes From

This file **cites** its authorities; it does not restate them as independent
truth, and it may not be used to widen them.

| Authority | What it originates |
|-----------|--------------------|
| `CLAUDE.md` → **Approved Exception — Marketplace-Specific Rule Architecture Migration** | The authorised marketplace set, the exclusion of US, and the migration authorisation. |
| `CLAUDE.md` → **Approved Authorisation — Phase 1a Marketplace-Routing Implementation** | The Phase 1a implementation authorisation, this file's approved path, and the operating boundaries. |
| `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md` | The Owner marketplace-scope decisions, including NL/ES preservation and US/CA treatment. |
| `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md` | The approved Phase 1 routing architecture, including the two-test model. |

**On any conflict, the authority above wins.** Adding a marketplace here without a
corresponding change to those authorities is invalid.

---

## The Two-Test Model

Routing requires **two independent tests**. Neither implies the other, in either
direction, and they must never be collapsed into one.

| | Question | Owner |
|---|---|---|
| **Test 1 — Routing authorisation** | Is this marketplace authorised for Phase 1 routing? | **This file** |
| **Test 2 — Content availability** | Does the owning rule source hold verified content usable for that marketplace? | **The owning `context/` rule file**, at evaluation time |

- **Passing Test 1 does not mean content exists.** An authorised marketplace may
  have no verified rule content for a given rule family.
- **Passing Test 2 does not mean routing is authorised.** Content may exist in a
  rule source for a marketplace that is not authorised for routing.

**A consumer must apply both. Either test failing stops the route.**

---

## Test 1 — Authorised Marketplaces

| Marketplace | Test 1 | Basis |
|-------------|--------|-------|
| **UK** | **Authorised** | Named in the approved architecture scope |
| **DE** | **Authorised** | Named in the approved architecture scope |
| **FR** | **Authorised** | Named in the approved architecture scope |
| **IT** | **Authorised** | Named in the approved architecture scope |
| **US** | **Not authorised — explicitly excluded** | Named and excluded by name in `CLAUDE.md` |
| **CA** | **Not authorised — outside scope by omission** | Never named in `CLAUDE.md`; falls under "any marketplace not named is outside this exception entirely" |
| **NL** | **Not authorised** | Not in the approved architecture scope. Existing NL content in a rule source is preserved but grants no routing authorisation |
| **ES** | **Not authorised** | As NL |
| Any other marketplace | **Not authorised** | Not in the approved architecture scope |

**US and CA are both unauthorised for different reasons, and the distinction is
not collapsed here.** US is excluded by name; CA is outside scope by omission.

**Content existence never grants routing authorisation.** A marketplace appearing
anywhere in a rule source — including NL and ES — does not make it authorised.
This table, not the presence of content, is Test 1.

**No marketplace may be added to this table** without a corresponding change to the
authorities named above. Adding one here alone is invalid and grants nothing.

---

## Outcomes

| Input condition | Test 1 outcome | What the consumer does |
|-----------------|----------------|------------------------|
| Marketplace is **authorised** (see table) | **Pass** | Proceed to **Test 2** against the owning rule source. Test 1 passing is not a verdict. |
| Marketplace is **not authorised** — US, CA, NL, ES or any other | **Fail** | Do not route. Record the outcome **prescribed by `CLAUDE.md` → Phase 1a §E**: `[VERIFY]` / Insufficient Evidence, as the owning skill already provides. |
| Marketplace is **missing** | **Cannot be evaluated** | Do not route. Do not infer a marketplace. Record the **§E** outcome: `[VERIFY]` / Insufficient Evidence, as the owning skill already provides. |
| Marketplace is **ambiguous** | **Cannot be evaluated** | As missing — the **§E** outcome applies. Do not select the more likely marketplace. |

`CLAUDE.md` → Phase 1a **§E** governs all four of these states — *missing,
ambiguous, unsupported, or outside the authorised scope* — and assigns them one
outcome: **`[VERIFY]` / Insufficient Evidence, as the owning skill already
provides.** Every Test 1 failure defers to it. There is no separate outcome for
"not authorised".

### No default marketplace

**Where marketplace is missing, ambiguous, unsupported or outside the approved
scope, the outcome is never UK, and never any other marketplace.** There is no
fallback, no default and no nearest-match. A route occurs only for a marketplace
explicitly listed as **Authorised** above.

**Currency never identifies a marketplace.** Several authorised marketplaces share
a currency, and denomination is not evidence of marketplace.

### Outcome vocabulary is not owned here

**`CLAUDE.md` → Phase 1a §E owns the outcome** for every marketplace state above.
This file applies it by reference and adds nothing to it.

This file **does not introduce a status vocabulary**, and §E forbids one:
*"No new repository-wide status vocabulary is introduced."* `[VERIFY]`,
Insufficient Evidence, No Action and Conflict continue to mean exactly what the
consuming skill's own Decision Rules already say. **Nothing here redefines,
widens or reinterprets them**, and no status such as "Not Authorised",
"Marketplace Out of Scope" or "Unsupported Marketplace" exists or is created.

---

## Test 2 — Where Content Availability Is Answered

This file does **not** answer Test 2 and does **not** record whether content
exists. It points to the owning source so a consumer knows where to ask.

| Rule family | Owning source — sole authority on its own content |
|-------------|---------------------------------------------------|
| Bid Rules | `context/bid-rules.md` |
| Budget Rules | `context/budget-rules.md` |
| Hour Budget Rules | `context/hour-budget-rules.md` |
| Product Pause Rules | `context/product-pause-rules.md` |

**This table is a pointer, not a content status.** It records who owns each rule
family, nothing about what any of them contains. **Recording content-availability
status in this file is prohibited** — it would duplicate a fact the owning source
already owns, and would go stale silently whenever that source changed.

**Authorisation never manufactures content.** Where a marketplace passes Test 1 but
the owning source holds no verified content for it, the outcome is the consuming
skill's existing `[VERIFY]` / Insufficient Evidence behaviour — never a substituted
value from another marketplace.

---

## How a Consuming Skill Uses This File

1. Determine marketplace from the request or filed evidence, per the skill's own
   existing input rules. **Never infer a missing marketplace.**
2. **Test 1** — check the marketplace against **Authorised Marketplaces** above.
   If it is not authorised, or cannot be determined, **stop** and record the
   `CLAUDE.md` §E outcome — `[VERIFY]` / Insufficient Evidence, as the skill
   already provides. Do not proceed to step 3.
3. **Test 2** — separately determine, from the owning rule source, whether verified
   content usable for that marketplace exists. If it does not, apply the skill's
   existing `[VERIFY]` / Insufficient Evidence behaviour and stop.
4. Only when **both** tests pass may the skill proceed to evaluate the rule, by
   reference to the owning source as it already does.

**Consuming skills at Phase 1a:** `skills/hour-budget-check.md` and
`skills/product-pause-check.md`. No other skill consumes this file yet — extending
it to further skills is **Phase 1b**, which is not authorised.

---

## Duplicate Truth Prevention

Per `CLAUDE.md` → *No Duplicate Truth*.

**What this file owns:** Test 1 — marketplace routing authorisation. That is new
operational truth and exists nowhere else.

**What it must never become:**

- **A PPC business-rule owner.** No threshold, monetary value, percentage, ratio,
  click gate, order count, price band, spend trigger, budget figure, multiplier,
  efficiency value, evaluation window or formula may appear here. This is
  verifiable by reading the file: it contains none.
- **A content-availability owner.** Test 2 is answered only by the owning rule
  source.
- **A second marketplace-scope owner.** Scope decisions remain with
  `decisions/DECISION_MARKETPLACE_RULE_ARCHITECTURE_SCOPE.md`.
- **A second architecture owner.** The approved architecture remains with
  `decisions/DECISION_MARKETPLACE_ROUTING_ARCHITECTURE_PHASE1.md`.
- **A second authorisation source.** Authorisation remains with `CLAUDE.md`.

`context/README.md` names this file for discoverability only; it is navigation and
is not a routing owner.

---

## Known Limitations

Genuine unresolved items. None is worked around by inventing data.

1. **Marketplace cannot be verified from repository data.** The campaign register in
   `context/campaign-list.md` is unpopulated and its Marketplace field requirement is
   `[VERIFY]`, so marketplace reaches a skill only from the request. Test 1 gates a
   value this repository cannot independently confirm. `[VERIFY]`
2. **Phase 1b not implemented.** Only the two skills named above consume this file.
   Every other skill remains unintegrated. `[VERIFY]`
3. **Phase 2 not implemented.** The four rule-family files have not been migrated,
   split, renamed or moved, and remain at their existing paths. `[VERIFY]`
4. **Migration precondition (b) remains OPEN.** Nothing in this file changes it.
   `[VERIFY]`
5. **Reviewer role undefined** repository-wide —
   `validation/REPOSITORY_GAP_REGISTER.md` → GAP-G01. None assigned. `[VERIFY]`

---

## Queryability Test

Using only this document and the sources it references by path, can another LLM
answer:

| Question | Answerable? | Answer / Where |
|----------|-------------|----------------|
| What owns operational marketplace routing? | Yes | **This file** — Metadata; What This File Owns |
| Which marketplaces are authorised for Phase 1 routing? | Yes | **UK, DE, FR, IT** — Authorised Marketplaces |
| Is US authorised? | Yes | **No — explicitly excluded** |
| Is CA authorised? | Yes | **No — outside scope by omission** |
| Are NL/ES authorised because content exists? | Yes | **No** — content existence never grants authorisation |
| What happens if marketplace is missing? | Yes | **No route, never UK** — Outcomes |
| What happens if marketplace is ambiguous? | Yes | **No route, never UK** — Outcomes |
| Is UK ever the default? | Yes | **No** — No default marketplace |
| Does routing authorisation prove content exists? | Yes | **No** — The Two-Test Model |
| Does content existence prove routing authorisation? | Yes | **No** — The Two-Test Model |
| Which file owns Hour Budget rule content? | Yes | `context/hour-budget-rules.md` — Test 2 table |
| Which file owns Product Pause rule content? | Yes | `context/product-pause-rules.md` — Test 2 table |
| Does this file contain PPC business-rule values? | Yes | **No** — Duplicate Truth Prevention |
| Which skills consume this file? | Yes | `hour-budget-check`, `product-pause-check` — How a Consuming Skill Uses This File |
| Is Phase 1b implemented? | Yes | **No** — Known Limitations 2 |
| Is Phase 2 implemented? | Yes | **No** — Known Limitations 3 |

**Result: PASS**

---

## Ownership and Status

- **Owner:** Jathukulan
- **Reviewer:** `[VERIFY]` — none defined repository-wide (GAP-G01)
- **Status:** Active
- **Authoritative for:** marketplace routing authorisation (Test 1) only
- **Phase 1b Implemented:** NO
- **Phase 2 Implemented:** NO
- **Rule-family files migrated:** NO
