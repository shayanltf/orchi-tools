---
name: ios
description: Build, run, inspect, and extend iOS app behavior. Use when working with App Intents, iOS Simulator debugging, simulator UI inspection, or browser-visible simulator previews.
---

# iOS

This skill covers three areas of iOS development: exposing app actions through App Intents, building and debugging apps on the iOS Simulator via XcodeBuildMCP, and mirroring a running simulator into the Codex in-app browser with SwiftUI hot-reload previews. Use it whenever a task involves system surfaces (Shortcuts, Siri, Spotlight, widgets, controls), simulator-based testing or debugging, or browser-visible proof of simulator behavior.

## Use when

- Designing or implementing `AppIntent`, `AppEntity`, `AppShortcutsProvider`, or widget/control configuration intents.
- Building, installing, launching, or debugging an iOS app on Simulator with XcodeBuildMCP.
- Capturing screenshots, logs, or UI descriptions from a running simulator.
- Mirroring an iOS Simulator into the browser for visible interaction or QA proof.
- Rendering SwiftUI previews from an importable Swift package outside Xcode Canvas with hot reload.

## Workflow

### 1) Classify the request

Determine which areas apply before reading any reference:

- **App Intents** — the task involves system surfaces, automation, Siri, Spotlight, widgets, or controls.
- **Simulator debugging** — the task involves building, running, launching, log capture, UI inspection, or diagnosing runtime behavior.
- **Simulator browser / previews** — the task requires browser-visible simulator output or SwiftUI hot-reload previews from a Swift package.

Multiple areas may apply. A browser preview session normally requires the app to build and launch first (debugger area), so run the debugger workflow before the browser workflow.

### 2) App Intents

Follow guidance in [`references/app-intents.md`](./references/app-intents.md).

**Sequence:**

1. Start with actions, not screens. Identify the 1–3 highest-value verbs (compose, open, find, filter, continue, start) that should work outside the app.
2. Define a small entity surface. Add `AppEntity` types only for objects the system needs to understand or route. Keep entities narrower than the persistence model.
3. Decide whether each action completes in place (`openAppWhenRun = false`) or opens the app (`openAppWhenRun = true`). When the app must react inside the main scene, add one clear routing path — an `AppIntentRouter` or equivalent — instead of scattering ad hoc navigation logic.
4. Add `AppShortcutsProvider` entries for the first set of high-value intents with direct, task-oriented phrases.
5. Build and verify: confirm the intents target compiles, intents appear in Shortcuts, and the app opens or routes to the expected place when an intent runs.

**Key rules:**

- Prefer a dedicated intents target or module for the system-facing layer.
- Keep intent types thin; business logic stays in app services or domain models.
- Use `AppEnum` for fixed choices (tabs, modes, visibility levels) before reaching for a full entity.
- Treat App Intents as system integration infrastructure, not only as a Shortcuts feature.
- Expose only the actions and entities that have real user value outside the app on the first pass.

**Anti-patterns:** exposing every screen as its own intent; mirroring the full model graph as entities; hiding runtime handoff in global side effects; vague Shortcut phrases; treating the first pass as a broad taxonomy project.

**Apple documentation:**
- `https://developer.apple.com/documentation/appintents/making-actions-and-content-discoverable-and-widely-available`
- `https://developer.apple.com/documentation/appintents/creating-your-first-app-intent`
- `https://developer.apple.com/documentation/appintents/adopting-app-intents-to-support-system-experiences`

Use web search to confirm current App Intents API behavior — the surface evolves across OS releases.

### 3) Simulator debugging

Follow guidance in [`references/debugger.md`](./references/debugger.md).

**Sequence:**

1. Call `mcp__XcodeBuildMCP__list_sims` and select the booted simulator. If none are booted, ask the user to boot one.
2. Call `mcp__XcodeBuildMCP__session-set-defaults` with `projectPath` or `workspacePath`, `scheme`, `simulatorId`, and optionally `configuration: "Debug"` and `useLatestOS: true`.
3. Call `mcp__XcodeBuildMCP__build_run_sim`. On failure, check error output and retry with `preferXcodebuild: true` or escalate before any UI interaction. On success, verify launch with `describe_ui` or `screenshot`.
4. Interact using `describe_ui` → `tap` / `type_text` / `gesture` → `screenshot`. Always call `describe_ui` before tapping; prefer `id` or `label` over coordinates.
5. For logs: `start_sim_log_cap` (bundle id) → work → `stop_sim_log_cap` and summarize important lines.

