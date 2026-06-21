---
name: build
description: Build, run, debug, and test Apple projects with Xcode and SwiftPM. Use when discovering project structure, launching macOS apps, running SwiftPM packages, or triaging tests.
---

# Build

This skill covers the full build-run-debug-test loop for macOS Apple projects. It applies to Xcode workspaces and projects, SwiftPM packages, and any hybrid entrypoint. It does not cover iOS simulators, mobile-specific tooling, or platform-narrowed concerns such as SwiftUI layout, performance profiling, or signing distribution — escalate to the relevant skill when the build loop surfaces those.

## Use When

- Discovering whether a project uses Xcode, SwiftPM, or both.
- Creating or updating `script/build_and_run.sh` and `.codex/environments/environment.toml`.
- Building, launching, or relaunching a macOS app or executable.
- Triaging build, launch, runtime, or test failures.
- Classifying a failure before escalating to a narrower domain skill.

## Workflow

### 1. Discover the project entrypoint

- Run `find . -name '*.xcworkspace' -o -name '*.xcodeproj' -o -name 'Package.swift'`.
- Check git status: `git rev-parse --is-inside-work-tree`. If no repo exists, run `git init` at the project root — never inside a nested subdirectory of a parent repo.
- If more than one entrypoint exists, explain the default choice and the ambiguity before proceeding.
- Pick the matching path below based on what you find.

### 2. Xcode projects and workspaces

- List schemes: `xcodebuild -list -workspace <workspace>` or `xcodebuild -list -project <project>`.
- Prefer the app-producing scheme unless the user names another.
- Determine the process name to kill before relaunch.
- Create or update `script/build_and_run.sh` to: kill the existing process, build via `xcodebuild`, launch the built `.app`.
- For the exact script shape and environment file format, load `references/run-debug-run-button-bootstrap.md`.

### 3. SwiftPM packages

- Read `Package.swift`. Identify executable, library, and test products.
- Use `swift build` by default; release mode only when explicitly requested.
- For true command-line executables: launch the raw binary via `swift run <product>` or from the build path.
- For AppKit/SwiftUI GUI apps: stage a project-local `.app` bundle under `dist/`, generate a minimal `Info.plist`, and launch with `/usr/bin/open -n <bundle>`. Do not launch SwiftPM GUI binaries directly — that produces no Dock icon, no foreground activation, and missing bundle identifier warnings.
- If the package is library-only, explain that it is not directly runnable.
- For the exact bundle-staging script shape, load `references/run-debug-run-button-bootstrap.md`.

### 4. Create or update `script/build_and_run.sh`

Every macOS project that runs repeatedly needs a single project-local entrypoint. The script must:

1. Kill the existing running process.
2. Build the target.
3. Launch the freshly built app or executable.

Support optional flags: `--debug` (lldb), `--logs` (log stream by process), `--telemetry` (log stream by subsystem), `--verify` (pgrep check). Keep the no-flag default path simple.

Keep the script in `script/build_and_run.sh`, not inside app source directories (`App/`, `Views/`, `Models/`, `Stores/`, `Services/`, `Support/`).

### 5. Wire the Codex Run button

After the script exists, write `.codex/environments/environment.toml` at the project root. If the file already exists, update the `Run` action command rather than adding a duplicate. Do not write this file before the script exists. Load `references/run-debug-run-button-bootstrap.md` for the exact TOML shape.

### 6. Run through the script

- Default: `./script/build_and_run.sh`
- With flags: `./script/build_and_run.sh --debug | --logs | --telemetry | --verify`

For SwiftPM packages without a run script yet, use `swift run <product>` or `swift test` directly.

### 7. Triage failures

Run the smallest meaningful command that reproduces the failure. Classify by category:

- **Build**: compiler, linker, missing SDK/toolchain, build settings, signing
- **Launch**: script bug, bundle misconfiguration, missing entitlements, activation policy
- **Runtime**: crash, signal, sandbox violation, async timing
- **Test**: assertion failure, flake, environment/fixture setup, missing host app, iOS-only assumption

For tests: start with the narrowest failing scope (single target or case) before running the full suite. Avoid full-suite reruns without new information.

For SwiftPM tests: `swift test` (add `--filter` when a specific case is known).
For Xcode tests: `xcodebuild test -scheme <scheme> -destination 'platform=macOS'`.

Distinguish compilation failures from test-execution failures. Mark likely flakes as such.

### 8. Debug

- Use `--logs` or `--telemetry` for config, entitlement, sandbox, and action-event verification.
- Use `--debug` or direct `lldb` for symbolized crash debugging.
- For SwiftPM GUI apps where the window does not come forward after launch: check `NSApp.setActivationPolicy(.regular)` and `NSApp.activate(ignoringOtherApps: true)`.
- If the user explicitly requests XcodeBuildMCP and it is available, use it for Xcode-aware discovery or debug/logging. Fall back to shell immediately when it does not provide a clean macOS path.

### 9. Escalate when appropriate

After the build loop identifies the root domain, escalate to: `macos`, `ios`, `swiftui`, or `performance`. Report the command run, the result, and the next blocker when verification cannot complete in this skill.

## Key Rules

- Prefer existing project-local build commands before creating new ones.
- Run the narrowest command that proves or disproves the current theory.
- Do not leave a one-off manual command chain once a stable `build_and_run.sh` can own the workflow.
- Do not write `.codex/environments/environment.toml` before the run script exists.
- Do not launch SwiftPM GUI apps as raw executables.
- Do not describe mobile or simulator workflows as if they apply to macOS.
- If build output is large, summarize the first real blocker and name the follow-up command.
- Prefer SwiftPM over Xcode when both exist and the package path is clearly simpler.

## Output Expectations

For every build/run/test result, provide:

- The detected project type and entrypoint.
- The script path and Codex environment action configured, if applicable.
- The exact command run.
- Whether build, launch, or test succeeded.
- The top blocker if it failed, with the smallest useful error snippet.
- The next sensible action.

## References

- [`references/run-debug.md`](references/run-debug.md) — Shell-first build/run/debug workflows for macOS Xcode and SwiftPM projects. Load when creating or debugging `build_and_run.sh`, diagnosing launch failures, or choosing between Xcode and SwiftPM entrypoints.
- [`references/run-debug-run-button-bootstrap.md`](references/run-debug-run-button-bootstrap.md) — Canonical script shapes for CLI executables and SwiftPM GUI apps, plus the exact `.codex/environments/environment.toml` format. Load when writing or updating `script/build_and_run.sh` or the Codex environment file.
- [`references/swiftpm-macos.md`](references/swiftpm-macos.md) — SwiftPM-specific workflow for package-first repos with no Xcode project. Load when `Package.swift` is the primary entrypoint.
- [`references/test-triage.md`](references/test-triage.md) — Narrowing and classifying Xcode and SwiftPM test failures. Load when triaging assertion failures, crashes, flakes, or environment setup errors.
