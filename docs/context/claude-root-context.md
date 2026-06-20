# Claude Root Context

Use when deciding whether to create or edit root instruction files. This repo intentionally ships no root `CLAUDE.md`.

## Root File Rules

- Root context file stays short. Budget: project root under 200 lines, global root under 120 lines.
- Root file points to context leaves; it does not hold long paragraphs.
- Always-loaded root facts use explicit imports where runtime supports them.
- On-demand knowledge uses leaf line: link plus trigger sentence.
- If content needs a paragraph, move it to a context file.

## Scope Split

- Project scope: only useful in this repo.
- Global scope: useful across repos.
- Test: if another repo needs it tomorrow, global; otherwise project.
- Do not mirror project-specific content into global files.

## Editing Protocol

- Update leaf line when file moves or summary changes.
- Do not silently change plan directory settings.
- Do not create root instruction files for this plugin unless the plugin purpose changes.
- Plugin context loads through skills, agents, hooks, and manifests, not root `CLAUDE.md`.
