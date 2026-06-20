---
name: build
description: Build, run, debug, and test Apple projects with Xcode and SwiftPM. Use when discovering project structure, launching macOS apps, running SwiftPM packages, or triaging tests.
---

# Build

Use this skill for build, run, debug, and test loops that do not require a narrower platform skill first. Select the module by project entrypoint and failure type.

## Source Modules

Use these modules as the source of truth:

- `references/modules/build-run-debug/source.md` for shell-first macOS project discovery, build scripts, app launch, runtime failures, and Codex Run button wiring.
- `references/modules/swiftpm-macos/source.md` for SwiftPM-first macOS packages, executables, and tests.
- `references/modules/test-triage/source.md` for narrowing Xcode or SwiftPM test failures, assertions, crashes, and setup errors.

When a module points to its own `references/` or `scripts/`, resolve the path inside that module directory first. When a module references a sibling `SKILL.md`, map it to that sibling module's `source.md` under this grouped tree.

## Workflow

1. Discover the project entrypoint: Xcode project, workspace, SwiftPM package, or existing script.
2. Read the module that matches the entrypoint before adding scripts or changing commands.
3. Prefer existing project-local build commands before creating new ones.
4. Run the smallest meaningful command that reproduces the build, launch, or test result.
5. Classify failures as environment, dependency, compilation, signing, launch, runtime, or test-regression issues.
6. Escalate to `macos`, `ios`, `swiftui`, or `performance` only when the build loop identifies a narrower domain problem.
7. Report the command run, the result, and the next blocker when verification cannot complete.

## Merge Rules

- Keep source-module content intact; apply it through this skill instead of rewriting it.
- Do not replace project build structure unless the selected module requires a repeatable entrypoint and no equivalent exists.
- Keep test triage focused on the smallest failing scope before broad suites.
