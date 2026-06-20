---
name: apple-one-context
description: Use when building, porting, or reviewing Apple One Skills context across Codex and Claude Code plugin, skill, agent, workflow, docs, and Apple-platform work.
version: 0.1.0
author: Apple One Skills contributors
license: MIT
---

## Usage

Read `docs/INDEX.md` at plugin root first. If inspecting from this skill directory, use `../../docs/INDEX.md`.

Load only task-relevant leaves:

- Apple-platform coverage: `docs/context/apple-skill-research.md`
- Codex agents: `docs/context/codex-agents.md`
- Codex skills: `docs/context/codex-skills.md`
- Codex rules: `docs/context/codex-rules.md`
- Codex workflows: `docs/context/codex-workflows.md`
- Claude interop: `docs/context/claude-agents.md`, `docs/context/claude-skills.md`, `docs/context/claude-commands.md`, `docs/context/claude-root-context.md`
- Non-code docs: `docs/context/docs-output.md`
- Voice/reporting: `docs/context/voice-and-reporting.md`
- Release review: `docs/context/security-and-privacy.md`
- Source check: `docs/context/source-map.md`

Keep response compact. Preserve exact identifiers, file paths, manifest fields, and runtime-specific vocabulary.
