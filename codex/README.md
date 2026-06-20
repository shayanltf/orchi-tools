# Codex Runtime

Codex loads this repository through its local plugin flow. Plugin name is `apple-skills`; individual skills keep purpose-scoped names.

The manifest is `.codex-plugin/plugin.json` and points at the validator-compatible default skill directory:

```text
skills/
```

Codex can invoke installed skills explicitly with `$<skill-name>` or choose them implicitly from each skill description.
