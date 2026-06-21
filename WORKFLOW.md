# Workflow

Use this file when importing sources, grouping skills, packaging a runtime, or preparing a release. The practices are runtime-agnostic; apply them to every plugin this marketplace serves.

## Source Policy

- Import skill content only from approved public sources. The current copied source is OpenAI's official plugin examples at `https://github.com/openai/plugins`.
- Record the source repo, snapshot SHA, and imported paths in `research/`. A plugin may also keep scoped source notes under `plugins/<plugin-name>/research/`.
- Attribute the source in `README.md` and `research/`.
- Do not import from proprietary, unavailable, personal, or unapproved sources, and do not keep references to sources that are researched but not copied.
- The current active copied sources are:
  - Apple: `plugins/build-ios-apps` and `plugins/build-macos-apps`.
  - Web: `plugins/build-web-apps/skills/frontend-app-builder`, `plugins/build-web-apps/skills/frontend-testing-debugging`, `plugins/build-web-apps/skills/react-best-practices`, and `plugins/build-web-apps/skills/shadcn-best-practices`.
- The Web plugin excludes `stripe-best-practices`, `supabase-postgres-best-practices`, and `build-web-data-visualization`.

## Marketplace And Plugin Scope

- `orchi-tools` is a marketplace repository. Each plugin owns one scoped root at `plugins/<plugin-name>/`.
- Active plugins:
  - `apple` - Apple ecosystem skills for Codex and Claude Code.
  - `web` - Frontend web skills for Codex and Claude Code.
- Keep plugin work inside that plugin's root unless the change is marketplace-wide documentation, catalog metadata, or release coordination.
- Do not place one plugin's skills, runtime files, assets, or support commands under another plugin's root.
- Do not prefix skill folder names with the plugin name.

## Naming And Grouping

- Group by user workflow, not by source branding, unless a source skill must remain exact.
- Apple groups related OpenAI iOS and macOS source skills into first-class purpose skills: `swiftui`, `ios`, `macos`, `build`, and `performance`.
- Web keeps the four approved OpenAI source skill surfaces distinct: `frontend-app-builder`, `frontend-testing-debugging`, `react-best-practices`, and `shadcn-best-practices` with source frontmatter preserved.
- A grouped plugin may compose a `SKILL.md` from approved source guidance. An exact-copy plugin must preserve the source skill directory content and only add packaging files around it.

## Skill Authoring

- `SKILL.md` is the skill, not an index. Its YAML frontmatter (`name`, `description`) controls when the harness loads it; its body is a real working skill.
- Lay content directly in the skill: `SKILL.md` at the skill root, detail in flat, topic-named files under `references/`, executables under `scripts/`.
- Preserve imported content according to that plugin's import mode:
  - For grouped imports, relocate reference and script files verbatim; the only allowed edits are fixing broken relative paths. Compose the `SKILL.md` body by faithfully merging the source guidance.
  - For exact-copy imports, copy the source skill directory exactly and do not rewrite, summarize, blend, or blind-merge the skill content.
- Reference supporting files from `SKILL.md` so the harness knows what each holds and when to load it. Keep all referenced paths inside the skill folder; route cross-skill needs by skill name, not by reaching into another skill's files.
- Add only the runtime-specific metadata each harness requires. Codex keeps `agents/openai.yaml`; Claude runtime trees omit Codex-only `agents/openai.yaml`.

## Runtime Layout

Each plugin keeps each runtime in that plugin's scoped root. Never share one skill tree across runtimes.

- Codex plugin root: `plugins/<plugin-name>/`.
- Codex manifest: `plugins/<plugin-name>/.codex-plugin/plugin.json`.
- Codex skills: `plugins/<plugin-name>/skills/`.
- Claude plugin root: `plugins/<plugin-name>/claude/`.
- Claude manifest: `plugins/<plugin-name>/claude/.claude-plugin/plugin.json`.
- Claude skills: `plugins/<plugin-name>/claude/skills/`.
- Codex marketplace catalog: `.agents/plugins/marketplace.json`, with each entry using `source.path: ./plugins/<plugin-name>`.
- Claude marketplace catalog: `.claude-plugin/marketplace.json`, with each entry using `git-subdir` and `path: plugins/<plugin-name>/claude`.
- Keep per-runtime notes in that runtime's folder, for example `plugins/apple/codex/` and `plugins/apple/claude/`.

## Community Skill Adaptation

Follow this process whenever you adopt or adapt a skill from the community.

1. Vet the source. Confirm the license permits reuse and the source is approved (see Source Policy). Record the source, snapshot, and paths in `research/`; attribute it in `README.md`.
2. Decide the plugin. Use an existing `plugins/<plugin-name>/` root when the source belongs to that plugin's scope. Create a new plugin root when it is a distinct product surface.
3. Decide the import mode. Use grouped adaptation only when the plugin's approved structure calls for it. Use exact-copy import when the source skill must stay distinct.
4. Duplicate per runtime. Each runtime gets its own copy under its own tree (see Runtime Layout). Identical content across runtimes is expected and acceptable because each platform has its own layout and validator rules.
5. Strip personal and source-specific noise only when adaptation mode allows it. Do not alter exact-copy skill content except where layout validation requires a structural wrapper.
6. Verify per runtime: run each runtime's validator or structure check, confirm `SKILL.md` frontmatter, confirm every referenced path resolves inside the skill, and confirm runtime-only files stay in the right runtime tree.

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

- Active plugin names: `apple`, `web`.
- First release tag: `v0.1.0`.
- A release tag points at the reviewed release commit.
- Set a plugin's `version` in one place per runtime to avoid conflicting update signals.
