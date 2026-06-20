# Codex Workflows

Use when migrating command workflows into Codex.

## Surface Map

- Codex slash commands are built-in; do not port Claude command Markdown as if custom slash commands run.
- Reusable user workflows become skills.
- Name migrated workflows `orchestrate-<name>`.
- Mention legacy trigger in skill description so natural-language routing still works.
- Use `$skill-name` for explicit invocation.

## Runtime Translation

- User gates become concise chat questions or structured choices.
- Companion skills are invoked in parent Codex session.
- Subagent dispatch becomes Codex custom-subagent work by name.
- If persistent teammate threads are absent, keep role boundary and execute scoped fan-out.
- Task tracking becomes visible plan/checklist when available.
- File work uses normal inspect/edit flow; manual patches use `apply_patch`.
- Shell work uses Codex shell execution.
- Runtime-context checks are explicit file reads or shell commands.

## Review Contract

- Planning and implementation workflows run AFK by default once approved.
- Hold human interaction for end HITL review unless user asks otherwise.
- Plans can mark orchestrator-only work with `//TODO -> Orchestrator task: ...`.
- Orchestrator completes marked work before next phase.
- Change-making workflows report tests run, gaps, and review handoff.
