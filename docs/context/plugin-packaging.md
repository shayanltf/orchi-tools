# Plugin Packaging

Use when changing plugin structure.

- Plugin name: `apple-skills`.
- Display name: `Apple Skills`.
- Root manifests: `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`.
- Skills live at root `skills/<skill>/SKILL.md`.
- Claude: components must stay at plugin root, not inside `.claude-plugin/`.
- Codex: skill directory needs `SKILL.md`; optional `references/`, `scripts/`, `assets/`, `agents/openai.yaml`.
- Keep Claude and Codex runtime notes in `claude/` and `codex/`.
- Do not create `CLAUDE.md` or `CODEX.md`.
- Do not prefix skill names with `apple-skills`.
- Version stays `0.1.0` until next release.
