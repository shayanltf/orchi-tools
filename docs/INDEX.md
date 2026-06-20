# Apple One Skills Index

## Runtime

- [README](../README.md) - Project purpose, structure, local Claude load path, Codex entry note, and release line.
- [Claude manifest](../.claude-plugin/plugin.json) - Claude Code plugin identity, version, metadata, and `./claude/skills/` component path.
- [Codex manifest](../.codex-plugin/plugin.json) - Codex plugin identity, version, UI metadata, and default `./skills/` component path.
- [Claude skill entry](../claude/skills/apple-one-context/SKILL.md) - Claude invocation surface that tells agents to read this index, then load only relevant context leaves.
- [Codex skill entry](../skills/apple-one-context/SKILL.md) - Codex invocation surface that maps the same context pack into Codex wording and file paths.

## Context

- [Apple Skill Research](context/apple-skill-research.md) - Public Apple-platform skill inventory distilled into coverage decisions: SwiftUI, concurrency, testing, persistence, Xcode, simulator, signing, performance.
- [Claude Agents](context/claude-agents.md) - Claude subagent design contract: one job, routing description, tool limits, model tier, memory, and handoff boundaries.
- [Claude Skills](context/claude-skills.md) - Claude skill authoring contract: focused `SKILL.md`, concise frontmatter, supporting files, invocation control, and plugin namespace rules.
- [Claude Commands](context/claude-commands.md) - Claude command migration contract: commands as ordered prompts, skills as reusable knowledge, dynamic context only where runtime supports it.
- [Claude Root Context](context/claude-root-context.md) - CLAUDE.md guidance without creating one here: keep roots short, link context leaves, never bury paragraphs in root files.
- [Codex Agents](context/codex-agents.md) - Codex custom-agent TOML contract: narrow description, developer instructions, model mapping, sandbox, MCP, and memory handback rules.
- [Codex Skills](context/codex-skills.md) - Codex skill contract: progressive disclosure, `SKILL.md` shape, references/scripts split, and Claude-to-Codex vocabulary translation.
- [Codex Rules](context/codex-rules.md) - Codex rule-surface split: `AGENTS.md` for guidance, memories for recall, execpolicy `.rules` for command approval policy.
- [Codex Workflows](context/codex-workflows.md) - Codex workflow migration map: slash-command behavior becomes skill workflow, plan/checklist, subagent fan-out, and HITL review.
- [Docs Output](context/docs-output.md) - Non-code document output contract: finished file only, no change-story prose, no inline diff narration.
- [Voice And Reporting](context/voice-and-reporting.md) - Cross-surface voice and reporting matrix: runtime self-instructions, human docs, chat output, and compressed agent reports.
- [Security And Privacy](context/security-and-privacy.md) - Release review checklist: no secrets, credentials, private repo names, personal data, telemetry surprises, or source-leak residue.
- [Source Map](context/source-map.md) - Public sources used for this isolated plugin: official Claude Code docs, OpenAI Codex docs, and public Apple-platform skill repositories.
