# Plugin Packaging

Use when changing plugin structure.

- Plugin name: `apple-skills`.
- Display name: `Apple Skills`.
- Root manifests: `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`.
- Install manifests: `.claude-plugin/marketplace.json`, `.agents/plugins/marketplace.json`.
- Public install commands omit version refs; harnesses track marketplace updates from the repository source.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Skills live at root `skills/<skill>/SKILL.md`.
- Claude: components must stay at plugin root, not inside `.claude-plugin/`.
- Claude install path: marketplace add -> plugin install -> `/apple-skills:<skill>`.
- Codex: skill directory needs `SKILL.md`; optional `references/`, `scripts/`, `assets/`.
- Every skill ships `agents/openai.yaml` so it renders consistently in the Codex plugin directory. Claude ignores this file; Codex reads it for the skill card and invocation policy. Add `icon_small`/`icon_large`/`brand_color`/`policy` only when the source ships icon assets.
- Codex install path: add marketplace -> install/enable `Apple Skills` in Codex plugin directory.
- Keep Claude and Codex runtime notes in `claude/` and `codex/`.
- Do not create `CLAUDE.md` or `CODEX.md`.
- Do not prefix skill names with `apple-skills`.
- Version stays `0.1.0` until next release.
