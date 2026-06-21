# Orchi Tools Index

## Root

- [README](../README.md) - Marketplace purpose, Apple and Web install flows, skill library, runtime layout, OpenAI source attribution, and release line.
- [WORKFLOW](../WORKFLOW.md) - Source policy, marketplace plugin scoping, naming, runtime layout, skill authoring, docs, writing, install distribution, and release practices.
- [CLAUDE.md](../CLAUDE.md) - Claude Code guidance for the multi-plugin marketplace, scoped Claude plugin roots, skill authoring, and validation.
- [AGENTS.md](../AGENTS.md) - Agent entry point; references `CLAUDE.md`.
- [Claude marketplace](../.claude-plugin/marketplace.json) - Claude install catalog for `apple@orchi-tools` and `web@orchi-tools`, each using a scoped `git-subdir` plugin root.
- [Codex marketplace](../.agents/plugins/marketplace.json) - Codex install catalog for `apple` and `web`, each pointing at `./plugins/<plugin-name>`.
- [Changelog](../CHANGELOG.md) - Release history for marketplace and plugin versions.

## Apple Plugin

- [Apple README](../plugins/apple/README.md) - Apple plugin install flow, grouped skill library, runtime layout, and source attribution.
- [Apple Codex manifest](../plugins/apple/.codex-plugin/plugin.json) - Codex plugin metadata for `apple`, MCP config pointer, app card text, and scoped `skills/`.
- [Apple Claude manifest](../plugins/apple/claude/.claude-plugin/plugin.json) - Claude plugin metadata for `apple`; plugin root is `plugins/apple/claude/`.
- [Apple MCP config](../plugins/apple/.mcp.json) - XcodeBuildMCP server config used by Codex iOS simulator skills.
- [Apple Codex runtime notes](../plugins/apple/codex/README.md) - Codex-specific Apple install, skill, and MCP notes.
- [Apple Claude runtime notes](../plugins/apple/claude/README.md) - Claude-specific Apple install, skill, and scoped plugin-root notes.
- [Build And Run macOS App Command](../plugins/apple/commands/build-and-run-macos-app.md) - Detect project shape, create/update a run script, build, stop old app instance, and launch the fresh app.
- [Fix Codesign Error Command](../plugins/apple/commands/fix-codesign-error.md) - Inspect macOS signing or entitlement failures and name the minimum fix path.
- [Test macOS App Command](../plugins/apple/commands/test-macos-app.md) - Run the smallest useful macOS test scope and classify failures by cause.

## Web Plugin

- [Web README](../plugins/web/README.md) - Web plugin install flow, skill library, runtime layout, and source attribution.
- [Web Codex manifest](../plugins/web/.codex-plugin/plugin.json) - Codex plugin metadata for `web`, app card text, and scoped `skills/`.
- [Web Claude manifest](../plugins/web/claude/.claude-plugin/plugin.json) - Claude plugin metadata for `web`; plugin root is `plugins/web/claude/`.
- [Web Claude runtime notes](../plugins/web/claude/README.md) - Claude-specific Web install, skill, and scoped plugin-root notes.
- [Web source inventory](../plugins/web/research/source-inventory.md) - Scoped Web source paths, source snapshot, copy decision, and explicit exclusions.
- [Web import map](../plugins/web/research/import-map.md) - Exact Web source skill directories mapped to Codex and Claude destinations.

## Context

- [Library Navigation](context/library-navigation.md) - Fast skill picker by Apple task: iOS App Intents, simulator, SwiftUI, macOS build, AppKit, signing, tests.
- [Plugin Packaging](context/plugin-packaging.md) - Codex and Claude packaging rules for scoped Apple and Web plugin roots, manifests, catalogs, runtime trees, MCP, and commands.
- [Skill Import Policy](context/skill-import-policy.md) - OpenAI-only import rules: active source paths, exact-copy Web import, runtime metadata, attribution, and stale-reference cleanup.
- [Docs And Research Rules](context/docs-and-research-rules.md) - What belongs in `docs/context/`, `research/`, README, WORKFLOW, changelog, and issue comments.
- [Release Review](context/release-review.md) - Validation and review checklist before PR handoff, tag move, or merge.

## Research

- [Source Inventory](../research/source-inventory.md) - Marketplace-wide active OpenAI source paths, source snapshot, and copy decisions.
- [Import Map](../research/import-map.md) - Apple grouped source map and Web exact-copy source map.
- [Official Docs](../research/official-docs.md) - Official Claude, Codex, OpenAI plugin-source, and Apple docs used for scope verification.
