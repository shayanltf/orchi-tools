# Workflow

Use this file when importing sources, grouping skills, packaging a runtime, or preparing a release. The practices are runtime-agnostic; apply them to every harness this repo serves.

## Source Policy

- Import skill content only from approved public sources. The current allowed source is OpenAI's official plugin examples at `https://github.com/openai/plugins` (`plugins/build-ios-apps`, `plugins/build-macos-apps`).
- Record the source repo, snapshot SHA, and imported paths in `research/`.
- Attribute the source in `README.md` and `research/`.
- Do not import from proprietary, unavailable, personal, or unapproved sources, and do not keep references to sources that are researched but not copied.

## Naming And Grouping

- One plugin, named `apple`. Skills group by purpose so users reach them as `apple:<group>` (for example `apple:swiftui`, `apple:macos`).
- Group by user workflow, not by source branding: `swiftui`, `ios`, `macos`, `build`, `performance`.
- Merge purely. Move each source skill into the grouped runtime skill as preserved guidance; do not rewrite its content.
- Do not prefix skill folder names with the plugin name.

## Skill Authoring

- `SKILL.md` is the skill, not an index. Its YAML frontmatter (`name`, `description`) controls when the harness loads it; its body is the working instruction set.
- Name by purpose and scope, not source branding.
- Keep one skill focused on one job.
- Preserve skill body content unless privacy, stale source refs, broken paths, packaging, or style rules require edits.
- Do not create archived source wrappers such as `source.md`.
- Use purpose-named references and scripts inside the runtime skill when progressive disclosure is needed.
- Reference supporting files from `SKILL.md` so the harness knows what each holds and when to load it.
- Add only the runtime-specific metadata each harness requires, and keep it out of the other harness's tree.

## Runtime Layout

Keep each runtime in its own plugin tree. Never share one skill tree across runtimes.

- Codex plugin files live under `codex/<plugin-name>/`.
- Claude plugin files live under the Claude runtime tree.
- Do not use root `skills/` as a shared runtime source.
- Duplicate skill content when both runtimes need the same guidance.
- Adapt paths, manifests, agents, commands, MCP config, and assets per runtime.
- Keep each runtime's `SKILL.md` files as active skills, not archived source wrappers.
- Use purpose-named references and scripts inside the runtime skill when progressive disclosure is needed.
- Record this separation when adapting future community skills.

## Docs Directory

`docs/INDEX.md` is the root context map. Every linked file gets one leaf line:

```md
- [File Title](path/file.md) - One line carrying 80% of the file's meaning.
```

- Link the exact path; keep the line short, specific, and task-routable.
- Update the leaf line when a file's meaning changes.
- Do not turn docs into task logs, and do not copy setup-context files from outside sources.

## Writing Style

Apply to `README.md`, `WORKFLOW.md`, `CLAUDE.md`, docs, and skill-facing instructions:

- Use imperative instructions: `Run`, `Configure`, `Install`.
- Use present tense: `This plugin provides`; avoid future tense.
- Use second person when addressing the reader: `Install the marketplace`.
- Use third person when describing the project: `Apple contains`.
- Use active voice: `Codex loads skills`, not `skills are loaded by Codex`.
- Use neutral technical language. Avoid marketing adjectives.

## Install Distribution

- Public install commands and marketplace plugin sources omit version refs; each runtime tracks the configured repository source.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Keep install guidance harness-first; do not make cloning the primary path.

## Release

- Plugin manifest name: `apple`.
- Display name: `Apple`.
- First release tag: `v0.1.0`.
- A release tag points at the reviewed release commit.
- Set a plugin's `version` in one place per runtime to avoid conflicting update signals.
- Tag must point at corrected release commit.
- If a tag was created before correction, move it only after corrected PR is ready and reviewed.
