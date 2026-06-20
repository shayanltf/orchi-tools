---
name: performance
description: Diagnose Apple app performance, leaks, runtime logging, and profiling evidence. Use when profiling iOS Simulator flows, inspecting memgraphs, auditing SwiftUI runtime cost, or adding focused telemetry.
---

# Performance

Use this skill for measurement-backed performance, memory, and runtime-observability work. Select the evidence module first, then add platform modules only when setup or reproduction requires them.

## Source Modules

Use these modules as the source of truth:

- `references/modules/ios-ettrace-performance/source.md` for focused iOS Simulator ETTrace capture, symbolication, stack interpretation, and before/after comparisons.
- `references/modules/ios-memgraph-leaks/source.md` for iOS memgraph capture, leak inspection, retain-cycle analysis, and release verification.
- `references/modules/swiftui-performance-audit/source.md` for code-first SwiftUI runtime performance review and profiling follow-up.
- `references/modules/telemetry/source.md` for lightweight macOS unified Logger instrumentation and log inspection.

When a module points to its own `references/` or `scripts/`, resolve the path inside that module directory first. When a module references a sibling `SKILL.md`, map it to that sibling module's `source.md` under this grouped tree. For iOS launch, UI driving, logs, or screenshots, pair the performance module with `../ios/references/modules/ios-debugger-agent/source.md`.

## Workflow

1. Identify whether the problem is CPU latency, memory growth, SwiftUI rendering cost, or missing runtime evidence.
2. Read the matching module before collecting traces or editing code.
3. Define the exact user flow, start point, stop point, device, and build configuration before profiling.
4. Prefer code review for obvious SwiftUI invalidation or state problems, then request trace evidence when code does not explain the symptom.
5. Preserve before/after evidence for performance and leak fixes.
6. Keep telemetry lightweight and tied to decisions the team can make from logs.
7. Report confidence level, evidence path, and remaining uncertainty when profiling is partial.

## Merge Rules

- Keep source-module content intact; apply it through this skill instead of rewriting it.
- Route simulator launch/setup to `ios` and macOS signing or packaging blockers to `macos`.
- Avoid speculative performance claims without trace, log, memgraph, or code evidence.
