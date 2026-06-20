# Claude Commands

Use when converting or reviewing Claude command-shaped workflows.

## Contract

- Command = stored ordered prompt.
- Skill = reusable knowledge or procedure.
- If command body becomes a knowledge dump, extract skill.
- Use `skills/` for new work; legacy `.claude/commands/*.md` still works.
- Frontmatter stays declarative: `description`, `allowed-tools`, `argument-hint`, `model`, `context`.
- Body uses ordered steps. One action per step.
- No closing summary boilerplate; runtime reports status.

## Runtime Context

- Bash injection belongs in command/skill surfaces that support it, not agent bodies.
- Static file imports use supported `@path` placement only.
- Fresh state comes from commands run at invocation time.
- Stable reference content belongs in a linked file.

## Migration

- Preserve gates, branches, review points, and verification.
- Replace custom command assumptions with skill invocation when packaging for plugins.
- Keep task context in the parent; pass only scoped handoff to subagents.
- HITL review happens once at end unless user explicitly asks for checkpoints.
