# Skill Import Policy

Use before adding, renaming, or removing skills.

- Current copied source allowlist: `https://github.com/openai/plugins`.
- Current Apple source paths: `plugins/build-ios-apps`, `plugins/build-macos-apps`.
- Current Web source paths:
  - `plugins/build-web-apps/skills/frontend-app-builder`
  - `plugins/build-web-apps/skills/frontend-testing-debugging`
  - `plugins/build-web-apps/skills/react-best-practices`
  - `plugins/build-web-apps/skills/shadcn-best-practices`
- Do not copy `plugins/build-web-apps/skills/stripe-best-practices`, `plugins/build-web-apps/skills/supabase-postgres-best-practices`, or `plugins/build-web-apps/skills/build-web-data-visualization`.
- Keep each plugin's imported skills under that plugin root at `plugins/<plugin-name>/`.
- Preserve `SKILL.md`, `references/`, `scripts/`, assets, evals, metadata, and source support files that are part of the approved source directories.
- Preserve Codex `agents/openai.yaml` only in Codex skill trees under `plugins/<plugin-name>/skills/`.
- Omit Codex-only `agents/openai.yaml` from Claude skill trees under `plugins/<plugin-name>/claude/skills/`.
- Preserve supporting root files when skills require them: Apple keeps `.mcp.json`, `commands/`, and assets under `plugins/apple/`.
- Keep skill folder names purpose-scoped or source-surface-scoped.
- Remove unused source references from README, docs, research, and copied skill bodies when the import mode allows editing.
- Attribute OpenAI in README and research.
- Do not keep license files or attribution for sources not copied.
- Search for secrets, tokens, private repo names, private paths, and stale source names after import.
