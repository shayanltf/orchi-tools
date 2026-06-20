---
name: macos
description: Build native macOS app behavior around AppKit interop, signing, notarization, entitlements, windows, and desktop runtime constraints. Use for macOS-specific app work.
---

# macOS

Use this skill for macOS-specific app behavior and distribution constraints. Select modules by the failure mode or implementation surface, then combine them only when the task crosses those boundaries.

## Working References

Use these purpose-named references as the source of truth:

- `references/appkit-interop.md` for narrow SwiftUI-to-AppKit bridges, representables, NSWindow access, panels, menus, and responder-chain work.
- `references/window-management.md` for SwiftUI window chrome, drag regions, placement, restoration, launch behavior, and borderless windows.
- `references/signing-entitlements.md` for codesign, sandbox, hardened runtime, entitlements, Gatekeeper, and trust failures.
- `references/packaging-notarization.md` for archives, exported bundles, notarization readiness, hardened runtime, and distribution validation.

When a reference points to a supporting `references/<name>.md` file, resolve it inside the directory that matches the reference stem. For example, a pointer from `references/appkit-interop.md` to `references/representables.md` resolves to `references/appkit-interop/representables.md`.

## Workflow

1. Identify whether the task concerns desktop UI behavior, AppKit bridging, runtime trust, or distribution.
2. Read the matching module before editing code or changing signing settings.
3. Keep AppKit interop narrow and tied to the exact macOS behavior SwiftUI cannot provide.
4. Use signing guidance before packaging guidance when launch or trust fails locally.
5. Use packaging guidance when the artifact must be archived, exported, notarized, or distributed.
6. Preserve entitlements and signing settings that the project already depends on.
7. Verify with the smallest local build, launch, codesign, notarization, or package inspection path that matches the task.

## Merge Rules

- Keep imported source guidance intact except for path, packaging, privacy, or grouping fixes required by this Codex skill.
- Keep macOS UI guidance separate from iOS SwiftUI guidance unless the same shared view layer is being edited.
- Route SwiftPM-only build and test workflows to the `build` skill unless macOS signing or packaging is the blocker.
