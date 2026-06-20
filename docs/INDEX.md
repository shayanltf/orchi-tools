# Apple Plugin Index

## Root

- [README](../README.md) - Plugin purpose, Codex and Claude install flow, grouped skill library, runtime layout, OpenAI source attribution, and release line.
- [WORKFLOW](../WORKFLOW.md) - Source policy, naming and grouping, runtime separation, skill authoring, docs, writing, install distribution, and release practices.
- [CLAUDE.md](../CLAUDE.md) - Claude Code guidance: repo purpose, Claude plugin structure, skill authoring, and validation.
- [AGENTS.md](../AGENTS.md) - Agent entry point; references `CLAUDE.md`.
- [Claude manifest](../claude/.claude-plugin/plugin.json) - Claude plugin metadata for `apple`; plugin root is `claude/`, skills at `claude/skills/`.
- [Claude marketplace](../.claude-plugin/marketplace.json) - Claude install catalog for `apple@orchi-tools` with a `git-subdir` source pointing at `claude/`.
- [Codex manifest](../codex/apple/.codex-plugin/plugin.json) - Codex plugin metadata for `apple`, MCP config pointer, app card text, and plugin-local `skills/`.
- [Codex marketplace](../.agents/plugins/marketplace.json) - Codex install catalog for `Apple` under `Orchi Tools` with local source path `./codex/apple`.
- [Codex MCP config](../codex/apple/.mcp.json) - XcodeBuildMCP server config used by Codex iOS simulator skills.
- [Build And Run macOS App Command](../commands/build-and-run-macos-app.md) - Detect project shape, create/update a run script, build, stop old app instance, and launch the fresh app.
- [Fix Codesign Error Command](../commands/fix-codesign-error.md) - Inspect macOS signing or entitlement failures and name the minimum fix path.
- [Test macOS App Command](../commands/test-macos-app.md) - Run the smallest useful macOS test scope and classify failures by cause.
- [Changelog](../CHANGELOG.md) - Release history for plugin versions.

## Context

- [Library Navigation](context/library-navigation.md) - Fast skill picker by grouped Apple task: SwiftUI, iOS, macOS, build, performance.
- [Plugin Packaging](context/plugin-packaging.md) - Runtime-separated plugin structure rules: Codex under `codex/apple/`, Claude under `claude/`, manifests, marketplace entries, MCP config, and no shared root `skills/`.
- [Skill Import Policy](context/skill-import-policy.md) - OpenAI-only import rules: active source paths, preserved skill structure, README attribution, stale-reference cleanup.
- [Docs And Research Rules](context/docs-and-research-rules.md) - What belongs in `docs/context/`, `research/`, README, WORKFLOW, changelog, and issue comments.
- [Release Review](context/release-review.md) - Validation and review checklist before PR handoff, tag move, or merge.

## Research

- [Source Inventory](../research/source-inventory.md) - Active OpenAI source paths, source snapshot, and copy decision.
- [Import Map](../research/import-map.md) - Grouped repo skill names mapped to OpenAI `build-ios-apps` and `build-macos-apps` source paths.
- [Official Docs](../research/official-docs.md) - Official Claude, Codex, OpenAI plugin-source, and Apple docs used for scope verification.
