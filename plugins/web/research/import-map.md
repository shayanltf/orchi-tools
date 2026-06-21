# Web Import Map

Use when tracing Web plugin skill destinations to OpenAI source paths.

## From `plugins/build-web-apps/skills`

- `frontend-app-builder` <- `plugins/build-web-apps/skills/frontend-app-builder`
- `frontend-testing-debugging` <- `plugins/build-web-apps/skills/frontend-testing-debugging`
- `react-best-practices` <- `plugins/build-web-apps/skills/react-best-practices`
- `shadcn-best-practices` <- `plugins/build-web-apps/skills/shadcn-best-practices`

## Runtime Split

- Codex destinations live under `plugins/web/skills/<skill>`.
- Claude destinations live under `plugins/web/claude/skills/<skill>`.
- Claude copies omit Codex-only `agents/openai.yaml` files.
