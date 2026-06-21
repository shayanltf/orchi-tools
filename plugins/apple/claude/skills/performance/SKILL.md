---
name: performance
description: Diagnose Apple app performance, leaks, runtime logging, and profiling evidence. Use when profiling iOS Simulator flows, inspecting memgraphs, auditing SwiftUI runtime cost, or adding focused telemetry.
---

# Performance

This skill covers measurement-backed performance, memory, and runtime-observability work on Apple platforms: iOS Simulator ETTrace profiling, memgraph leak inspection, code-first SwiftUI performance audits, and lightweight unified-logging telemetry. Use it whenever a task involves CPU latency, memory growth, SwiftUI rendering cost, or missing runtime evidence.

## Use when

- Profiling an iOS Simulator flow for CPU hotspots with ETTrace and interpreting the captured stacks.
- Capturing and inspecting a memgraph to find leaks, retain cycles, and verify releases.
- Auditing SwiftUI runtime cost from code and profiling evidence.
- Adding focused unified `Logger` telemetry to make runtime behavior observable.

## Workflow

### 1) Classify the symptom

Decide whether the problem is CPU latency, memory growth, SwiftUI rendering cost, or missing runtime evidence. Read the matching reference before collecting traces or editing code, and define the exact user flow, start point, stop point, device, and build configuration before profiling.

### 2) ETTrace CPU profiling

Follow [`references/ettrace.md`](./references/ettrace.md) for focused iOS Simulator ETTrace capture, symbolication, stack interpretation, and before/after comparison. The bundled scripts in `scripts/ettrace/` (`collect_ios_dsyms.sh`, `analyze_flamegraph_json.py`) support dSYM collection and flamegraph analysis.

### 3) Memory and leaks

Follow [`references/memgraph-leaks.md`](./references/memgraph-leaks.md) for memgraph capture, leak inspection, retain-cycle analysis, and release verification. The bundled scripts in `scripts/memgraph/` (`capture_sim_memgraph.sh`, `summarize_memgraph_leaks.py`) support capture and summarization.

### 4) SwiftUI performance audit

Follow [`references/swiftui-performance-audit.md`](./references/swiftui-performance-audit.md) for code-first SwiftUI runtime review. Prefer code review for obvious invalidation or state problems first, then request trace evidence when code does not explain the symptom. Deepen with [`references/swiftui-profiling-intake.md`](./references/swiftui-profiling-intake.md), [`references/swiftui-code-smells.md`](./references/swiftui-code-smells.md), [`references/swiftui-optimizing-instruments.md`](./references/swiftui-optimizing-instruments.md), [`references/swiftui-understanding-hangs.md`](./references/swiftui-understanding-hangs.md), and [`references/swiftui-report-template.md`](./references/swiftui-report-template.md).

### 5) Telemetry

Follow [`references/telemetry.md`](./references/telemetry.md) for lightweight macOS unified `Logger` instrumentation and log inspection. Keep telemetry tied to decisions the team can make from logs.

## Key rules

- Avoid speculative performance claims without trace, log, memgraph, or code evidence.
- Define the flow, start/stop points, device, and build configuration before capturing any trace.
- Preserve before/after evidence for performance and leak fixes.
- Report confidence level, evidence path, and remaining uncertainty when profiling is partial.
- Route simulator launch, UI driving, logs, and screenshots to the `ios` skill, and macOS signing or packaging blockers to the `macos` skill.

## References

- [`references/ettrace.md`](./references/ettrace.md) — ETTrace capture, symbolication, and stack interpretation; load for CPU latency profiling. Helpers in `scripts/ettrace/`.
- [`references/memgraph-leaks.md`](./references/memgraph-leaks.md) — Memgraph capture, leak and retain-cycle inspection, release verification; load for memory work. Helpers in `scripts/memgraph/`.
- [`references/swiftui-performance-audit.md`](./references/swiftui-performance-audit.md) — Code-first SwiftUI runtime review; load for SwiftUI rendering cost. Supporting detail: [`references/swiftui-profiling-intake.md`](./references/swiftui-profiling-intake.md), [`references/swiftui-code-smells.md`](./references/swiftui-code-smells.md), [`references/swiftui-optimizing-instruments.md`](./references/swiftui-optimizing-instruments.md), [`references/swiftui-demystify-wwdc23.md`](./references/swiftui-demystify-wwdc23.md), [`references/swiftui-understanding-hangs.md`](./references/swiftui-understanding-hangs.md), [`references/swiftui-understanding-improving.md`](./references/swiftui-understanding-improving.md), [`references/swiftui-report-template.md`](./references/swiftui-report-template.md).
- [`references/telemetry.md`](./references/telemetry.md) — Lightweight unified `Logger` instrumentation and log inspection; load when adding runtime observability.
