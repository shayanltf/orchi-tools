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
- Each group is one first-class skill, not a container of nested old skills.
- Do not prefix skill folder names with the plugin name.

## Skill Authoring

- `SKILL.md` is the skill, not an index. Its YAML frontmatter (`name`, `description`) controls when the harness loads it; its body is a real working skill — domain overview, "use when" guidance, and a merged decision/workflow across the group's sub-areas.
- Lay content directly in the skill: `SKILL.md` at the skill root, detail in flat, topic-named files under `references/`, executables under `scripts/`. Do not create inert wrapper files (no `source.md`) and do not nest old skills under `references/modules/`.
- Preserve imported content when moving it into a group: relocate reference and script files verbatim; the only allowed edits are fixing broken relative paths. Compose the `SKILL.md` body by faithfully merging the source guidance — do not invent facts.
- Reference supporting files from `SKILL.md` so the harness knows what each holds and when to load it. Keep all referenced paths inside the skill folder; route cross-skill needs by skill name, not by reaching into another skill's files.
- Add only the runtime-specific metadata each harness requires (for example Codex `agents/openai.yaml`), and keep it out of the other harness's tree.

## Runtime Layout

Each runtime keeps its skills in its own folder. Never share one skill tree across runtimes.

- A runtime whose validator requires skills at the repository root uses root `skills/` (currently Codex, via `.codex-plugin/plugin.json`).
- A second runtime uses its own subdirectory and a subdirectory-scoped install source so its plugin root is that subdirectory (currently Claude, via `claude/` and a `git-subdir` marketplace source). This isolates it from the root `skills/` tree.
- Keep each runtime's manifest with its plugin root and its marketplace catalog where that runtime expects it.
- Keep per-runtime notes in the runtime's folder (`claude/`, `codex/`).

## Community Skill Adaptation

Follow this process whenever you adopt or adapt a skill from the community.

1. Vet the source. Confirm the license permits reuse and the source is approved (see Source Policy). Record the source, snapshot, and paths in `research/`; attribute it in `README.md`.
2. Decide the group. Map the community skill to one purpose group by what the user does with it, not by its original name or branding.
3. Adapt it as a first-class skill (see Skill Authoring). Merge the community content into the group's `SKILL.md` and flat topic references. Do not keep it as a nested archive of the original skill and do not add inert wrapper files. Relocate reference and script content verbatim; fix only broken paths.
4. Duplicate per runtime. Each runtime gets its own copy under its own tree (see Runtime Layout). Identical content across runtimes is expected and acceptable — the separation is required because each platform has its own layout and validator rules. Never point two runtimes at one shared root skill tree.
5. Strip personal and source-specific noise: private names, local paths, and references to sources researched but not copied.
6. Verify per runtime: run each runtime's validator or structure check, confirm `SKILL.md` frontmatter, confirm every referenced path resolves inside the skill, and confirm no inert `source.md` or `references/modules/` artifacts remain.

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
