---
name: macos
description: Build native macOS app behavior around AppKit interop, signing, notarization, entitlements, windows, and desktop runtime constraints. Use for macOS-specific app work.
---

# macOS

Use this skill for macOS-specific app behavior and distribution constraints. Select modules by the failure mode or implementation surface, then combine them only when the task crosses those boundaries.

## Source Modules

Use these modules as the source of truth:

- `references/modules/appkit-interop/source.md` for narrow SwiftUI-to-AppKit bridges, representables, NSWindow access, panels, menus, and responder-chain work.
- `references/modules/window-management/source.md` for SwiftUI window chrome, drag regions, placement, restoration, launch behavior, and borderless windows.
- `references/modules/signing-entitlements/source.md` for codesign, sandbox, hardened runtime, entitlements, Gatekeeper, and trust failures.
- `references/modules/packaging-notarization/source.md` for archives, exported bundles, notarization readiness, hardened runtime, and distribution validation.

When a module points to its own `references/` or `scripts/`, resolve the path inside that module directory first. When a module references a sibling `SKILL.md`, map it to that sibling module's `source.md` under this grouped tree.

## Workflow

1. Identify whether the task concerns desktop UI behavior, AppKit bridging, runtime trust, or distribution.
2. Read the matching module before editing code or changing signing settings.
3. Keep AppKit interop narrow and tied to the exact macOS behavior SwiftUI cannot provide.
4. Use signing guidance before packaging guidance when launch or trust fails locally.
5. Use packaging guidance when the artifact must be archived, exported, notarized, or distributed.
6. Preserve entitlements and signing settings that the project already depends on.
7. Verify with the smallest local build, launch, codesign, notarization, or package inspection path that matches the task.

## Merge Rules

- Keep source-module content intact; apply it through this skill instead of rewriting it.
- Keep macOS UI guidance separate from iOS SwiftUI guidance unless the same shared view layer is being edited.
- Route SwiftPM-only build and test workflows to the `build` skill unless macOS signing or packaging is the blocker.
