# Web Claude Runtime

Claude Code installs the `web` plugin through the `orchi-tools` marketplace.

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install web@orchi-tools
```

Invoke the scoped skills through the plugin namespace:

```text
/web:frontend-app-builder
/web:frontend-testing-debugging
/web:react-best-practices
/web:shadcn
```

## Layout

Claude Code reads this plugin from the `plugins/web/claude/` subdirectory:

- `plugins/web/claude/.claude-plugin/plugin.json` - Claude plugin manifest (`web`).
- `plugins/web/claude/skills/<skill>/SKILL.md` - copied Claude skills, each with its own supporting files.

The marketplace entry uses a `git-subdir` source pointing at `plugins/web/claude/`, so Claude loads only `plugins/web/claude/skills/`. Codex-only `agents/openai.yaml` files are omitted from this runtime.
