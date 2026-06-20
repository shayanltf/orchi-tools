# Claude Skills

Use when authoring or reviewing Claude Code skills inside or outside plugins.

## Shape

- Skill = `SKILL.md` plus optional `references/`, `scripts/`, `assets/`.
- Plugin skill path = `<plugin>/skills/<name>/SKILL.md`.
- Plugin root `SKILL.md` works for one-skill plugins; `skills/` is better for growth.
- Frontmatter: put trigger words first in `description`.
- Use `when_to_use` only when description needs extra routing context.
- Use `disable-model-invocation: true` for manual-only workflows.
- Use `user-invocable: false` for background knowledge users should not call.
- Keep body concise; once loaded, every line stays in context.

## Body

- State what to do. No motivation essay.
- Put fragile/deterministic operations in scripts.
- Put long examples, schemas, and reference tables in supporting files.
- Reference supporting files by name and trigger condition.
- Use dynamic context only where Claude skill runtime supports it.

## Plugin Behavior

- Plugin skills invoke as `/plugin-name:skill-name`.
- Directory name sets invocation name under `skills/`.
- Skill frontmatter `name` controls invocation only for plugin-root `SKILL.md`.
- Do not put `skills/`, `agents/`, `commands/`, or `hooks/` inside `.claude-plugin/`.
- Root plugin `CLAUDE.md` is not loaded; ship runtime instructions as skills or agents.
