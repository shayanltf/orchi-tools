# Web Source Inventory

Use when checking what was imported into the `web` plugin.

## Active Copied Source

- OpenAI official plugin examples: https://github.com/openai/plugins
- Source snapshot: `202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Imported source paths:
  - `plugins/build-web-apps/skills/frontend-app-builder`
  - `plugins/build-web-apps/skills/frontend-testing-debugging`
  - `plugins/build-web-apps/skills/react-best-practices`
  - `plugins/build-web-apps/skills/shadcn-best-practices`
- Source plugin manifests declare:
  - `author.name: OpenAI`
  - `repository: https://github.com/openai/plugins`
  - `license: MIT`
- `react-best-practices` preserves Vercel Engineering source metadata.

## Copy Decision

- Copy the four approved skill directories exactly for Codex.
- Copy the same source content for Claude while omitting Codex-only `agents/openai.yaml` files.
- Do not copy `stripe-best-practices`, `supabase-best-practices`, `supabase-postgres-best-practices`, or `build-web-data-visualization`.
- Attribute OpenAI and Vercel source metadata in README and research.
