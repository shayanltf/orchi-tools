# Workflow

Use this file when managing imports, `docs/`, `research/`, releases, or future skill updates.

## Import Rule

Cloning alone is not enough. Clone/import source skills, then curate:

- New name by purpose/scope, not source branding.
- Clear boundary: one skill, one job.
- Group/order by user workflow: SwiftUI, Swift language/tests/persistence, build/debug/release.
- Preserve useful skill body content. Change packaging/frontmatter only when needed for clean access, privacy, license, or folder-name alignment.
- Move source refs, mentions, author attribution, and license notes to `README.md` and `licenses/`.
- Never import content from proprietary or unlicensed sources; keep those as research references only.

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
- Do not copy every setup-context file from outside sources.

## `docs/context/`

Use for reusable high-fidelity context future agents should load again.

Admit only:

- Stable best practices.
- Repo rules.
- Skill import policy.
- Plugin packaging guidance.
- Library navigation guidance.
- Privacy/license/release guardrails.

Reject:

- One-run notes.
- Long source dumps.
- Private source names.
- Scratch research.
- Anything better stored in README, WORKFLOW, or research.

Write caveman-compressed: fewer words, no filler, exact identifiers stay.

## `research/`

Use for durable long-term research findings from internet, public repos, official docs, and squad research.

Admit only:

- Source inventory.
- License/copy decision.
- Import map.
- Official docs map.
- Long-term findings worth re-reading.

Reject:

- Raw browsing noise.
- Temporary command output.
- Unverified claims.
- Private source names.

Write caveman-compressed. Preserve exact links.

## Squads

- Planning Squad: source evaluation, scope map, import decision, docs/research policy.
- Implementation Squad: skill import, naming, grouping, manifests, repo structure.
- Review Squad: credential scan, personal leak scan, license risk, public-source isolation.

Do not merge until review checks copied skill content, README attribution, manifests, `docs/`, `research/`, and tag/version alignment.

## Release

- Plugin manifest name: `apple-skills`.
- Display name: `Apple Skills`.
- First release tag: `v0.1.0`.
- Tag must point at corrected release commit.
- If a tag was created before correction, move it only after corrected PR is ready and reviewed.
