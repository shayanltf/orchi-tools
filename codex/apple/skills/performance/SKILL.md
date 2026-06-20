---
name: performance
description: Diagnose Apple app performance, leaks, runtime logging, and profiling evidence. Use when profiling iOS Simulator flows, inspecting memgraphs, auditing SwiftUI runtime cost, or adding focused telemetry.
---

# Performance

Use this skill for measurement-backed performance, memory, and runtime-observability work. Select the evidence module first, then add platform modules only when setup or reproduction requires them.

## Working References

Use these purpose-named references as the source of truth:

- `references/ios-ettrace-performance.md` for focused iOS Simulator ETTrace capture, symbolication, stack interpretation, and before/after comparisons.
- `references/ios-memgraph-leaks.md` for iOS memgraph capture, leak inspection, retain-cycle analysis, and release verification.
- `references/swiftui-performance-audit.md` for code-first SwiftUI runtime performance review and profiling follow-up.
- `references/telemetry.md` for lightweight macOS unified Logger instrumentation and log inspection.

When a reference points to a supporting `references/<name>.md` or `scripts/<name>` path, resolve it inside the directory that matches the reference stem. For iOS launch, UI driving, logs, or screenshots, pair this skill with `../ios/references/ios-debugger-agent.md`.

## Workflow

1. Identify whether the problem is CPU latency, memory growth, SwiftUI rendering cost, or missing runtime evidence.
2. Read the matching module before collecting traces or editing code.
3. Define the exact user flow, start point, stop point, device, and build configuration before profiling.
4. Prefer code review for obvious SwiftUI invalidation or state problems, then request trace evidence when code does not explain the symptom.
5. Preserve before/after evidence for performance and leak fixes.
6. Keep telemetry lightweight and tied to decisions the team can make from logs.
7. Report confidence level, evidence path, and remaining uncertainty when profiling is partial.

## Merge Rules

- Keep imported source guidance intact except for path, packaging, privacy, or grouping fixes required by this Codex skill.
- Route simulator launch/setup to `ios` and macOS signing or packaging blockers to `macos`.
- Avoid speculative performance claims without trace, log, memgraph, or code evidence.
