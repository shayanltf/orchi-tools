# Claude Agents

Use when authoring or reviewing Claude Code subagents.

## Core Rules

- One agent = one job. If scope names two jobs, split.
- `description` routes. Third person. Specific trigger. Name exclusions.
- Body is system prompt. No slash-command `!` or `@` magic inside agent body.
- Use `tools`, not `allowed-tools`, for subagent allowlists.
- Add MCP tools by full name when `tools` is explicit: `mcp__server__tool`.
- Use `mcpServers` only for servers not already configured in parent session.
- Restrict read-only agents: no `Write`, no `Edit`, no state change.
- Pick model by difficulty: Haiku simple/high-volume, Sonnet normal, Opus hard/high-risk.
- Subagents cannot spawn subagents. Parent orchestrator chains work.
- Plugin agents appear in `/agents`; plugin namespacing prevents collisions.

## Memory

- Prefer memory MCP: search first, add durable reusable facts at finish.
- Use family `user_id` for tiered ladders: `coder`, `researcher`, similar.
- Never store secrets, credentials, tokens, private values, or one-run logs.
- If MCP memory is down, hand back reusable cross-project pattern to parent.

## Handoff

- Implementation agents derive checks, run available checks, and name gaps.
- Review agents stay read-only unless explicitly assigned to patch.
- Security findings need severity, evidence, affected path, and remediation.
- Reports can be compressed; code, docs, configs, and commit messages stay normal prose.
