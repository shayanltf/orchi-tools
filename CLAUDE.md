# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What This Repo Is

This repository publishes the `orchi-tools` marketplace. The marketplace offers multiple scoped plugins, and each plugin owns its own root under `plugins/<plugin-name>/`.

Current plugin roots:

- `plugins/apple/` - Apple ecosystem skills for Codex and Claude Code.
- `plugins/web/` - Frontend web skills for Codex and Claude Code.

Do not treat the repository root as a plugin root. The root contains marketplace catalogs, docs, research, and release coordination.

## Claude Plugin Structure

- `.claude-plugin/marketplace.json` is the Claude marketplace catalog.
- Each Claude plugin root is `plugins/<plugin-name>/claude/`.
- Each Claude plugin manifest is `plugins/<plugin-name>/claude/.claude-plugin/plugin.json`.
- Each Claude skill tree is `plugins/<plugin-name>/claude/skills/`.
- Marketplace entries use `git-subdir` sources:
  - `apple` -> `plugins/apple/claude`
  - `web` -> `plugins/web/claude`

Because each Claude plugin root is its own `claude/` subdirectory, Claude loads only that plugin's Claude skill tree. Codex skill trees under `plugins/<plugin-name>/skills/` are not Claude inputs.

## Authoring Skills

- `SKILL.md` is the skill itself, not an index. Its YAML frontmatter (`name`, `description`) decides when Claude loads the skill; its body is the working instructions.
- Keep imported source content intact according to the plugin's import mode:
  - Apple uses grouped purpose skills: `swiftui`, `ios`, `macos`, `build`, and `performance`.
  - Web preserves the four approved OpenAI source skill surfaces as distinct copied skill directories.
- Reference supporting files from `SKILL.md` so Claude knows what each one holds and when to load it.
- Do not add Codex-only files (`agents/openai.yaml`) to Claude skill trees.
- Do not prefix skill folder names with the plugin name.

## Validation

Validate a Claude plugin from a checkout with its scoped plugin directory:

```bash
claude --plugin-dir ./plugins/apple/claude
claude --plugin-dir ./plugins/web/claude
```

Confirm each `plugins/<plugin-name>/claude/skills/<skill>/SKILL.md` has valid frontmatter and that every path it references resolves inside that skill folder.

## Conventions

See [WORKFLOW.md](./WORKFLOW.md) for the source, grouping, docs, writing, distribution, and release practices that apply across plugins and runtimes.
