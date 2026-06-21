# Plugin Packaging

Use when changing plugin structure.

- Active plugin name: `apple`. Display name: `Apple`.
- Reserved plugin name: `web`. The Codex catalog may list it as `NOT_AVAILABLE` while its source repo is absent.
- Apple skills group by purpose: `swiftui`, `ios`, `macos`, `build`, `performance`.
- Each runtime keeps skills in its own folder; do not share one skill tree.

## Codex

- Plugin manifest: `.codex-plugin/plugin.json` (`skills: ./skills/`, `mcpServers: ./.mcp.json`).
- Marketplace catalog: `.agents/plugins/marketplace.json`.
- Skills at root `skills/<group>/SKILL.md`; the Codex validator requires root `skills/`.
- Each Codex skill ships `agents/openai.yaml` for the Codex card. Add `icon_small`/`icon_large`/`brand_color`/`policy` only when icon assets exist.
- MCP servers in `.mcp.json`; macOS helper commands in root `commands/`.
- Install: marketplace add -> install/enable `Apple` in the Codex plugin directory.
- `web` is catalog-only here: `.agents/plugins/marketplace.json` points to the planned `https://github.com/shayanltf/orchi-web-tools.git` source with `policy.installation: NOT_AVAILABLE`. Do not copy web skills into this repository or mark `web` available until that source repo exists and validates.

## Claude

- Plugin manifest: `claude/.claude-plugin/plugin.json`. Marketplace catalog: `.claude-plugin/marketplace.json`.
- The marketplace entry uses a `git-subdir` source with `path: claude`, so the plugin root is `claude/` and Claude loads only `claude/skills/`, never root `skills/`.
- Skills at `claude/skills/<group>/SKILL.md` with supporting files under each skill's `references/`. No `agents/openai.yaml` on the Claude side.
- Install: `claude plugin marketplace add` -> `claude plugin install apple@orchi-tools` -> `/apple:<group>`.
- Do not add a Claude `web` entry here until the planned `orchi-web-tools` repo contains a `claude/` plugin root. This catalog has no disabled-install policy equivalent for missing Claude sources.

## Both

- `SKILL.md` is the skill, not an index: frontmatter (`name`, `description`) plus working body.
- Preserve imported source content under `references/modules/<module>/source.md`; merge, do not rewrite.
- Do not prefix skill names with the plugin name.
- Public install commands and marketplace sources omit version refs.
- Repo guidance lives in `CLAUDE.md`; `AGENTS.md` references `CLAUDE.md`. Do not create `CODEX.md`.
- Version stays `0.1.0` until the next release.
