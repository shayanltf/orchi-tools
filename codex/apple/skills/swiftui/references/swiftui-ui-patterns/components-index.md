# Components Index

Use this file to find component and cross-cutting guidance. Each entry lists when to use it.

## Available components

- TabView: `references/swiftui-ui-patterns/tabview.md` — Use when building a tab-based app or any tabbed feature set.
- NavigationStack: `references/swiftui-ui-patterns/navigationstack.md` — Use when you need push navigation and programmatic routing, especially per-tab history.
- Sheets and presentation: `references/swiftui-ui-patterns/sheets.md` — Use for local item-driven sheets, centralized modal routing, and sheet-specific action patterns.
- Form and Settings: `references/swiftui-ui-patterns/form.md` — Use for settings, grouped inputs, and structured data entry.
- macOS Settings: `references/swiftui-ui-patterns/macos-settings.md` — Use when building a macOS Settings window with SwiftUI's Settings scene.
- Split views and columns: `references/swiftui-ui-patterns/split-views.md` — Use for iPad/macOS multi-column layouts or custom secondary columns.
- List and Section: `references/swiftui-ui-patterns/list.md` — Use for feed-style content and settings rows.
- ScrollView and Lazy stacks: `references/swiftui-ui-patterns/scrollview.md` — Use for custom layouts, horizontal scrollers, or grids.
- Scroll-reveal detail surfaces: `references/swiftui-ui-patterns/scroll-reveal.md` — Use when a detail screen reveals secondary content or actions as the user scrolls or swipes between full-screen sections.
- Grids: `references/swiftui-ui-patterns/grids.md` — Use for icon pickers, media galleries, and tiled layouts.
- Theming and dynamic type: `references/swiftui-ui-patterns/theming.md` — Use for app-wide theme tokens, colors, and type scaling.
- Controls (toggles, pickers, sliders): `references/swiftui-ui-patterns/controls.md` — Use for settings controls and input selection.
- Input toolbar (bottom anchored): `references/swiftui-ui-patterns/input-toolbar.md` — Use for chat/composer screens with a sticky input bar.
- Top bar overlays (iOS 26+ and fallback): `references/swiftui-ui-patterns/top-bar.md` — Use for pinned selectors or pills above scroll content.
- Overlay and toasts: `references/swiftui-ui-patterns/overlay.md` — Use for transient UI like banners or toasts.
- Focus handling: `references/swiftui-ui-patterns/focus.md` — Use for chaining fields and keyboard focus management.
- Searchable: `references/swiftui-ui-patterns/searchable.md` — Use for native search UI with scopes and async results.
- Async images and media: `references/swiftui-ui-patterns/media.md` — Use for remote media, previews, and media viewers.
- Haptics: `references/swiftui-ui-patterns/haptics.md` — Use for tactile feedback tied to key actions.
- Matched transitions: `references/swiftui-ui-patterns/matched-transitions.md` — Use for smooth source-to-destination animations.
- Deep links and URL routing: `references/swiftui-ui-patterns/deeplinks.md` — Use for in-app navigation from URLs.
- Title menus: `references/swiftui-ui-patterns/title-menus.md` — Use for filter or context menus in the navigation title.
- Menu bar commands: `references/swiftui-ui-patterns/menu-bar.md` — Use when adding or customizing macOS/iPadOS menu bar commands.
- Loading & placeholders: `references/swiftui-ui-patterns/loading-placeholders.md` — Use for redacted skeletons, empty states, and loading UX.
- Lightweight clients: `references/swiftui-ui-patterns/lightweight-clients.md` — Use for small, closure-based API clients injected into stores.

## Cross-cutting references

- App wiring and dependency graph: `references/swiftui-ui-patterns/app-wiring.md` — Use to wire the app shell, install shared dependencies, and decide what belongs in the environment.
- Async state and task lifecycle: `references/swiftui-ui-patterns/async-state.md` — Use when a view loads data, reacts to changing input, or needs cancellation/debouncing guidance.
- Previews: `references/swiftui-ui-patterns/previews.md` — Use when adding `#Preview`, fixtures, mock environments, or isolated preview setup.
- Performance guardrails: `references/swiftui-ui-patterns/performance.md` — Use when a screen is large, scroll-heavy, frequently updated, or showing signs of avoidable re-renders.

## Planned components (create files as needed)

- Web content: create `references/swiftui-ui-patterns/webview.md` — Use for embedded web content or in-app browsing.
- Status composer patterns: create `references/swiftui-ui-patterns/composer.md` — Use for composition or editor workflows.
- Text input and validation: create `references/swiftui-ui-patterns/text-input.md` — Use for forms, validation, and text-heavy input.
- Design system usage: create `references/swiftui-ui-patterns/design-system.md` — Use when applying shared styling rules.

## Adding entries

- Add the component file and link it here with a short “when to use” description.
- Keep each component reference short and actionable.
