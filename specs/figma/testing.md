---
spec: figma.spec.md
---

## Test Plan

### Integration Tests

- `shellcheck bin/* hooks/*`
- `bin/fledge-figma help`
- Run install/remove hooks and verify no user files are deleted.
- Live Figma sync/export/diff remains an independently credentialed integration.
