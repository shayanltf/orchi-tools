# Skill Import Policy

Use before adding, renaming, or removing skills.

- Current copied source allowlist: `https://github.com/openai/plugins`.
- Current source paths: `plugins/build-ios-apps`, `plugins/build-macos-apps`.
- Import Apple-related skill directories only.
- The reserved `web` catalog entry does not authorize copying web skill content into this repository.
- Preserve `SKILL.md`, `references/`, `scripts/`, and `agents/openai.yaml`.
- Preserve supporting root files when skills require them: `.mcp.json`, `commands/`, assets.
- Keep skill folder names purpose-scoped.
- Remove unused source references from README, docs, research, and copied skill bodies.
- Attribute OpenAI in README and research.
- Do not keep license files or attribution for sources not copied.
- Search for secrets, tokens, private repo names, private paths, and stale source names after import.
