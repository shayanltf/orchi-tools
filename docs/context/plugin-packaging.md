# Plugin Packaging

Use when changing plugin structure.

- `orchi-tools` is the marketplace repository.
- Active plugin roots:
  - `plugins/apple` - display name `Apple`.
  - `plugins/web` - display name `Web`.
- Each plugin owns its own work under `plugins/<plugin-name>/`.
- Each runtime keeps skills in its own folder; do not share one skill tree.

## Codex

- Marketplace catalog: `.agents/plugins/marketplace.json`.
- Marketplace entry source paths:
  - `apple` -> `./plugins/apple`
  - `web` -> `./plugins/web`
- Plugin manifest: `plugins/<plugin-name>/.codex-plugin/plugin.json`.
- Codex skills: `plugins/<plugin-name>/skills/<skill>/SKILL.md`.
- Codex runtime metadata may include `agents/openai.yaml` inside each Codex skill.
- Apple MCP servers live in `plugins/apple/.mcp.json`; Apple macOS helper commands live in `plugins/apple/commands/`.
- Install: marketplace add -> install or enable `Apple` or `Web` in the Codex plugin directory.

## Claude

- Marketplace catalog: `.claude-plugin/marketplace.json`.
- Marketplace entry source paths:
  - `apple` -> `plugins/apple/claude`
  - `web` -> `plugins/web/claude`
- Plugin manifest: `plugins/<plugin-name>/claude/.claude-plugin/plugin.json`.
- Claude skills: `plugins/<plugin-name>/claude/skills/<skill>/SKILL.md`.
- No `agents/openai.yaml` files belong in Claude skill trees.
- Install: `claude plugin marketplace add` -> `claude plugin install <plugin-name>@orchi-tools` -> invoke `/<plugin-name>:<skill>`.

## Plugin Notes

- Apple groups approved OpenAI iOS and macOS source skills into `swiftui`, `ios`, `macos`, `build`, and `performance`.
- Web preserves four approved OpenAI Build Web Apps source skill directories as separate skills: `frontend-app-builder`, `frontend-testing-debugging`, `react-best-practices`, and `shadcn-best-practices`.
- Web does not copy Stripe, Supabase/Postgres, or web data visualization source content.

## Both

- `SKILL.md` is the skill, not an index: frontmatter (`name`, `description`) plus working body.
- Preserve imported source content according to the plugin's import mode.
- Do not prefix skill names with the plugin name.
- Public install commands and marketplace sources omit version refs.
- Repo guidance lives in `CLAUDE.md`; `AGENTS.md` references `CLAUDE.md`. Do not create `CODEX.md`.
- Version stays `0.1.0` until the next release.
