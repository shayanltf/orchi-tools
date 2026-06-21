---
name: macos
description: Build native macOS app behavior covering AppKit interop, window chrome and placement, code signing, entitlements, packaging, and notarization. Use for any macOS-specific implementation, distribution, or trust failure that goes beyond shared SwiftUI patterns.
---

# macOS

Native macOS app work spans two broad layers: desktop UI behavior (windows, AppKit bridges, drag and drop) and distribution trust (signing, entitlements, packaging, notarization). Both layers are covered here. Work in only the area the task touches; combine them only when the task explicitly crosses that boundary.

These window and scene APIs target macOS 15+ SwiftUI. For older deployment targets, expect more AppKit bridging or `@available` guards.

## Use When

- Implementing an AppKit bridge, representable, NSWindow access, panel, menu validation, or responder-chain hook.
- Customizing window chrome, toolbar visibility, drag regions, background materials, minimize/zoom/restoration behavior, launch behavior, or placement.
- Diagnosing a codesign failure, sandbox rejection, Gatekeeper block, hardened runtime error, or entitlement mismatch.
- Archiving, exporting, or notarizing an app bundle; validating distribution readiness.

Do not use this skill for pure SwiftUI scene architecture, settings scenes, inspectors, sidebars, or document models — those belong in `swiftui-patterns`. Route SwiftPM-only build and test workflows to the `build` skill unless signing or packaging is the blocker.

## Merged Workflow

Work through the stages that apply to the task. Skip stages that do not apply.

### 1. Identify the task surface

Classify the task as one or more of:

- Desktop UI behavior — window chrome, drag, AppKit bridge
- AppKit interop — representables, panels, menus, responder chain, drag/drop
- Signing and trust — local launch failures, entitlement errors, Gatekeeper
- Distribution — archiving, exporting, notarization readiness

### 2. AppKit interop (when SwiftUI is not enough)

Use the smallest bridge that solves the problem.

- Use pure SwiftUI when behavior already exists in scenes, toolbars, commands, inspectors, or standard controls.
- Use `NSViewRepresentable` for a view-level bridge (e.g. `NSTextView`, custom control).
- Use `NSViewControllerRepresentable` when controller lifecycle, delegate coordination, or AppKit presentation logic is needed.
- Use direct AppKit window or app hooks only for `NSWindow`, responder-chain, menu validation, panels, or app-level behavior that SwiftUI does not expose.

Ownership rule: SwiftUI owns value state, selection, and observable models. AppKit objects stay inside the representable, coordinator, or bridge object. Expose only bindings and small callbacks back to SwiftUI.

Lifecycle rule: SwiftUI may recreate representables. Coordinators hold delegate and target-action glue — they are not a second app architecture.

### 3. Window chrome and behavior

Before reaching for AppKit, check whether SwiftUI scene and window modifiers already solve it.

**Toolbar and title**
- `.toolbar(removing: .title)` — hide the drawn title while keeping it logical for accessibility and menus.
- `.toolbarBackgroundVisibility(.hidden, for: .windowToolbar)` — extend media or hero content to the top edge.
- `.toolbarVisibility(.hidden, for: .windowToolbar)` — remove the toolbar entirely when controls are not needed.
- Remove manually painted titlebar fills before layering these APIs.

**Drag regions**
- Always replace any lost drag affordance after hiding the toolbar or toolbar background.
- Use `WindowDragGesture()` on a transparent overlay or non-interactive header region.
- Pair with `.allowsWindowActivationEvents(true)` so click-then-drag from a background window activates and moves it.
- For media players, insert the drag overlay between content and playback controls so AVKit keeps receiving input.

**Background and materials**
- `.containerBackground(.thickMaterial, for: .window)` — frosted material for utility or About windows.
- Prefer system materials over hardcoded translucent colors.

**Window behavior**
- `.windowMinimizeBehavior(.disabled)` — always-reachable utility windows (e.g. About).
- `.restorationBehavior(.disabled)` — windows that should not reopen at next launch (About, transient info, welcome).
- Keep restoration enabled for primary document and navigation windows.
- `.defaultLaunchBehavior(.presented)` — windows that must appear first at launch (e.g. welcome window).

**Placement**
- `.defaultWindowPlacement { content, context in ... }` — initial size/position for newly opened windows. Use `content.sizeThatFits(.unspecified)` and clamp to `context.defaultDisplay.visibleRect`.
- `.windowIdealPlacement { content, context in ... }` — zoom behavior (Window > Zoom or Option-click green button). Preserve aspect ratio; fit the display.
- Always account for external displays and rotated or narrow screens when sizing player or document windows.

