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

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install apple@orchi-tools
```

Invoke the grouped skills by namespace:

```text
/apple:swiftui
/apple:ios
/apple:macos
/apple:build
/apple:performance
```

## Skill Library

- `swiftui` - SwiftUI UI, Liquid Glass, component patterns, and view refactors across Apple platforms.
- `ios` - App Intents, iOS Simulator debugging, simulator inspection, and browser-visible simulator previews.
- `macos` - AppKit interop, windows, signing, entitlements, packaging, and notarization.
- `build` - Xcode and SwiftPM build, run, debug, and test triage workflows.
- `performance` - ETTrace profiling, memgraph leaks, SwiftUI performance audits, and telemetry.

## Runtime Layout

Each runtime keeps its skills in its own plugin folder:

- `.agents/plugins/marketplace.json` exposes the repo marketplace.
- `codex/apple/` contains the Codex plugin root, manifest, assets, MCP config, and Codex-specific skills at `codex/apple/skills/`.
- `.claude-plugin/marketplace.json` exposes the Claude marketplace.
- `claude/` contains the Claude plugin root, manifest, and Claude-specific skills at `claude/skills/`.
- Keep Codex and Claude skill files separate, even when both runtimes use the same source guidance.

## Source Attribution

Apple imports Apple-related skill content from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths: `plugins/build-ios-apps` and `plugins/build-macos-apps`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.
- iOS and macOS plugin work is credited to Thomas Ricouard (Dimillian): https://github.com/Dimillian, https://x.com/Dimillian.

Only OpenAI-sourced Apple skill content belongs in this repo unless a future workflow decision explicitly changes the source policy.

## Local Development

Run the Codex plugin validator from the `plugin-creator` skill against `codex/apple/`.

Codex uses `codex/apple/.codex-plugin/plugin.json`, `codex/apple/.mcp.json`, and `.agents/plugins/marketplace.json` for marketplace validation and install flow.

## Release

Initial release tag: `v0.1.0`.
