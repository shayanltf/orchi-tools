# Skill Import Policy

Use before adding, renaming, or removing skills.

- Current copied source allowlist: `https://github.com/openai/plugins`.
- Current source paths: `plugins/build-ios-apps`, `plugins/build-macos-apps`.
- Import Apple-related skill directories only.
- Preserve `SKILL.md`, `references/`, `scripts/`, and `agents/openai.yaml`.
- Preserve supporting runtime files when skills require them: MCP config, `commands/`, assets.
- Keep skill folder names purpose-scoped.
- Remove unused source references from README, docs, research, and copied skill bodies.
- Attribute OpenAI in README and research.
- Do not keep license files or attribution for sources not copied.
- Search for secrets, tokens, private repo names, private paths, and stale source names after import.
