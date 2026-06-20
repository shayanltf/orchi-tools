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
- Merge purely. Move each source skill into the group as a preserved module; do not rewrite its content.
- Do not prefix skill folder names with the plugin name.

## Skill Authoring

- `SKILL.md` is the skill, not an index. Its YAML frontmatter (`name`, `description`) controls when the harness loads it; its body is the working instruction set.
- Preserve imported content. Keep each merged source skill under `references/modules/<module>/source.md` with its original `references/` and `scripts/`.
- Reference supporting files from `SKILL.md` so the harness knows what each holds and when to load it. Keep all referenced paths inside the skill folder.
- Add only the runtime-specific metadata each harness requires, and keep it out of the other harness's tree.

## Runtime Layout

Each runtime keeps its skills in its own folder. Never share one skill tree across runtimes.

- A runtime whose validator requires skills at the repository root uses root `skills/` (currently Codex, via `.codex-plugin/plugin.json`).
- A second runtime uses its own subdirectory and a subdirectory-scoped install source so its plugin root is that subdirectory (currently Claude, via `claude/` and a `git-subdir` marketplace source). This isolates it from the root `skills/` tree.
- Keep each runtime's manifest with its plugin root and its marketplace catalog where that runtime expects it.
- Keep per-runtime notes in the runtime's folder (`claude/`, `codex/`).

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
- Use present tense; avoid future tense.
- Use second person for the reader, third person for the project.
- Use active voice and neutral technical language; avoid marketing adjectives.

## Install Distribution

- Public install commands and marketplace plugin sources omit version refs; each runtime tracks the configured repository source.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Keep install guidance harness-first; do not make cloning the primary path.

## Release

- Plugin name `apple`; first release tag `v0.1.0`.
- A release tag points at the reviewed release commit.
- Set a plugin's `version` in one place per runtime to avoid conflicting update signals.
