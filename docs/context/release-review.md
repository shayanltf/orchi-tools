# Release Review

Use before PR handoff, tag move, or merge.

- Validate Claude plugin: `claude plugin validate . --strict`.
- Validate Codex plugin: plugin validator against repo root.
- Parse JSON manifests.
- Validate `docs/INDEX.md` links.
- Confirm all copied source licenses exist in `licenses/`.
- Search hidden files for secrets and private source names.
- Confirm only README has source refs/mentions/attribution.
- Confirm no `CLAUDE.md` or `CODEX.md`.
- Confirm `v0.1.0` tag points at corrected release commit.
- Hand off to Review Squad for credential/personal leak review.
