# Orchi Tools

Orchi Tools is a plugin marketplace for agent harnesses.

Maintained by the Orchi Team, with source published from `shayanltf/orchi-tools`.

## Catalog

- `apple` - available. Apple ecosystem skills for Codex and Claude Code.
- `web` - available. Frontend web skills for Codex and Claude Code.

## Install

Install from marketplace metadata. Do not clone this repo into every project.

### Codex

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Open the Codex app plugin directory, choose the `Orchi Tools` marketplace, then install or enable `Apple` or `Web`.

Use the grouped Codex skills:

```text
Use $swiftui to refactor this SwiftUI view.
Use $ios to debug this iOS simulator failure.
Use $macos to inspect this macOS signing error.
Use $build to triage this SwiftPM test failure.
Use $performance to investigate this memory growth.
```

Use the scoped Web Codex skills:

```text
Use $frontend-app-builder to build a polished frontend.
Use $frontend-testing-debugging to verify this UI.
Use $react-best-practices to review React performance.
Use $shadcn to work with shadcn/ui components.
```

### Claude Code

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install apple@orchi-tools
claude plugin install web@orchi-tools
```

Invoke the grouped skills by namespace:

```text
/apple:swiftui
/apple:ios
/apple:macos
/apple:build
/apple:performance
/web:frontend-app-builder
/web:frontend-testing-debugging
/web:react-best-practices
/web:shadcn
```

## Skill Library

### Apple

- `swiftui` - SwiftUI UI, Liquid Glass, component patterns, and view refactors across Apple platforms.
- `ios` - App Intents, iOS Simulator debugging, simulator inspection, and browser-visible simulator previews.
- `macos` - AppKit interop, windows, signing, entitlements, packaging, and notarization.
- `build` - Xcode and SwiftPM build, run, debug, and test triage workflows.
- `performance` - ETTrace profiling, memgraph leaks, SwiftUI performance audits, and telemetry.

### Web

- `frontend-app-builder` - Frontend app, dashboard, game, creative website, hero, redesign, and visual UI building.
- `frontend-testing-debugging` - Rendered frontend QA, local dev server validation, browser testing, console checks, screenshots, and interaction proof.
- `react-best-practices` - React and Next.js performance guidance from Vercel Engineering.
- `shadcn` - shadcn/ui component, registry, styling, composition, CLI, and project workflow guidance.

## Runtime Layout

Each plugin owns its own scoped root under `plugins/<plugin-name>/`.

- `plugins/apple/` contains the Apple plugin for Codex and Claude.
- `plugins/web/` contains the Web plugin for Codex and Claude.
- `.agents/plugins/marketplace.json` is the Codex marketplace catalog. It points each plugin entry to its scoped root.
- `.claude-plugin/marketplace.json` is the Claude marketplace catalog. It points each plugin entry to that plugin's `claude/` subdirectory with `git-subdir`.
- `docs/` and `research/` describe marketplace-wide rules and source inventory; each plugin may also keep scoped docs and research under its own root.

## Apple Source Attribution

Apple imports Apple-related skill content from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths: `plugins/build-ios-apps` and `plugins/build-macos-apps`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.
- iOS and macOS plugin work is credited to Thomas Ricouard (Dimillian): https://github.com/Dimillian, https://x.com/Dimillian.

## Web Source Attribution

Web imports selected skill directories from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths:
  - `plugins/build-web-apps/skills/frontend-app-builder`
  - `plugins/build-web-apps/skills/frontend-testing-debugging`
  - `plugins/build-web-apps/skills/react-best-practices`
  - `plugins/build-web-apps/skills/shadcn-best-practices`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.
- React best practices preserve Vercel Engineering metadata from the source skill.

No Stripe, Supabase/Postgres, or web data visualization source content is copied into this plugin.

## Local Development

Run the Codex plugin validator from the `plugin-creator` skill against each plugin root:

```bash
python3 path/to/plugin-creator/scripts/validate_plugin.py plugins/apple
python3 path/to/plugin-creator/scripts/validate_plugin.py plugins/web
```

Validate marketplace catalogs with `jq . .agents/plugins/marketplace.json` and `jq . .claude-plugin/marketplace.json`.

## Release

Initial release tag: `v0.1.0`.