**If bundle id is unknown:** `get_sim_app_path` then `get_app_bundle_id`.

**Troubleshooting:** retry build with `preferXcodebuild: true`; confirm scheme and bundle id when the wrong app launches; re-run `describe_ui` after layout changes when elements are not hittable.

### 4) Simulator browser and SwiftUI previews

Follow guidance in [`references/simulator-browser.md`](./references/simulator-browser.md).

**Browser mirror:**

```bash
SIM="<simulator-udid>"
cleanup_serve_sim() {
  npx --yes serve-sim@latest --kill "$SIM" >/dev/null 2>&1 || true
}
trap cleanup_serve_sim EXIT INT TERM HUP
cleanup_serve_sim
npx --yes serve-sim@latest "$SIM"
```

Open the exact local URL printed by `serve-sim` in the Codex in-app browser. Verify a real frame is rendering — a loaded page alone is not proof the simulator stream is healthy. Keep the terminal alive while in use; when finished, stop it and wait for exit so the trap runs.

Never run an unscoped `serve-sim --kill`; another thread may own a different simulator mirror.

**SwiftUI package previews (hot reload):**

Use the bundled launcher for previews from an importable Swift package:

```bash
node <skill-root>/scripts/simulator-browser/swiftui-preview-browser.mjs \
  /absolute/path/to/Package.swift \
  --package-target "<target>" \
  --device "<simulator-udid>"
```

Watch mode is on by default. After the launcher prints the simulator UDID, start `serve-sim` for that same UDID and open its URL in the in-app browser.

To show a subset of previews: `--preview-filter <regex[,...]>` matched against display names and code identifiers.

For hot-reload QA: report the launcher's `hot reloaded package preview ... in pid ...` output and show the changed frame.

**Support boundary:** support Swift Package-backed `PreviewProvider` and `#Preview` declarations only. Do not edit the user's `.xcodeproj`, `.xcworkspace`, `Package.swift`, schemes, or build settings.

## Key rules across all areas

- Classify the request before touching files or starting simulator tools.
- Use the debugger workflow before the browser workflow when the app must first build, install, or launch.
- Prefer project-local schemes and existing build scripts; do not invent new launch paths.
- Record simulator device, scheme, bundle identifier, and command path when they affect repeatability.
- Verify behavior through the simulator, logs, screenshots, or browser-visible proof when available.
- Route CPU profiling, leaks, and SwiftUI rendering problems to the `performance` skill when the iOS workflow surfaces those concerns.

## References

- [`references/app-intents.md`](./references/app-intents.md) — Full App Intents workflow, strong defaults, and anti-patterns. Load when designing or implementing any App Intent, entity, query, widget configuration, or App Shortcuts surface.
- [`references/app-intents-first-pass-checklist.md`](./references/app-intents-first-pass-checklist.md) — Checklist for choosing the first intent and entity surface. Load when starting an App Intents integration from scratch.
- [`references/app-intents-example-patterns.md`](./references/app-intents-example-patterns.md) — Concrete example shapes: open-app handoff, inline background action, paired variants, `AppEnum`, entity selection, query dependencies, widget configuration, and shortcut phrase design. Load when deciding what pattern to implement.
- [`references/app-intents-code-templates.md`](./references/app-intents-code-templates.md) — Generalized Swift code templates for all major App Intents patterns. Load when writing new intent, entity, query, or shortcut provider code.
- [`references/app-intents-system-surfaces.md`](./references/app-intents-system-surfaces.md) — How to think about Shortcuts, Siri, Spotlight, widgets, Live Activities, and controls as entry points. Load when deciding which system surfaces an action should target.
- [`references/debugger.md`](./references/debugger.md) — Full XcodeBuildMCP workflow: discover simulator, set session defaults, build and run, UI interaction, log capture, and troubleshooting. Load for any build, run, inspect, or debug task on Simulator.
- [`references/simulator-browser.md`](./references/simulator-browser.md) — Browser mirror and SwiftUI preview launcher workflow, support boundary, and proof requirements. Load when mirroring the simulator into the Codex browser or rendering package previews with hot reload.
- `scripts/simulator-browser/` — Node.js launcher (`swiftui-preview-browser.mjs`) and generated-project helpers (`lib/xcode-project.mjs`, `templates/*.swift`). Referenced by the simulator-browser workflow; do not edit without updating the corresponding reference doc.
