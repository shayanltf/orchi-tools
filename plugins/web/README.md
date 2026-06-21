# Web

Web is an Orchi Tools plugin package for frontend web work in agent harnesses.

Maintained by the Orchi Team, with source published from `shayanltf/orchi-tools`.

## Install

Install from marketplace metadata. Do not clone this repo into every project.

### Codex

```bash
codex plugin marketplace add shayanltf/orchi-tools
```

Open the Codex app plugin directory, choose the `Orchi Tools` marketplace, then install or enable `Web`.

Use the scoped Codex skills:

```text
Use $frontend-app-builder to build a polished frontend.
Use $frontend-testing-debugging to verify this UI.
Use $react-best-practices to review React performance.
Use $shadcn to work with shadcn/ui components.
```

### Claude Code

```bash
claude plugin marketplace add shayanltf/orchi-tools
claude plugin install web@orchi-tools
```

Invoke the scoped skills by namespace:

```text
/web:frontend-app-builder
/web:frontend-testing-debugging
/web:react-best-practices
/web:shadcn
```

## Skill Library

- `frontend-app-builder` - Frontend app, dashboard, game, creative website, hero, redesign, and visual UI building.
- `frontend-testing-debugging` - Rendered frontend QA, local dev server validation, browser testing, console checks, screenshots, and interaction proof.
- `react-best-practices` - React and Next.js performance guidance from Vercel Engineering.
- `shadcn` - shadcn/ui component, registry, styling, composition, CLI, and project workflow guidance.

## Runtime Layout

Each runtime keeps its skills in its own folder:

- `skills/` contains the Codex skill surface. Codex requires this root path in `.codex-plugin/plugin.json`.
- `claude/skills/` contains the Claude skill surface. The Claude marketplace entry uses a `git-subdir` source pointing at `plugins/web/claude/`, so Claude loads only this folder and never the Codex root `skills/`.
- `claude/.claude-plugin/plugin.json` is the Claude plugin manifest.

## Source Attribution

Web imports selected skill directories from OpenAI's official plugin examples:

- Source repo: https://github.com/openai/plugins
- Imported paths:
  - `plugins/build-web-apps/skills/frontend-app-builder`
  - `plugins/build-web-apps/skills/frontend-testing-debugging`
  - `plugins/build-web-apps/skills/react-best-practices`
  - `plugins/build-web-apps/skills/shadcn-best-practices`
- Source snapshot used for this revision: `openai/plugins@202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Source plugin manifests declare `license: MIT` and `author: OpenAI`.
- React best practices preserve Vercel Engineering metadata from the source skill.

No Stripe, Supabase/Postgres, or web data visualization source content is copied into this plugin.
