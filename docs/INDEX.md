# Apple Skills Index

## Root

- [README](../README.md) - Plugin purpose, install flow, OpenAI source attribution, skill library, local validation, release line.
- [WORKFLOW](../WORKFLOW.md) - OpenAI-only source rule, naming, docs, research, writing, install, review, and release rules.
- [Claude manifest](../.claude-plugin/plugin.json) - Claude plugin metadata for `apple-skills` and root `skills/`.
- [Claude marketplace](../.claude-plugin/marketplace.json) - Claude install catalog for `apple-skills@orchi-tools`.
- [Codex manifest](../.codex-plugin/plugin.json) - Codex plugin metadata, MCP config pointer, app card text, and root `skills/`.
- [Codex marketplace](../.agents/plugins/marketplace.json) - Codex install catalog for `Apple Skills` under `Orchi Tools`.
- [MCP config](../.mcp.json) - XcodeBuildMCP server config used by iOS simulator skills.
- [Build And Run macOS App Command](../commands/build-and-run-macos-app.md) - Detect project shape, create/update a run script, build, stop old app instance, and launch the fresh app.
- [Fix Codesign Error Command](../commands/fix-codesign-error.md) - Inspect macOS signing or entitlement failures and name the minimum fix path.
- [Test macOS App Command](../commands/test-macos-app.md) - Run the smallest useful macOS test scope and classify failures by cause.
- [Changelog](../CHANGELOG.md) - Release history for plugin versions.

## Context

- [Library Navigation](context/library-navigation.md) - Fast skill picker by Apple task: iOS App Intents, simulator, SwiftUI, macOS build, AppKit, signing, tests.
- [Plugin Packaging](context/plugin-packaging.md) - Claude/Codex plugin structure rules: manifests, root `skills/`, `.mcp.json`, commands, no `CLAUDE.md` or `CODEX.md`.
- [Skill Import Policy](context/skill-import-policy.md) - OpenAI-only import rules: active source paths, preserved skill structure, README attribution, stale-reference cleanup.
- [Docs And Research Rules](context/docs-and-research-rules.md) - What belongs in `docs/context/`, `research/`, README, WORKFLOW, changelog, and issue comments.
- [Release Review](context/release-review.md) - Validation and review checklist before PR handoff, tag move, or merge.

## Research

- [Source Inventory](../research/source-inventory.md) - Active OpenAI source paths, source snapshot, and copy decision.
- [Import Map](../research/import-map.md) - Repo skill names mapped to OpenAI `build-ios-apps` and `build-macos-apps` source paths.
- [Official Docs](../research/official-docs.md) - Official Claude, Codex, OpenAI plugin-source, and Apple docs used for scope verification.
