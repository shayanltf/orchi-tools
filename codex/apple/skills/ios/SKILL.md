---
name: ios
description: Build, run, inspect, and extend iOS app behavior. Use when working with App Intents, iOS Simulator debugging, simulator UI inspection, or browser-visible simulator previews.
---

# iOS

Use this skill for iOS runtime, simulator, and system-surface work. Select the module that matches the actual task before running tools or editing code.

## Working References

Use these purpose-named references as the source of truth:

- `references/ios-app-intents.md` for App Intents, app entities, App Shortcuts, Siri, Spotlight, widgets, and controls.
- `references/ios-debugger-agent.md` for building, installing, launching, inspecting, and debugging iOS apps on Simulator with XcodeBuildMCP.
- `references/ios-simulator-browser.md` for mirroring an iOS Simulator in the Codex browser and rendering SwiftUI previews from importable Swift packages.

When a reference points to a supporting `references/<name>.md` file, resolve it inside the directory that matches the reference stem. For example, a pointer from `references/ios-app-intents.md` to `references/code-templates.md` resolves to `references/ios-app-intents/code-templates.md`.

## Workflow

1. Classify the request as system surface, simulator debugging, browser preview, or a combination.
2. Read the primary module before touching files or starting simulator tools.
3. Use App Intents guidance only when exposing actions or content to system surfaces.
4. Use the debugger module before the browser module when the app must first build, install, or launch.
5. Use the browser module when the user needs visible simulator interaction, preview proof, or hot reload.
6. Record the simulator device, scheme, bundle identifier, and command path when those details affect repeatability.
7. Verify behavior through the simulator, logs, screenshots, or browser-visible proof when available.

## Merge Rules

- Keep imported source guidance intact except for path, packaging, privacy, or grouping fixes required by this Codex skill.
- Prefer project-local schemes and existing build scripts before inventing new launch paths.
- Route CPU profiling, leaks, and SwiftUI rendering problems to the `performance` skill when the iOS workflow exposes those concerns.
