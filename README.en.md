# Human Control Layer Skill

[简体中文](README.md)

Human Control Layer compresses the **current** project into three short documents for an owner who does not read source code. In five to ten minutes, the owner should be able to understand what the system is, how its main parts work together, where the project stands, its key risks, and why its current architecture exists.

## When to use it

Create or refresh the snapshot when the user explicitly asks, a meaningful phase is completed, or the old snapshot would materially mislead the owner. Ordinary bugs, small features, individual commits, and routine task completion do not automatically trigger it. A separate [Human Diff](https://github.com/jbwu091-jdbsh/human-diff) handles decisions before major changes.

## Install in Codex

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo jbwu091-jdbsh/human-control-layer --path . --name human-control-layer
```

Start a new conversation after installation, or explicitly ask to use `human-control-layer` for a project snapshot. Other Agent/Harness environments can read `SKILL.md` and the templates as plain Markdown; no Codex API is required.

## Project output

```text
docs/human/
├── HCL-PROJECT_MAP.md       # product boundary, modules, data flow
├── HCL-CURRENT_STATE.md     # phase, progress, risks, next step
├── HCL-DECISIONS.md         # still-active decisions
└── archive/                 # create only when retired history must be kept
```

For a new project, fill the three files from actual evidence using [`templates/`](templates/). On later updates, edit only the files that became stale; remove or archive obsolete material instead of appending a task log. Suggested lengths are roughly 1500–2500, 800–1500, and 2000–3000 Chinese characters, respectively.

## Files

- `SKILL.md`: triggers, evidence, update, and compression rules.
- `templates/`: three project document templates with `HCL-` prefixes.
- `README.md` / `README.en.md`: Chinese and English guides.

Version 0.1 uses Markdown only. It needs no scripts, database, hooks, or vendor-specific harness features.
