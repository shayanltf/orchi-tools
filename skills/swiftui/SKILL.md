---
name: swiftui
description: Build, refactor, review, and tune SwiftUI features across Apple platforms. Use when shaping SwiftUI screens, scenes, navigation, state, components, Liquid Glass UI, or view structure.
---

# SwiftUI

This skill covers SwiftUI work across iOS and macOS: UI and navigation patterns, platform scenes and windowing, Liquid Glass adoption, and view-structure refactors. Use it when building or reviewing SwiftUI screens, choosing navigation/layout/state patterns, adopting Liquid Glass, or splitting oversized views.

## Use when

- Building or reviewing SwiftUI views, navigation, layout, controls, state, or previews on iOS.
- Building macOS SwiftUI scenes, windows, commands and menus, settings, or split-view inspectors.
- Adopting or reviewing iOS 26+ Liquid Glass surfaces and system chrome.
- Refactoring large SwiftUI views: splitting, Observation ownership, and data-flow cleanup.

## Workflow

### 1) Classify the target

Decide whether the target is iOS, macOS, or shared SwiftUI, and whether the task is UI construction, Liquid Glass adoption, or a structural refactor. More than one may apply. Load the smallest set of topic references that covers the task.

### 2) iOS SwiftUI UI patterns

Start from [`references/ios-ui-patterns.md`](./references/ios-ui-patterns.md) for navigation, state, layout, controls, previews, and app wiring. Load the focused topic file for the surface in play — for example [`references/ios-navigationstack.md`](./references/ios-navigationstack.md), [`references/ios-list.md`](./references/ios-list.md), [`references/ios-sheets.md`](./references/ios-sheets.md), [`references/ios-controls.md`](./references/ios-controls.md), [`references/ios-form.md`](./references/ios-form.md), [`references/ios-scrollview.md`](./references/ios-scrollview.md), or [`references/ios-performance.md`](./references/ios-performance.md). The full topic list is in [`references/ios-components-index.md`](./references/ios-components-index.md).

### 3) macOS SwiftUI patterns

Use [`references/macos-patterns.md`](./references/macos-patterns.md) for scenes, commands, toolbars, settings, split views, and inspectors, with focused files such as [`references/macos-windowing.md`](./references/macos-windowing.md), [`references/macos-commands-menus.md`](./references/macos-commands-menus.md), [`references/macos-settings.md`](./references/macos-settings.md), and [`references/macos-split-inspectors.md`](./references/macos-split-inspectors.md). The full topic list is in [`references/macos-components-index.md`](./references/macos-components-index.md).

### 4) Liquid Glass

Add Liquid Glass guidance only when the task asks for Liquid Glass, glass surfaces, system chrome, or iOS 26+ design review: [`references/ios-liquid-glass.md`](./references/ios-liquid-glass.md) for iOS or [`references/macos-liquid-glass.md`](./references/macos-liquid-glass.md) for macOS, with API detail in [`references/liquid-glass-api.md`](./references/liquid-glass-api.md).

### 5) View refactors

Add a refactor reference only when the request changes structure, state ownership, component boundaries, or view size: [`references/ios-view-refactor.md`](./references/ios-view-refactor.md) for iOS or [`references/macos-view-refactor.md`](./references/macos-view-refactor.md) for macOS, with model/view split patterns in [`references/mv-patterns.md`](./references/mv-patterns.md).

## Key rules

- Start from the user-visible task; load the smallest set of topic references that covers it.
- Prefer native SwiftUI before AppKit or UIKit escape hatches.
- Keep iOS- and macOS-specific guidance separate when a shared feature touches both platforms.
- Preserve the existing project architecture unless a reference explicitly justifies a change.
- Verify with the smallest available build, preview, or test path.
- Route runtime profiling to the `performance` skill, simulator build and run to the `ios` skill, and macOS signing or packaging to the `macos` skill when SwiftUI work surfaces those needs.

## References

- [`references/ios-ui-patterns.md`](./references/ios-ui-patterns.md) — iOS SwiftUI patterns overview; load first for any iOS UI task.
- [`references/ios-components-index.md`](./references/ios-components-index.md) — Index of the iOS topic files (navigation, list, sheets, controls, form, grids, media, theming, previews, and more); load to pick the exact topic file.
- [`references/macos-patterns.md`](./references/macos-patterns.md) — macOS SwiftUI patterns overview; load first for any macOS UI task.
- [`references/macos-components-index.md`](./references/macos-components-index.md) — Index of the macOS topic files (windowing, commands and menus, settings, split inspectors, menu bar extra).
- [`references/ios-liquid-glass.md`](./references/ios-liquid-glass.md) / [`references/macos-liquid-glass.md`](./references/macos-liquid-glass.md) / [`references/liquid-glass-api.md`](./references/liquid-glass-api.md) — Liquid Glass adoption and API detail; load only for glass surface work.
- [`references/ios-view-refactor.md`](./references/ios-view-refactor.md) / [`references/macos-view-refactor.md`](./references/macos-view-refactor.md) / [`references/mv-patterns.md`](./references/mv-patterns.md) — View splitting, Observation ownership, and data-flow refactors; load only for structural changes.

The remaining `references/ios-*.md` and `references/macos-*.md` files are focused topic docs named after their surface (for example `ios-tabview.md`, `ios-searchable.md`, `macos-windowing.md`); load the one that matches the screen or control in play.
