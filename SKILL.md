---
name: human-control-layer
description: Create or refresh a short, evidence-based current project snapshot for a nontechnical owner at an explicit request or meaningful milestone. Maintain the project map, current state, and active decisions; skip ordinary task-by-task updates and change-approval briefs.
---

# Human Control Layer

Keep a small set of current-state documents that lets a project owner understand what the system is, how its main parts work together, where the project stands, the main risks, and why its current architecture exists. This is a human-readable snapshot, not a changelog, task log, technical specification, approval system, or machine project state.

## When to update

Initialize or refresh when the user asks for a project snapshot or Human Control Layer, a meaningful phase or core subsystem becomes usable, the product boundary or core data flow changes, or the existing snapshot would materially mislead the owner. A structural change by itself does not force an immediate update; assess whether it changes the overall current picture.

Skip ordinary bugs, small features, local refactors, UI edits, tests, single commits or Sprints, and routine task completion unless the user explicitly requests a refresh. Do not make HCL a mandatory task-end artifact. When asked only to check drift, compare the documents with current evidence and report whether an update is needed before writing.

## Ground the snapshot

Read the current project files, relevant runtime or test evidence, accepted decisions, and existing HCL documents. Distinguish implemented, verified, in progress, blocked, and planned states. Do not turn plans, old documents, or a successful build into proof of working product behavior. Preserve existing project conventions and the user's write authorization.

For a new file-based project, use `docs/human/` and initialize only these three files, adapting the [templates](templates/) to actual evidence:

- `HCL-PROJECT_MAP.md`: one-sentence definition, product boundary, core modules and responsibilities, their relationships and main data flow, key external dependencies, important code locations, and current architecture constraints. Update only when the system map materially changes.
- `HCL-CURRENT_STATE.md`: current phase, completed and ongoing capabilities, main risks or blockers, next step, and explicit non-goals. Keep only facts that remain current.
- `HCL-DECISIONS.md`: the few important decisions that still constrain the present architecture, with reason, long-term effect, and guardrails. Keep `Active` in the main file; move `Superseded` or `Retired` decisions to `docs/human/archive/decisions/` when history must be kept.

Every HCL document created by this skill uses the `HCL-` filename prefix. Never overwrite a similarly named unprefixed project document. Refer to or migrate relevant content only when needed and authorized. Existing HCL files can be updated individually; do not rewrite all three merely to keep timestamps aligned.

## Keep it short and readable

Default to the project's language, using Simplified Chinese if unspecified. Explain business behavior before code names; include paths only as traceable evidence. Prefer a simple arrow flow when it clarifies module relationships. Suggested maximums are about 1500–2500 Chinese characters for Project Map, 800–1500 for Current State, and 2000–3000 for Decisions. The three files together should take roughly 5–10 minutes to read.

When nearing a limit, remove stale material, merge duplicates, replace implementation detail with a business explanation, and archive history that still matters. Do not add more core files to evade compression. Record uncertainty clearly when evidence is incomplete.

## Relationship to Human Diff

Human Diff is a separate, pre-change decision brief. HCL describes the current system after a meaningful milestone or an explicit request. Neither skill automatically triggers the other. Do not use HCL to imply that an undecided structural proposal was approved.

Before finishing, confirm that each edited statement describes the present system, the current state reads as a snapshot rather than a diary, only active decisions remain in the main decisions file, and a nonprogrammer can understand the result.
