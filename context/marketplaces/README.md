# Marketplace Constitution

Operational standard for marketplace knowledge in the LEDSone PPC AIOS.

---

## 1. Purpose

This directory contains marketplace-specific operational knowledge for LEDSone
Amazon PPC.

Every marketplace follows the same governance model. Every marketplace remains
operationally independent.

The governance model is shared. The operational content is not.

---

## 2. AIOS Philosophy

- The AIOS is the company's operational brain.
- Daily work improves the AIOS.
- Daily work does not build the AIOS.

---

## 3. Marketplace Independence Principle

Each marketplace is an independent operational knowledge domain.

Rules are never assumed to transfer automatically between marketplaces.

Intentional duplication is acceptable ONLY through the Knowledge Transfer Gate
(Section 5).

A rule from one marketplace may become another marketplace's rule only when:

- evidence verifies it is the approved rule for that marketplace, AND
- the Repository Owner approves that transfer.

Copying one marketplace's operational content into another marketplace without
passing through the Knowledge Transfer Gate is prohibited.

---

## 4. Knowledge States

A marketplace's operational knowledge exists in exactly two states.

### A. Approved Knowledge

Operational knowledge that has been traced to an identified source, verified
against evidence, approved by the Repository Owner, and recorded inside the
AIOS.

Approved Knowledge may be relied on for operational analysis.

### B. Approved Gap

A formally recorded statement that no approved operational knowledge exists for
a given rule in a given marketplace.

Approved Gap means the absence of approved operational knowledge has itself been
verified and formally recorded.

An Approved Gap is approved documentation about missing evidence.

It is NOT:

- placeholder rule content
- incomplete documentation
- draft operational guidance
- temporary notes
- operational instruction

### Boundary

No operational statement may exist outside these two states.

Never use:

- guessed knowledge
- inferred rules
- copied marketplace rules
- AI-generated operational rules
- estimated thresholds
- assumed marketplace behaviour

---

## 5. Knowledge Transfer Gate

Operational knowledge originates outside the AIOS and enters it through a single
controlled gate.

Possible external sources include:

- Configurator PDFs
- BGCT
- SOP
- Vendor Central documentation
- Approved Decision Records
- Claude Project
- Company-approved operational documentation

Knowledge enters AIOS only after:

1. Source identified
2. Evidence verified
3. Repository Owner approval
4. Recorded inside AIOS

After entry, AIOS becomes the operational source of truth.

### What Knowledge Transfer is not

Knowledge Transfer is approval of DOCUMENTATION.

It is NOT:

- marketplace automation
- Amazon Ads execution
- campaign modification
- bid change
- budget change
- pause action

Knowledge Transfer therefore does NOT invoke the Roshanthan / Satheesvaran
authorization gate. That authorization gate governs live marketplace automation
only.

---

## 6. Marketplace Structure Standard

Every marketplace occupies its own directory and follows the same directory
layout.

Illustration only:

```
context/marketplaces/
    UK/
    DE/
    FR/
    IT/
    ES/
```

The presence of a marketplace directory records where its operational knowledge
lives. It grants no routing authorisation and no operational permission.

---

## 7. Rule Structure Standard

A rule directory takes one of two layouts, determined by its knowledge state.

### Approved Knowledge layout

```
<rule>/
    README.md
    rule.md
    thresholds.md
    examples.md
    evidence.md
    validation.md
    history.md
```

### Approved Gap layout

```
<rule>/
    GAP.md
```

Only `GAP.md` exists until approved evidence exists.

An evidence-first repository never creates empty:

- thresholds
- examples
- evidence
- validation
- history

files for knowledge it does not yet possess.

### Required GAP.md fields

Every `GAP.md` MUST contain EXACTLY these fields, in this exact order:

```
Status
Current State
Evidence
Owner
Next Action
```

`Status` MUST be:

```
OPEN [VERIFY]
```

A `GAP.md` contains NO operational rule, NO threshold, NO instruction, NO
recommendation, and nothing that could be mistaken for Approved Knowledge.

---

## 8. Marketplace Launch State

| Marketplace | Launch state |
| --- | --- |
| UK | Approved Knowledge — populate from approved sources. |
| DE | Approved Gaps until approved evidence exists. |
| FR | Approved Gaps until approved evidence exists. |
| IT | Approved Gaps until approved evidence exists. |
| ES | Approved Gaps until approved evidence exists. |

DE, FR and IT already have partial approved source material identified (e.g.
configurator material and previous validation work).

ES currently has NO identified approved operational source. All ES operational
knowledge therefore begins as Approved Gap.

US is not included. Current governance excludes US.

---

## 9. Migration Rule

Creating new marketplace folders and this README is additive and safe.

Moving, renaming or relocating existing committed files is a controlled
migration.

Controlled migration requires:

- path impact review
- reference verification
- coordinated update
- one controlled change

---

## 10. Daily Operational Workflow

```
Receive work
    ↓
Open marketplace
    ↓
Locate rule
    ↓
Review evidence
    ↓
Perform analysis
    ↓
Record findings
    ↓
Update Approved Knowledge  or  Approved Gap
```

---

## 11. Scope Boundary

This document defines ONLY marketplace operational standards.

It does NOT:

- define PPC thresholds
- define business rules
- authorize marketplace rule changes
- constitute a Knowledge Transfer

Outputs DRAFT recommendations only.

Never applies Amazon Ads changes.

Human approval required before implementation.

If automation is implied, STOP and flag it.

---

## 12. Repository Evolution

The marketplace architecture is intentionally stable.

Knowledge evolves continuously.

Repository structure changes only when justified by demonstrated operational
need.

Marketplace knowledge evolves through evidence.

Architecture does not evolve through speculation.

---

## 13. Queryability

Using only this document, another LLM can answer:

- **What is a marketplace?** An independent operational knowledge domain with
  its own directory, governed by the shared model in this document (Sections 1,
  3, 6).
- **How is marketplace knowledge organised?** One directory per marketplace, one
  directory per rule, in one of the two layouts in Section 7.
- **What is Approved Knowledge?** Section 4A.
- **What is Approved Gap?** Section 4B.
- **How does knowledge enter AIOS?** Through the four-step Knowledge Transfer
  Gate in Section 5.
- **What must every GAP.md contain?** The five fields in Section 7, in order,
  with `Status` set to `OPEN [VERIFY]`.
- **What is each marketplace's launch state?** Section 8.
- **How should marketplaces evolve?** Section 12 — knowledge through evidence,
  architecture only on demonstrated need.
