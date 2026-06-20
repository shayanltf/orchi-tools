# Codex Runtime

Codex loads this repository through its local plugin flow. The manifest is `.codex-plugin/plugin.json` and points at the validator-compatible default skill directory:

```text
skills/
```

The runtime skill is:

```text
apple-one-context
```

The skill points to `docs/INDEX.md`, then loads only the context leaves relevant to the task.