**Borderless windows**
- `.windowStyle(.plain)` — no standard titlebar. Always provide a visible drag affordance and a clear close path.

### 4. Signing and entitlements (when launch or trust fails locally)

Work signing before packaging when the failure is local.

1. Inspect the bundle: `codesign -dvvv --entitlements :- <app-or-binary>`.
2. Check Gatekeeper when relevant: `spctl -a -vv <app-or-binary>`.
3. Inspect entitlements or Info.plist: `plutil -p <path>`.
4. List available signing identities: `security find-identity -p codesigning -v`.

Classify the failure:

- Unsigned or ad hoc signed
- Wrong identity
- Entitlement mismatch
- Hardened runtime issue
- App Sandbox issue
- Nested code signing issue
- Distribution or notarization prerequisite

Explain the minimum fix path. Distinguish local development problems from distribution problems. Never invent missing entitlements. Do not conflate notarization with local debug signing.

Preserve entitlements and signing settings the project already depends on.

### 5. Packaging and notarization (when distributing)

Work this stage when the artifact must be archived, exported, notarized, or distributed.

1. Confirm the distribution goal: local archive validation, signed distributable, or notarization troubleshooting.
2. Validate bundle structure: nested frameworks, helper tools, and embedded entitlements.
3. Check signing prerequisites: hardened runtime, signing identity, nested code signatures, required entitlements.
4. Separate packaging issues from trust-policy symptoms. Point to the minimum follow-up validation commands.

Do not present notarization as required for ordinary local debug runs. Disclose when the actual exported artifact is not available and conclusions are inferred from project settings.

### 6. Verify

Use the smallest local build, launch, codesign, notarization, or package inspection path that matches the task scope. Use `build-run-debug` to verify window behavior in a real foreground `.app` bundle.

## Key Rules

- Keep AppKit bridges narrow and explicitly owned. SwiftUI is the source of truth; AppKit handles the imperative edge.
- Never hide a toolbar or toolbar background without replacing the drag affordance.
- Never disable restoration on the main document window unless the user explicitly wants a fresh-start app.
- Do not reach for `NSWindow` mutation before checking whether SwiftUI window modifiers already solve the problem.
- Do not duplicate the source of truth between SwiftUI and AppKit.
- Never invent entitlements. Preserve those the project already depends on.
- Call out when inference is based on project settings rather than an actual exported artifact.
- Keep macOS guidance separate from iOS SwiftUI guidance unless a shared view layer is being edited.

## References

- `references/appkit-interop.md` — Bridge selection, ownership model, lifecycle rules, and output expectations for AppKit interop. Load when implementing any representable, coordinator, panel, or AppKit hook.
- `references/appkit-interop-representables.md` — `NSViewRepresentable` vs `NSViewControllerRepresentable` choice, coordinator skeleton, and pitfalls. Load when writing or reviewing a representable wrapper.
- `references/appkit-interop-window-panels.md` — `NSWindow` access, utility panels, and `NSOpenPanel`/`NSSavePanel` usage. Load when SwiftUI scenes are not enough for panel or window behavior.
- `references/appkit-interop-responder-menus.md` — First responder, command routing, and menu validation patterns. Load when AppKit responder-chain hooks are needed for menu enablement or action routing.
- `references/appkit-interop-drag-drop-pasteboard.md` — File URL dragging, `NSPasteboard`, custom pasteboard types, and AppKit drop delegates. Load when SwiftUI drag/drop APIs are insufficient.
- `references/window-management.md` — Full SwiftUI window chrome guide: toolbar, drag regions, materials, minimize/restoration/launch behavior, placement, borderless windows, review checklist, and guardrails. Load for any window customization task.
- `references/window-management-api-snippets.md` — Concrete Swift code examples for all window modifier patterns. Load when role and modifier choices are clear and implementation examples are needed.
- `references/signing-entitlements.md` — Inspection commands, failure classification, and minimum fix paths for codesign, sandbox, hardened runtime, and Gatekeeper issues. Load when a signing or trust failure is the blocker.
- `references/packaging-notarization.md` — Workflow, guardrails, and output expectations for archiving, bundle validation, and notarization readiness. Load when the task is about distribution rather than local development.
