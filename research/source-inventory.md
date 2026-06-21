# Source Inventory

Use when checking what was imported.

## Active Copied Source

- OpenAI official plugin examples: https://github.com/openai/plugins
- Source snapshot: `202e9242b1084e30d44cea8f553c2bdb5dcc75c9`
- Imported source paths:
  - `plugins/build-ios-apps`
  - `plugins/build-macos-apps`
- Source plugin manifests declare:
  - `author.name: OpenAI`
  - `repository: https://github.com/openai/plugins`
  - `license: MIT`
- iOS/macOS plugin work credited to Thomas Ricouard (Dimillian): https://github.com/Dimillian, https://x.com/Dimillian

## Copy Decision

- Copy OpenAI Apple-related skill directories.
- Copy root support files needed by those skills: `.mcp.json`, `commands/`, assets.
- Attribute OpenAI and Thomas Ricouard (Dimillian) in README.
- Do not keep researched-but-unused public sources in repo docs.

## Catalog-Only Entries

- `web` is reserved in the Codex marketplace with `installation: NOT_AVAILABLE`.
- No `web` source content is copied into this repository.
- Do not add `web` source attribution here until source files are actually imported into a plugin repository.
