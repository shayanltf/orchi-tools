# Codex Runtime

Codex installs the Apple plugin through the `orchi-tools` marketplace. The Codex plugin name is `apple`.

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Open the Codex app plugin directory, choose the `Orchi Tools` marketplace, then install or enable `Apple`.

Codex reads `codex/apple/.codex-plugin/plugin.json`. The root marketplace points to `codex/apple/` as the Codex plugin directory.

Inside that plugin directory, the manifest points at the validator-compatible grouped skill directory:

```text
skills/
```

Use these grouped skills from the Apple plugin:

- `swiftui` - SwiftUI UI, Liquid Glass, component patterns, and view refactors across Apple platforms.
- `ios` - App Intents, iOS Simulator debugging, simulator inspection, and browser-visible simulator previews.
- `macos` - AppKit interop, windows, signing, entitlements, packaging, and notarization.
- `build` - Xcode and SwiftPM build, run, debug, and test triage workflows.
- `performance` - ETTrace profiling, memgraph leaks, SwiftUI performance audits, and telemetry.

Invoke the grouped skills through Codex, for example:

```text
Use $swiftui to refactor this SwiftUI view.
Use $ios to debug this iOS simulator failure.
Use $macos to inspect this signing error.
Use $build to triage this SwiftPM test failure.
Use $performance to investigate this memory growth.
```

Codex loads `codex/apple/.mcp.json` for XcodeBuildMCP-backed iOS simulator workflows.
