# Codex Agents

Use when authoring or porting Codex custom agents.

## TOML Shape

- Location: `~/.codex/agents/` for personal; `.codex/agents/` for project.
- Required: `name`, `description`, `developer_instructions`.
- Optional: `model`, `model_reasoning_effort`, `sandbox_mode`, `mcp_servers`, `skills.config`.
- `description` routes parent Codex session; keep narrow and opinionated.
- `developer_instructions` carries behavior, boundaries, output shape, escalation.
- Do not copy Claude-only fields: `tools`, `permissionMode`, `maxTurns`, native `skills`, local memory metadata.

## Model Map

- Opus-style hard reasoning: `gpt-5.5`, `xhigh`.
- Sonnet-style balanced work: `gpt-5.4`, `xhigh`.
- Haiku-style simple fast work: `gpt-5.3-codex-spark`, `high`.

## MCP And Memory

- Non-global MCP servers use TOML tables: `[mcp_servers.name]`.
- Do not declare global `memory` MCP per agent; inherit global OAuth-configured server.
- Search memory each turn, persist only durable reusable facts at finish.
- If memory MCP is down, hand back a cross-project-safe pattern to parent.
- Never hand back secrets, credentials, private paths, tokens, or one-off logs.

## Porting

- Replace Claude tool names with Codex-native wording: inspect files, edit files, run shell commands, use subagents.
- Preserve capability when removing tool names.
- Validate TOML after changes.
- Smoke-test agent loading before release when Codex CLI is available.
