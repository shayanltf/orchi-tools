# Release Review

Use before PR handoff, tag move, or merge.

- Validate Claude plugins from their scoped roots:
  - `claude --plugin-dir ./plugins/apple/claude`
  - `claude --plugin-dir ./plugins/web/claude`
- Validate Codex plugins with the plugin validator against each scoped plugin root:
  - `plugins/apple`
  - `plugins/web`
- Parse JSON manifests and marketplace catalogs.
- Validate `docs/INDEX.md` links.
- Confirm README attributes only active copied source: `https://github.com/openai/plugins`.
- Confirm research files mention only active source and official docs.
- Search hidden files for secrets, private source names, stale public source names, and local paths.
- Confirm root `CLAUDE.md` points to scoped plugin roots and no `CODEX.md` exists.
- Confirm marketplace install URLs and source entries omit version refs.
- Confirm `v0.1.0` tag points at the corrected release commit.
- Hand off to Review Squad for credential/personal leak review.
