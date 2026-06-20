# Apple One Skills

Apple One Skills is a compact open source context plugin for Apple-platform agent work across Claude Code and Codex.

Maintained by Shayan Latif, with source published from `shayanltf/orchi-tools`.

## What It Contains

- `docs/INDEX.md` - root context map with one leaf line per file.
- `docs/context/` - compressed agent context for Apple skill research, Claude Code plugin surfaces, Codex plugin surfaces, docs output, voice, and privacy checks.
- `claude/` - Claude Code skill entry point and runtime notes.
- `codex/` - Codex skill entry point and runtime notes.
- `.claude-plugin/plugin.json` - Claude Code plugin manifest.
- `.codex-plugin/plugin.json` - Codex plugin manifest.

## Use

Claude Code can load this repository as a local plugin:

```bash
claude --plugin-dir .
```

Invoke the context skill as:

```text
/apple-one-skills:apple-one-context
```

Codex can load the same repository through its local plugin flow. The Codex manifest points at `skills/`, and the runtime skill is `apple-one-context`.

## Release

Initial release: `v0.1.0`.
