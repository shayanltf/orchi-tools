# Apple

Apple is an Orchi Tools plugin package for Apple ecosystem work in agent harnesses.

Maintained by the Orchi Team, with source published from `shayanltf/orchi-tools`.

## Install

Install from marketplace metadata. Do not clone this repo into every project.

### Codex

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Open the Codex app plugin directory, choose the `Orchi Tools` marketplace, then install or enable `Apple`.

Use the grouped Codex skills:

```text
Use $swiftui to refactor this SwiftUI view.
Use $ios to debug this iOS simulator failure.
Use $macos to inspect this macOS signing error.
Use $build to triage this SwiftPM test failure.
Use $performance to investigate this memory growth.
```

### Claude Code

Claude Code uses its runtime-specific plugin manifest and guidance under `.claude-plugin/` and `claude/`.

## Skill Library

- `swiftui` - SwiftUI UI, Liquid Glass, component patterns, and view refactors across Apple platforms.
- `ios` - App Intents, iOS Simulator debugging, simulator inspection, and browser-visible simulator previews.
- `macos` - AppKit interop, windows, signing, entitlements, packaging, and notarization.
- `build` - Xcode and SwiftPM build, run, debug, and test triage workflows.
- `performance` - ETTrace profiling, memgraph leaks, SwiftUI performance audits, and telemetry.

## Runtime Layout

- `skills/` contains the Codex-compatible grouped skill surface. Codex requires this path in `.codex-plugin/plugin.json`.
- `codex/` contains Codex runtime notes.
- `.claude-plugin/` and `claude/` contain Claude Code runtime files.
- `.mcp.json` configures XcodeBuildMCP-backed iOS simulator workflows.

## Source Attribution

Apple imports Apple-related skill content from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths: `plugins/build-ios-apps` and `plugins/build-macos-apps`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.
- iOS and macOS plugin work is credited to Thomas Ricouard (Dimillian): https://github.com/Dimillian, https://x.com/Dimillian.

Only OpenAI-sourced Apple skill content belongs in this repo unless a future workflow decision explicitly changes the source policy.

## Local Development

Run the Codex plugin validator from the `plugin-creator` skill against the repo root.

Codex uses `.codex-plugin/plugin.json`, `.mcp.json`, and `.agents/plugins/marketplace.json` for marketplace validation and install flow.

## Release

Initial release tag: `v0.1.0`.
