# Plugin Packaging

Use when changing plugin structure.

- Plugin name: `apple-skills`.
- Display name: `Apple Skills`.
- Root manifests: `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`.
- Install manifests: `.claude-plugin/marketplace.json`, `.agents/plugins/marketplace.json`.
- Public install commands omit version refs; harnesses track marketplace updates from the repository source.
- Marketplace plugin source entries omit `ref` and `sha`.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Skills live at root `skills/<skill>/SKILL.md`.
- Skill support files stay with each skill: `references/`, `scripts/`, `agents/openai.yaml`.
- Codex MCP servers live in `.mcp.json`; `.codex-plugin/plugin.json` points at it with `mcpServers`.
- macOS helper commands live in root `commands/`.
- Claude components stay at plugin root, not inside `.claude-plugin/`.
- Claude install path: marketplace add -> plugin install -> `/apple-skills:<skill>`.
- Codex install path: add marketplace -> install/enable `Apple Skills` in Codex plugin directory.
- Keep Claude and Codex runtime notes in `claude/` and `codex/`.
- Do not create `CLAUDE.md` or `CODEX.md`.
- Do not prefix skill names with `apple-skills`.
- Version stays `0.1.0` until next release.
