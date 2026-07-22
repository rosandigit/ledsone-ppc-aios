# LEDSone PPC AIOS

## Purpose

This repository is the documentation and operating-knowledge base for LEDSone
Amazon PPC work. It stores documentation, reusable AI context, evidence and
decisions.

It does **not** connect to Amazon Ads. It does **not** automate Amazon PPC.
It produces documentation and DRAFT recommendations only.

## Repository layout

| Folder | Contents |
|--------|----------|
| `context/` | Reusable AI context and the authoritative rule files |
| `skills/` | Definitions of the repeatable PPC checks the AI can run |
| `intelligence-inbox/` | Raw inputs awaiting triage, then moved to `processed/` |
| `campaigns/` | Campaign documentation by lifecycle: active, paused, archived |
| `reports/` | Weekly and monthly report drafts, plus a record of what was sent |
| `keywords/` | Master negatives, proven exact-match library, expansion candidates |
| `evidence/` | Source data and exports that recommendations are based on |
| `decisions/` | Decisions taken, approvals given, and rollbacks |
| `validation/` | Checks that repository content is accurate and current |
| `handover/` | What another person or LLM needs to continue this work |
| `github-prompts/` | Prompts used to operate this repository |

Every folder has a `README.md` stating its purpose, what belongs in it, what
does not, its owner and its status.

## AI workflow

1. Read the relevant files in `context/` before anything else.
2. Read the evidence in `evidence/` that applies to the question.
3. Run the relevant skill from `skills/`.
4. Produce a **DRAFT** recommendation with the calculation or reasoning shown.
5. Jathukulan reviews it.
6. If approved, Jathukulan applies the change manually in Amazon Ads and logs
   it in `decisions/`.

## Evidence-first philosophy

No recommendation is made without evidence behind it. Every draft references
the evidence it was derived from, including the source, the date and the date
range. Anything not yet documented from a verified source is marked
`[VERIFY]` rather than guessed at.

## Human approval requirement

Every recommendation involving bids, budgets, keywords, campaigns or targeting
requires human approval before implementation. The AI never approves its own
output.

## Draft recommendation policy

All skill output is a draft. Drafts show the calculation or reasoning so a
human can check the working. A draft is not an instruction and is not
authorisation to act.

## No Amazon Ads automation

This repository never changes anything in Amazon Ads and holds no credentials
or API access. There is no automatic undo in Amazon Ads — rollbacks are done
manually via Change History and logged in `decisions/`.

If a request implies automating Amazon Ads changes, the correct response is to
**STOP** and flag it.

## Owner

Jathukulan

## Status

Active
