# Apple Skill Research

Use when choosing Apple-platform skill coverage. Keep public-source-backed. No private source names. No personal workspace detail.

## Coverage Spine

- SwiftUI: view composition, state, data flow, layout, performance, current platform UI patterns.
- Swift concurrency: async/await, actors, task isolation, cancellation, Sendable, Swift 6 migration.
- Testing: Swift Testing macros, parameterized tests, XCTest migration, simulator/device split.
- Persistence: SwiftData first, Core Data when legacy or migration pressure exists, CloudKit sync when product scope needs it.
- Xcode build: build settings, warning policy, compile-time reduction, repeatable Makefile/script wrappers.
- Debug tooling: simulator workflow, browser/simulator inspection, ETTrace, memgraph, crash/log triage.
- macOS: AppKit interop, windows, signing, entitlements, notarization, SwiftPM packaging.
- Agent workflow: skill files stay small; deep examples live in references; scripts own deterministic build/test steps.

## Public Source Families

- Paul Hudson / Hacking with Swift: SwiftUI, Swift Concurrency, Swift Testing, SwiftData, and canonical Swift Agent Skills directory.
- Antoine van der Lee / SwiftLee: SwiftUI, Swift Concurrency, Swift Testing, Core Data, Xcode Build Optimization, RocketSim workflow.
- Thomas Ricouard / Dimillian plus OpenAI plugin examples: Codex Monitor, personal skills, official Build iOS Apps and Build macOS Apps plugin patterns.
- Krzysztof Zablocki / Merowing: rules-based LLM guidance, Sourcery, Inject, fast iteration patterns.
- AppCreator / Paul Solt: agent-friendly Xcode build scripts, Makefiles, warnings-as-errors, xcbeautify, version tracking.

## Compression Decision

- Keep capability names, trigger conditions, and tool boundaries.
- Drop biography, social-post prose, personal setup, and one-off commentary.
- Preserve public repo links in `source-map.md`, not every operational context leaf.
- Merge duplicated SwiftUI/concurrency/testing guidance by task purpose, not by author.
- Treat official iOS/macOS plugin layouts as packaging precedent; treat community repos as coverage evidence.
