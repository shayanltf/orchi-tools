# Claude Runtime

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

Claude Code reads its plugin from the `claude/` subdirectory:

- `claude/.claude-plugin/plugin.json` - Claude plugin manifest (`apple`).
- `claude/skills/<skill>/SKILL.md` - grouped Claude skills, each with its own `references/`.

The marketplace entry uses a `git-subdir` source pointing at `claude/`, so the Claude plugin root is `claude/` and Claude loads only `claude/skills/`. Root `skills/` belongs to the Codex plugin and is never loaded by Claude.

For maintainer validation from a checkout:

```bash
claude --plugin-dir ./claude
```
