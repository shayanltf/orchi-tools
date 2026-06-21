# Changelog

## Unreleased

- Re-scoped `orchi-tools` as a marketplace repository with independent plugin roots under `plugins/<plugin-name>/`.
- Moved the Apple plugin runtime files under `plugins/apple/` and updated marketplace entries to target that scoped plugin root.
- Added the Web plugin under `plugins/web/` for Codex and Claude Code.
- Copied the four approved OpenAI Build Web Apps skill directories into the Web plugin: `frontend-app-builder`, `frontend-testing-debugging`, `react-best-practices`, and `shadcn-best-practices`.
- Excluded Stripe, Supabase/Postgres, and web data visualization source content from the Web plugin.
- Updated Codex and Claude marketplace catalogs to publish both `apple` and `web` as available plugins.
- Aligned Codex plugin manifests with the official OpenAI plugin format: trimmed `interface.capabilities` to the supported `Interactive`, `Read`, and `Write` values, added top-level `homepage` and `repository` to the Apple manifest, and set `policy.products` to `["CODEX"]` in the Codex marketplace catalog.
- Added an install Troubleshooting note to `README.md` explaining the `URL rejected: Malformed input to a URL function` error and the exact `marketplace add` identifier to pass.

## [0.1.0] - 2026-06-20

- Added Apple Skills plugin manifests for Claude Code and Codex.
- Replaced the initial broad third-party import set with OpenAI-sourced Apple skills from `openai/plugins`.
- Added XcodeBuildMCP config, macOS helper commands, reusable docs context, and OpenAI-only research files.
- Kept marketplace install guidance harness-first with no version refs in public install commands.
