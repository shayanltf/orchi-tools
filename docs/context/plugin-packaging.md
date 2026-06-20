# Plugin Packaging

Use when changing plugin structure.

- Plugin name: `apple`.
- Display name: `Apple`.
- Skills group by purpose: `swiftui`, `ios`, `macos`, `build`, `performance`.
- Keep each runtime in its own plugin tree; do not share one skill tree.

## Codex

- Plugin root: `codex/apple/`.
- Plugin manifest: `codex/apple/.codex-plugin/plugin.json`.
- Marketplace catalog: `.agents/plugins/marketplace.json`; point the `apple` entry at `./codex/apple`.
- Skills: `codex/apple/skills/<group>/SKILL.md`.
- MCP config: `codex/apple/.mcp.json`.
- Assets: `codex/apple/assets/`.
- Add `agents/openai.yaml` only to Codex skills when the Codex card needs runtime metadata.
- Install through the Codex marketplace flow; do not make cloning the primary user path.

## Claude

- Plugin root: `claude/`.
- Plugin manifest: `claude/.claude-plugin/plugin.json`.
- Marketplace catalog: `.claude-plugin/marketplace.json`.
- Marketplace source: use `git-subdir` with `path: claude` so Claude loads only `claude/`.
- Skills: `claude/skills/<group>/SKILL.md`.
- Keep Claude skills free of Codex-only files such as `agents/openai.yaml`.
- Install with `claude plugin marketplace add` and `claude plugin install apple@orchi-tools`.

## Both

- Treat `SKILL.md` as the active skill: frontmatter (`name`, `description`) plus working body.
- Merge source guidance into the grouped skill structure without changing meaning.
- Do not create archived source wrappers such as `source.md`.
- Use purpose-named references and scripts inside each runtime skill when progressive disclosure is needed.
- Duplicate content across Codex and Claude when both runtimes need the same guidance.
- Keep runtime manifests, marketplace source entries, assets, commands, MCP config, and agent metadata scoped to that runtime.
- Do not prefix skill names with the plugin name.
- Public install commands and marketplace sources omit version refs.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Put reusable future guidance in `WORKFLOW.md` and `docs/context/`, not in issue comments.
- Keep repo guidance in `CLAUDE.md`; keep `AGENTS.md` as a pointer to `CLAUDE.md`.
- Do not create `CODEX.md`.
- Keep version `0.1.0` until the next release.
