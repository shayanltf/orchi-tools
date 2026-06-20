# Codex Runtime

Codex installs Apple Skills through the `orchi-tools` marketplace. Plugin name is `apple-skills`; individual skills keep purpose-scoped names.

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Then install or enable `Apple Skills` from the Codex app plugin directory under `Orchi Tools`.

The manifest is `.codex-plugin/plugin.json` and points at the validator-compatible default skill directory:

```text
skills/
```

Codex can invoke installed skills explicitly with `$<skill-name>` or choose them implicitly from each skill description.
