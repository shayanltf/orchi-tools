# Release Review

Use before PR handoff, tag move, or merge.

- Validate Claude plugin: `claude plugin validate . --strict`.
- Validate Codex plugin: plugin validator against repo root.
- Parse JSON manifests.
- Validate `docs/INDEX.md` links.
- Confirm README attributes only active copied source: `https://github.com/openai/plugins`.
- Confirm research files mention only active source and official docs.
- Search hidden files for secrets, private source names, stale public source names, and local paths.
- Confirm no `CLAUDE.md` or `CODEX.md`.
- Confirm marketplace install URLs and source entries omit version refs.
- Confirm `v0.1.0` tag points at corrected release commit.
- Hand off to Review Squad for credential/personal leak review.
