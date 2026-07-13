---
spec: figma.spec.md
---

## Context

This POSIX-shell plugin provides a small design-token bridge without adding a language runtime dependency.

## Related Modules

- Figma REST API
- fledge command and lifecycle hooks

## Design Decisions

- Keep live API calls token-header authenticated and migration tests offline.
- Preserve generated/user files on plugin removal.
