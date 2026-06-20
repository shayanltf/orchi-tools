# Claude Runtime

Claude Code loads this repository as a plugin from the repo root. Plugin name is `apple-skills`; individual skills keep purpose-scoped names.

```bash
claude --plugin-dir .
```

Skills live in root `skills/` per Claude plugin structure. Invoke as `/apple-skills:<skill-name>`.
