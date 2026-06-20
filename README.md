# Apple Skills

Apple Skills is an open source plugin that centralizes Apple ecosystem agent skills for Claude Code and Codex.

Maintained by Shayan Latif, with source published from `shayanltf/orchi-tools`.

## What It Contains

- `docs/INDEX.md` - root context map with one leaf line per file.
- `WORKFLOW.md` - import, naming, docs, research, squad, and release workflow.
- `docs/context/` - reusable high-fidelity agent context, caveman-compressed.
- `research/` - durable long-term findings from public internet and official docs research.
- `skills/` - curated Apple ecosystem skills with purpose-scoped names.
- `claude/` - Claude Code runtime notes.
- `codex/` - Codex runtime notes.
- `.claude-plugin/plugin.json` - Claude Code plugin manifest.
- `.codex-plugin/plugin.json` - Codex plugin manifest.
- `licenses/` - copied third-party license files for imported MIT sources.

## Skill Library

### SwiftUI

- `swiftui-pro` - broad SwiftUI review and modern API guidance.
- `swiftui-expert` - SwiftUI state, view composition, invalidation, localization, animation, and API-refresh guidance.
- `swiftui-api-refresh` - official Apple docs scan workflow for SwiftUI API/deprecation refreshes.
- `swiftui-ui-patterns` - component, navigation, layout, and app wiring patterns.
- `swiftui-liquid-glass` - iOS 26+ Liquid Glass adoption and review.
- `swiftui-performance-audit` - SwiftUI runtime performance review and profiling guidance.
- `swiftui-view-refactor` - SwiftUI view splitting, Observation, dependency, and data-flow refactors.

### Swift Language, Tests, Persistence

- `swift-concurrency-pro` - broad Swift concurrency review and async/await guidance.
- `swift-concurrency` - diagnostic-first Swift 6 migration, actor isolation, Sendable, and data-race guidance.
- `swift-concurrency-expert` - remediation workflow for Swift 6.2+ concurrency warnings and errors.
- `swift-testing-pro` - modern Swift Testing review and improvement.
- `swift-testing-expert` - Swift Testing macros, traits, async tests, CI filtering, and XCTest migration.
- `swiftdata-pro` - SwiftData models, queries, migrations, and CloudKit-oriented guidance.
- `core-data` - Core Data stack, fetch, threading, migration, performance, and CloudKit guidance.

### Build, Debug, Release

- `xcode-build-orchestrator` - end-to-end Xcode build optimization workflow.
- `xcode-build-benchmark` - repeatable clean and incremental Xcode build baselines.
- `xcode-build-fixer` - approved Xcode build optimization implementation and re-benchmarking.
- `xcode-compilation-analyzer` - Swift compile hotspot analysis.
- `xcode-project-analyzer` - Xcode project, target, scheme, script phase, and build setting audit.
- `spm-build-analysis` - Swift Package Manager dependency and package graph build analysis.
- `ios-debugger-agent` - iOS simulator build/run/debug workflow through XcodeBuildMCP.
- `macos-menubar-tuist-app` - Tuist-first SwiftUI menubar app guidance.
- `macos-spm-app-packaging` - SwiftPM macOS app bundle, signing, notarization, and release packaging.
- `app-store-changelog` - user-facing App Store release note generation from git history.

## Source Attribution

Imported skill content comes from public MIT-licensed repositories:

- Paul Hudson / Hacking with Swift: https://github.com/twostraws/SwiftUI-Agent-Skill, https://github.com/twostraws/Swift-Concurrency-Agent-Skill, https://github.com/twostraws/Swift-Testing-Agent-Skill, https://github.com/twostraws/SwiftData-Agent-Skill
- Antoine van der Lee / SwiftLee: https://github.com/AvdLee/SwiftUI-Agent-Skill, https://github.com/AvdLee/Swift-Concurrency-Agent-Skill, https://github.com/AvdLee/Swift-Testing-Agent-Skill, https://github.com/AvdLee/Core-Data-Agent-Skill, https://github.com/AvdLee/Xcode-Build-Optimization-Agent-Skill
- Thomas Ricouard / Dimillian: https://github.com/Dimillian/Skills

Public sources researched but not copied because of license or availability constraints:

- OpenAI official iOS/macOS plugin examples: https://github.com/openai/plugins
- RocketSim Agent Skill: https://github.com/AvdLee/RocketSim-Agent-Skill
- SwiftLee Cursor collection: https://github.com/AvdLee/Swift-Agent-Skills-Cursor
- AppCreator skill download: https://super-easy-apps.kit.com/app-creator
- Merowing rules/tooling references: https://merowing.info/posts/stop-getting-average-code-from-your-llm

Third-party license copies live in `licenses/`.

## Use

Claude Code can load this repository as a local plugin:

```bash
claude --plugin-dir .
```

Invoke the context skill as:

```text
/apple-skills:<skill-name>
```

Codex can load the same repository through its local plugin flow. The Codex manifest points at `skills/`.

## Release

Initial release: `v0.1.0`.
