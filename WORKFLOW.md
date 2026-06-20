# Workflow

Use this file when managing source imports, `docs/`, `research/`, releases, or future skill updates.

## Source Rule

Current allowed copied source: OpenAI official plugin examples only.

- Import Apple-related skills from `https://github.com/openai/plugins`.
- Use `plugins/build-ios-apps` and `plugins/build-macos-apps` for the current library.
- Preserve OpenAI skill structure: `SKILL.md`, `references/`, `scripts/`, `agents/openai.yaml`.
- Preserve helper plugin surfaces when they support copied skills: `.mcp.json`, `commands/`, and required assets.
- Attribute OpenAI in README and research.
- Remove stale source refs from README, docs, research, and skill bodies.
- Do not keep references to researched-but-unused sources.
- Do not copy content from proprietary, unavailable, personal, or unapproved sources.

## Naming And Grouping

Cloning alone is not enough. Import source skills, then curate access:

- Name by purpose and scope, not source branding.
- Keep one skill focused on one job.
- Group by user workflow: iOS, macOS, shared SwiftUI where applicable.
- Do not prefix skill names with `apple-skills`.
- Preserve skill body content unless privacy, stale source refs, broken paths, packaging, or style rules require edits.

## Docs Directory

`docs/INDEX.md` is the root context map.

Every linked docs/context or research file needs one leaf line:

```md
- [File Title](path/file.md) - One line carrying 80% of file meaning.
```

Rules:

- Link exact file path.
- Keep line short, specific, task-routable.
- Update leaf line when file meaning changes.
- Do not turn docs into task logs.
- Do not copy setup-context files from outside sources.

## Writing Style

Apply to README, WORKFLOW, docs, and skill-facing instructions where edits are necessary:

- Use imperative instructions: `Run`, `Configure`, `Install`.
- Use present tense: `This plugin provides`; avoid future tense.
- Use second person when addressing the reader: `Install the marketplace`.
- Use third person when describing the project: `Apple Skills contains`.
- Use active voice: `Codex loads skills`, not `skills are loaded by Codex`.
- Use neutral technical language. Avoid marketing adjectives.

## Install Distribution

- Public install commands omit version refs.
- Marketplace plugin sources omit version refs.
- Claude Code and Codex track marketplace sources from the configured repository.
- Use explicit refs only for release validation, frozen installs, or rollback testing.
- Keep README install guidance harness-first; do not make project cloning the primary path.

## `docs/context/`

Use for reusable repo context future agents should load again.

Admit only:

- Repo rules.
- Current source policy.
- Plugin packaging guidance.
- Skill navigation guidance.
- Docs/research rules.
- Validation and release guardrails.

Reject:

- One-run notes.
- Long source dumps.
- Private source names.
- Researched-but-unused public source lists.
- Anything better stored in README, WORKFLOW, or research.

Write caveman-compressed: fewer words, no filler, exact identifiers stay.

## `research/`

Use for durable source and official-docs findings that belong to this repo.

Admit only:

- Active source inventory.
- Import map from active source paths to repo paths.
- Official docs map for plugin runtimes and Apple scopes.
- Long-term findings worth re-reading.

Reject:

- Raw browsing noise.
- Temporary command output.
- Unverified claims.
- Unused source lists.
- Private source names.

Write caveman-compressed. Preserve exact links.

## Squads

- Planning Squad: source evaluation, scope map, import decision, docs/research policy.
- Implementation Squad: skill import, grouping, manifests, repo structure.
- Review Squad: credential scan, personal leak scan, license risk, source isolation.

Do not merge until review checks copied skill content, README attribution, manifests, `docs/`, `research/`, and tag/version alignment.

## Release

- Plugin manifest name: `apple-skills`.
- Display name: `Apple Skills`.
- First release tag: `v0.1.0`.
- Tag must point at corrected release commit.
- If a tag was created before correction, move it only after corrected PR is ready and reviewed.
