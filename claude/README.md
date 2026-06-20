# Claude Runtime

Claude Code installs Apple Skills through the `orchi-tools` marketplace. Plugin name is `apple-skills`; individual skills keep purpose-scoped names.

```bash
claude plugin marketplace add shayanltf/orchi-tools@v0.1.0
claude plugin install apple-skills@orchi-tools
```

Skills live in root `skills/` per Claude plugin structure. Invoke as `/apple-skills:<skill-name>`.

Maintainer-only smoke test from a checkout:

```bash
claude --plugin-dir .
```
