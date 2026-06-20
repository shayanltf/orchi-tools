---
name: swiftui
description: Build, refactor, review, and tune SwiftUI features across Apple platforms. Use when shaping SwiftUI screens, scenes, navigation, state, components, Liquid Glass UI, or view structure.
---

# SwiftUI

Use this skill for SwiftUI work that spans iOS and macOS. Start from the user-visible task, choose the smallest relevant source modules, then merge their instructions into one implementation path.

## Working References

Use these purpose-named references as the source of truth:

- `references/swiftui-ui-patterns.md` for iOS SwiftUI navigation, state, layout, controls, previews, and app wiring.
- `references/swiftui-patterns.md` for macOS SwiftUI scenes, commands, toolbars, settings, split views, and inspectors.
- `references/swiftui-liquid-glass.md` for iOS 26+ Liquid Glass adoption and review.
- `references/liquid-glass.md` for macOS Liquid Glass adoption and review.
- `references/swiftui-view-refactor.md` for iOS SwiftUI view splitting, Observation ownership, and data flow cleanup.
- `references/view-refactor.md` for macOS SwiftUI scene and view refactors.

When a reference points to a supporting `references/<name>.md` file, resolve it inside the directory that matches the reference stem. For example, a pointer from `references/swiftui-ui-patterns.md` to `references/navigationstack.md` resolves to `references/swiftui-ui-patterns/navigationstack.md`.

## Workflow

1. Identify whether the target is iOS, macOS, or shared SwiftUI.
2. Read the matching platform module before editing.
3. Add Liquid Glass guidance only when the task asks for Liquid Glass, glass surfaces, system chrome, or iOS 26+ design review.
4. Add a refactor module only when the request changes structure, state ownership, component boundaries, or view size.
5. Merge the selected module instructions without duplicating conflicting guidance.
6. Preserve the existing project architecture unless the selected module explicitly justifies a change.
7. Verify with the smallest available build, preview, or test path from the project.

## Merge Rules

- Keep imported source guidance intact except for path, packaging, privacy, or grouping fixes required by this Codex skill.
- Prefer native SwiftUI before AppKit or UIKit escape hatches.
- Separate iOS-specific and macOS-specific guidance when a shared feature touches both platforms.
- Treat performance, simulator debugging, build, signing, and packaging work as separate skills unless SwiftUI code review directly uncovers the need.
