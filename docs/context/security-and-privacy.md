# Security And Privacy

Use before release, review, marketplace submission, or public handoff.

## Blockers

- No secrets.
- No API keys.
- No tokens.
- No credentials.
- No private repo names.
- No private paths.
- No personal infrastructure details.
- No local-only email, phone, address, account, or device identifiers.
- No hidden telemetry.
- No hook, monitor, MCP, or script that runs without clear user expectation.

## Review Steps

- Search repo for forbidden private source names and credential patterns.
- Inspect manifests for unexpected component paths.
- Inspect skills for personal references and one-off workspace instructions.
- Confirm no `CLAUDE.md` or `CODEX.md` was created here.
- Confirm docs mention public sources only.
- Confirm no external command runs on plugin load.
- Confirm release tag matches manifest version.

## If Found

- Remove secret immediately.
- Rotate credential outside repo if exposure happened.
- Replace private context with public or abstract wording.
- Re-run search before tag.
