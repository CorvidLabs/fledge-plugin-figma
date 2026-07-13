---
module: figma
version: 2
status: active
files:
  - bin/fledge-figma
  - bin/fledge-figma-diff
  - hooks/post-install.sh
  - hooks/post-remove.sh

db_tables: []
depends_on: []
---

# Figma

## Purpose

Initialize Figma sync configuration, retrieve file styles/components with token authentication, render token outputs in CSS/SCSS/Tailwind/JSON formats, compare remote styles with a local JSON baseline, and provide install/remove guidance hooks.

## Public API

| Action | Behavior |
|--------|----------|
| init | Create a documented `figma.toml` unless one already exists. |
| sync | Fetch the selected file, confirm identity, and generate configured tokens. |
| tokens | Fetch styles and write CSS, SCSS, Tailwind, or raw JSON output. |
| export | Fetch component metadata and write the configured JSON artifact. |
| diff | Compare current remote style JSON with the local token baseline. |
| lifecycle hooks | Print installation quick-start guidance and preserve user config/tokens on removal. |

## Invariants

1. Live Figma actions require `FIGMA_TOKEN`; help and init do not.
2. The token is sent only through the `X-Figma-Token` header and is never printed.
3. Init refuses to overwrite an existing configuration.
4. Explicit file keys win; configuration supplies a fallback.
5. Generated artifacts remain inside the configured output directories.
6. Removal does not delete user configuration or generated token files.
7. Diff uses a temporary remote snapshot and preserves the local baseline.

## Behavioral Examples

```
Given no token and no existing configuration
When init runs
Then it creates the default `figma.toml` without making a network request
```

## Error Cases

| Error | When | Behavior |
|-------|------|----------|
| Missing token | A live sync/tokens/export/diff action is requested | Report token setup guidance and exit non-zero. |
| Missing file key | Neither CLI nor config provides a key | Report usage and exit non-zero. |
| Figma request failure | API returns no usable response | Report fetch failure without exposing the token. |
| Unknown output format | Config format is unsupported | List supported formats and exit non-zero. |
| Missing local baseline | Diff has no token JSON | Direct the user to sync first and exit non-zero. |
| Existing config | Init would overwrite `figma.toml` | Refuse and exit non-zero. |

## Dependencies

- POSIX shell, curl, jq/standard text tools, and diff
- Figma REST API and personal access token for live operations
- fledge command and lifecycle-hook packaging

## Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1 | 2026-07-12 | Document existing Figma sync, export, diff, and hook behavior for SpecSync 5 adoption. |
| 2026-07-13 | CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-figma-fledge-plugin: Adopt SpecSync 5.0.1 and Trust 1.0.0 governance for the Figma Fledge plugin |
