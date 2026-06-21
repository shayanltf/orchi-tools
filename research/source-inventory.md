# Source Inventory

Use when checking what was imported.

## Active Copied Source

- OpenAI official plugin examples: https://github.com/openai/plugins
- Source snapshot: `202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare:
  - `author.name: OpenAI`
  - `repository: https://github.com/openai/plugins`
  - `license: MIT`

## Apple Source

- Imported source paths:
  - `plugins/build-ios-apps`
  - `plugins/build-macos-apps`
- iOS/macOS plugin work credited to Thomas Ricouard (Dimillian): https://github.com/Dimillian, https://x.com/Dimillian

## Apple Copy Decision

- Copy OpenAI Apple-related skill directories.
- Copy root support files needed by those skills: `.mcp.json`, `commands/`, assets.
- Scope Apple runtime files under `plugins/apple/`.
- Attribute OpenAI and Thomas Ricouard (Dimillian) in README.

## Web Source

- Imported source paths:
  - `plugins/build-web-apps/skills/frontend-app-builder`
  - `plugins/build-web-apps/skills/frontend-testing-debugging`
  - `plugins/build-web-apps/skills/react-best-practices`
  - `plugins/build-web-apps/skills/shadcn-best-practices`
- React best practices preserve Vercel Engineering metadata from the source skill.

## Web Copy Decision

- Copy only the four approved OpenAI Build Web Apps skill directories.
- Preserve each Web source skill surface as a distinct skill directory.
- Scope Web runtime files under `plugins/web/`.
- Keep Codex `agents/openai.yaml` in `plugins/web/skills/`.
- Omit Codex-only `agents/openai.yaml` from `plugins/web/claude/skills/`.
- Exclude `plugins/build-web-apps/skills/stripe-best-practices`, `plugins/build-web-apps/skills/supabase-postgres-best-practices`, and `plugins/build-web-apps/skills/build-web-data-visualization`.

## Cleanup Rule

- Do not keep researched-but-unused public sources in repo docs.
