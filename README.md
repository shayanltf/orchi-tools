# Apple Skills

Apple Skills is an open source plugin that packages Apple ecosystem skills for Claude Code and Codex.

Maintained by Shayan Latif in `shayanltf/orchi-tools`.

## What It Contains

- `.claude-plugin/marketplace.json` - Claude Code marketplace entry for installing from this repo.
- `.agents/plugins/marketplace.json` - Codex marketplace entry for installing from this repo.
- `.claude-plugin/plugin.json` - Claude Code plugin manifest.
- `.codex-plugin/plugin.json` - Codex plugin manifest.
- `.mcp.json` - XcodeBuildMCP configuration used by iOS simulator workflows.
- `skills/` - OpenAI-sourced Apple ecosystem skills.
- `commands/` - OpenAI-sourced macOS helper commands.
- `assets/` - plugin icons copied from the OpenAI Apple plugin examples.
- `docs/INDEX.md` - root context map with one leaf line per file.
- `docs/context/` - reusable repo context, caveman-compressed.
- `research/` - durable source and official-docs findings for this repo.
- `WORKFLOW.md` - source, docs, research, writing, validation, and release rules.
- `claude/` - Claude Code runtime notes.
- `codex/` - Codex runtime notes.

## Install

Install from marketplace metadata. Do not clone this repo into every project.

### Claude Code

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install apple-skills@orchi-tools
```

Invoke skills by namespace:

```text
/apple-skills:swiftui-ui-patterns
/apple-skills:ios-debugger-agent
/apple-skills:build-run-debug
```

### Codex

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Open the Codex app plugin directory, choose the `Orchi Tools` marketplace, then install or enable `Apple Skills`.

Use Apple Skills for Apple ecosystem work, for example:

```text
Use Apple Skills to refactor this SwiftUI view.
Use Apple Skills to debug this iOS simulator failure.
Use Apple Skills to inspect this macOS signing error.
```

## Skill Library

### iOS

- `ios-app-intents` - App Intents, app entities, App Shortcuts, and system surfaces.
- `ios-debugger-agent` - iOS simulator build, launch, UI inspection, and logs through XcodeBuildMCP.
- `ios-ettrace-performance` - ETTrace capture and stack analysis for iOS simulator profiling.
- `ios-memgraph-leaks` - memgraph capture, leak inspection, and before/after verification.
- `ios-simulator-browser` - Simulator mirroring and SwiftUI preview rendering in the Codex browser.
- `swiftui-liquid-glass` - iOS 26+ SwiftUI Liquid Glass implementation and review.
- `swiftui-performance-audit` - SwiftUI runtime performance audit from code and profiling evidence.
- `swiftui-ui-patterns` - SwiftUI navigation, layouts, controls, state, previews, and app wiring.
- `swiftui-view-refactor` - SwiftUI view splitting, Observation ownership, and data-flow cleanup.

### macOS

- `appkit-interop` - narrow SwiftUI-to-AppKit bridges for native macOS behavior.
- `build-run-debug` - shell-first macOS project discovery, build, launch, and debug workflow.
- `liquid-glass` - macOS SwiftUI Liquid Glass adoption and review.
- `packaging-notarization` - macOS bundle, signing, notarization, and distribution readiness checks.
- `signing-entitlements` - codesign, entitlements, hardened runtime, sandbox, and Gatekeeper inspection.
- `swiftpm-macos` - SwiftPM macOS package build, run, and test workflow.
- `swiftui-patterns` - native macOS SwiftUI scenes, menus, settings, windows, and desktop layouts.
- `telemetry` - focused unified Logger instrumentation and runtime event verification.
- `test-triage` - focused macOS test execution and failure classification.
- `view-refactor` - macOS SwiftUI scene and view refactors.
- `window-management` - SwiftUI macOS window chrome, drag regions, behavior, and placement.

## Source Attribution

Apple Skills imports Apple-related skill content from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths: `plugins/build-ios-apps` and `plugins/build-macos-apps`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.

Only OpenAI-sourced Apple skill content belongs in this repo unless a future workflow decision explicitly changes the source policy.

## Local Development

For maintainer validation from a checkout:

```bash
claude --plugin-dir .
```

Codex uses `.codex-plugin/plugin.json`, `.mcp.json`, and `.agents/plugins/marketplace.json` for marketplace validation and install flow.

## Release

Initial release tag: `v0.1.0`.
