# Import Map

Use when tracing repo skill destination to OpenAI source path.

## Apple iOS From `plugins/build-ios-apps/skills`

- `plugins/apple/skills/ios` and `plugins/apple/claude/skills/ios` include guidance from:
  - `plugins/build-ios-apps/skills/ios-app-intents`
  - `plugins/build-ios-apps/skills/ios-debugger-agent`
  - `plugins/build-ios-apps/skills/ios-simulator-browser`
- `plugins/apple/skills/performance` and `plugins/apple/claude/skills/performance` include guidance from:
  - `plugins/build-ios-apps/skills/ios-ettrace-performance`
  - `plugins/build-ios-apps/skills/ios-memgraph-leaks`
  - `plugins/build-ios-apps/skills/swiftui-performance-audit`
- `plugins/apple/skills/swiftui` and `plugins/apple/claude/skills/swiftui` include guidance from:
  - `plugins/build-ios-apps/skills/swiftui-liquid-glass`
  - `plugins/build-ios-apps/skills/swiftui-ui-patterns`
  - `plugins/build-ios-apps/skills/swiftui-view-refactor`

## Apple macOS From `plugins/build-macos-apps/skills`

- `plugins/apple/skills/macos` and `plugins/apple/claude/skills/macos` include guidance from:
  - `plugins/build-macos-apps/skills/appkit-interop`
  - `plugins/build-macos-apps/skills/packaging-notarization`
  - `plugins/build-macos-apps/skills/signing-entitlements`
  - `plugins/build-macos-apps/skills/window-management`
- `plugins/apple/skills/build` and `plugins/apple/claude/skills/build` include guidance from:
  - `plugins/build-macos-apps/skills/build-run-debug`
  - `plugins/build-macos-apps/skills/swiftpm-macos`
  - `plugins/build-macos-apps/skills/test-triage`
- `plugins/apple/skills/swiftui` and `plugins/apple/claude/skills/swiftui` include guidance from:
  - `plugins/build-macos-apps/skills/liquid-glass`
  - `plugins/build-macos-apps/skills/swiftui-patterns`
  - `plugins/build-macos-apps/skills/view-refactor`
- `plugins/apple/skills/performance` and `plugins/apple/claude/skills/performance` include guidance from:
  - `plugins/build-macos-apps/skills/telemetry`

## Apple Support Files

- `plugins/apple/.mcp.json` <- `plugins/build-ios-apps/.mcp.json`
- `plugins/apple/commands/` <- `plugins/build-macos-apps/commands`
- `plugins/apple/assets/build-ios-apps-small.svg` <- `plugins/build-ios-apps/assets/build-ios-apps-small.svg`
- `plugins/apple/assets/build-macos-apps-small.svg` <- `plugins/build-macos-apps/assets/build-macos-apps-small.svg`
- `plugins/apple/assets/app-icon.png` <- official Apple logo, rendered from `Apple_logo_black.svg` on Wikimedia Commons, centered on a 400x400 transparent canvas

## Web Exact-Copy Skills

- `plugins/web/skills/frontend-app-builder` <- `plugins/build-web-apps/skills/frontend-app-builder`
- `plugins/web/skills/frontend-testing-debugging` <- `plugins/build-web-apps/skills/frontend-testing-debugging`
- `plugins/web/skills/react-best-practices` <- `plugins/build-web-apps/skills/react-best-practices`
- `plugins/web/skills/shadcn-best-practices` <- `plugins/build-web-apps/skills/shadcn-best-practices`

## Web Claude Runtime Copies

- `plugins/web/claude/skills/frontend-app-builder` <- `plugins/build-web-apps/skills/frontend-app-builder`, excluding Codex-only `agents/`
- `plugins/web/claude/skills/frontend-testing-debugging` <- `plugins/build-web-apps/skills/frontend-testing-debugging`, excluding Codex-only `agents/`
- `plugins/web/claude/skills/react-best-practices` <- `plugins/build-web-apps/skills/react-best-practices`, excluding Codex-only `agents/`
- `plugins/web/claude/skills/shadcn-best-practices` <- `plugins/build-web-apps/skills/shadcn-best-practices`, excluding Codex-only `agents/`
