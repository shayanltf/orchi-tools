# Codex Rules

Use when deciding where Codex guidance belongs.

## Three Surfaces

- `AGENTS.md`: always-loaded Markdown guidance.
- Native memories: recall layer for useful prior patterns.
- Execpolicy `.rules`: command approval and sandbox policy.

## AGENTS.md

- Global: `~/.codex/AGENTS.md`.
- Global override: `~/.codex/AGENTS.override.md`.
- Project: `AGENTS.md` or `AGENTS.override.md` in root or nested directories.
- Codex builds instruction chain from broad to nearest directory.
- Nearest file can override broader guidance.
- Keep global always-on rules concise.
- Large guidance belongs in checked-in docs plus explicit read triggers.

## Memories

- Use memories for helpful recall, not hard policy.
- Do not manually edit generated memories as primary control surface.
- Rules that must always apply belong in `AGENTS.md` or checked-in docs.

## Execpolicy

- `.rules` files are not Markdown guidance.
- Use them for allow, deny, or require-approval decisions on shell commands.
- Verify policy with `codex execpolicy check` when available.
- Never replace project instructions with execpolicy.
