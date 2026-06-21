# Apple Claude Runtime

Claude Code installs the `apple` plugin through the `orchi-tools` marketplace.

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install apple@orchi-tools
```

Invoke the grouped skills through the plugin namespace:

```text
/apple:swiftui
/apple:ios
/apple:macos
/apple:build
/apple:performance
```

## Layout

Claude Code reads this plugin from the `plugins/apple/claude/` subdirectory:

- `plugins/apple/claude/.claude-plugin/plugin.json` - Claude plugin manifest (`apple`).
- `plugins/apple/claude/skills/<skill>/SKILL.md` - grouped Claude skills, each with its own `references/`.

The marketplace entry uses a `git-subdir` source pointing at `plugins/apple/claude/`, so Claude loads only `plugins/apple/claude/skills/`. Codex-only `agents/openai.yaml` files are omitted from this runtime.

For maintainer validation from a checkout:

```bash
claude --plugin-dir ./plugins/apple/claude
```
