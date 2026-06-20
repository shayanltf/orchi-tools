---
name: ios
description: Build, run, inspect, and extend iOS app behavior. Use when working with App Intents, iOS Simulator debugging, simulator UI inspection, or browser-visible simulator previews.
---

# iOS

Use this skill for iOS runtime, simulator, and system-surface work. Select the module that matches the actual task before running tools or editing code.

## Source Modules

Use these modules as the source of truth:

- `references/modules/ios-app-intents/source.md` for App Intents, app entities, App Shortcuts, Siri, Spotlight, widgets, and controls.
- `references/modules/ios-debugger-agent/source.md` for building, installing, launching, inspecting, and debugging iOS apps on Simulator with XcodeBuildMCP.
- `references/modules/ios-simulator-browser/source.md` for mirroring an iOS Simulator in the Codex browser and rendering SwiftUI previews from importable Swift packages.

When a module points to its own `references/` or `scripts/`, resolve the path inside that module directory first. When a module references a sibling `SKILL.md`, map it to that sibling module's `source.md` under this grouped tree.

## Workflow

1. Classify the request as system surface, simulator debugging, browser preview, or a combination.
2. Read the primary module before touching files or starting simulator tools.
3. Use App Intents guidance only when exposing actions or content to system surfaces.
4. Use the debugger module before the browser module when the app must first build, install, or launch.
5. Use the browser module when the user needs visible simulator interaction, preview proof, or hot reload.
6. Record the simulator device, scheme, bundle identifier, and command path when those details affect repeatability.
7. Verify behavior through the simulator, logs, screenshots, or browser-visible proof when available.

## Merge Rules

- Keep source-module content intact; apply it through this skill instead of rewriting it.
- Prefer project-local schemes and existing build scripts before inventing new launch paths.
- Route CPU profiling, leaks, and SwiftUI rendering problems to the `performance` skill when the iOS workflow exposes those concerns.
