# Codex Skills

Use when authoring or porting Codex skills.

## Shape

- Skill directory contains `SKILL.md`.
- Optional folders: `scripts/`, `references/`, `assets/`, `agents/openai.yaml`.
- Codex sees name, description, path first; full body loads only when selected.
- `SKILL.md` frontmatter needs `name` and `description`.
- Extra metadata can stay for repo continuity: `version`, `author`, `license`.
- Description front-loads trigger words and boundaries.

## Body

- Keep instructions focused and imperative.
- Move long examples and schemas into `references/`.
- Move deterministic or fragile steps into `scripts/`.
- Manual code edits use `apply_patch`.
- Shell work uses normal Codex shell execution.
- Research uses a research protocol plus official docs and source links.

## Porting From Claude

- User gates become concise chat questions or structured choice UI.
- Task tracking becomes Codex plan/checklist when available.
- Agent/team calls become named Codex subagents or scoped fan-out.
- File read/write/edit tool names become natural file-work instructions.
- Preserve approvals, verification, handoff, and review even when vocabulary changes.
- Never copy `credentials.md`; credentials stay local and gitignored.
