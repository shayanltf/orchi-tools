# Claude Runtime

Claude Code loads this repository as a plugin from the repo root.

```bash
claude --plugin-dir .
```

The runtime skill lives at `claude/skills/apple-one-context/SKILL.md` and is exposed as:

```text
/apple-one-skills:apple-one-context
```

The skill points to `docs/INDEX.md`, then loads only the context leaves relevant to the task.
