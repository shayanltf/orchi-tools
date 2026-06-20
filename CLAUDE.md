# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What This Repo Is

This repository publishes the `apple` plugin for two harnesses from one source:

- Claude Code, served from the `claude/` subdirectory.
- Codex, served from the `codex/apple/` subdirectory.

Both expose the same five grouped skills: `swiftui`, `ios`, `macos`, `build`, and `performance`. The skill content comes from OpenAI's official iOS and macOS plugin examples.

## Claude Plugin Structure

- `claude/.claude-plugin/plugin.json` is the Claude plugin manifest. The plugin name is `apple`.
- `claude/skills/<skill>/SKILL.md` defines each grouped skill, with that skill's supporting files under `claude/skills/<skill>/references/`.
- `.claude-plugin/marketplace.json` (repo root) is the Claude marketplace catalog. Its `apple` entry uses a `git-subdir` source with `path: claude`, so the Claude plugin root is `claude/`.

Because the plugin root is `claude/`, Claude loads only `claude/skills/`. Keep Claude skills separate from `codex/apple/skills/`.

## Authoring Skills

- Treat `SKILL.md` as the skill itself, not an index. Its YAML frontmatter (`name`, `description`) decides when Claude loads the skill; its body is the working instructions.
- Keep imported source guidance intact. Group and merge it; do not rewrite it unless paths, privacy, packaging, or style rules require edits.
- Do not create archived source wrappers such as `source.md`.
- Use purpose-named references and scripts inside each Claude skill when progressive disclosure is needed.
- Reference supporting files from `SKILL.md` so Claude knows what each one holds and when to load it.
- Do not add Codex-only files (`agents/openai.yaml`) to the Claude skills.
- Do not prefix skill folder names with the plugin name. The folder name `swiftui` becomes `/apple:swiftui`.

## Validation

- Run `claude --plugin-dir ./claude` from a checkout.
- Confirm each `claude/skills/<skill>/SKILL.md` has valid frontmatter and that every path it references resolves inside that skill folder.

## Conventions

See [WORKFLOW.md](./WORKFLOW.md) for the source, grouping, docs, writing, distribution, and release practices that apply across both runtimes.
