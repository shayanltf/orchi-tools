# Claude Runtime

Claude Code installs Apple Skills through the `orchi-tools` marketplace. Plugin name is `apple-skills`; individual skills keep purpose-scoped names.

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install apple-skills@orchi-tools
```

Skills live in root `skills/` per Claude plugin structure. Invoke as `/apple-skills:<skill-name>`.

For maintainer validation from a checkout:

```bash
claude --plugin-dir .
```
