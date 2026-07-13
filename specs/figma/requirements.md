---
spec: figma.spec.md
---

## User Stories

- As a frontend developer, I want to synchronize Figma styles and component metadata into project artifacts.
- As a reviewer, I want to compare current remote styles against a local baseline.

## Acceptance Criteria

### REQ-figma-001

The plugin SHALL initialize configuration without a token and refuse to overwrite an existing file.

Acceptance Criteria
- The offline install and remove hook smokes complete without a Figma token.
- Existing user configuration remains outside destructive lifecycle-hook behavior.

### REQ-figma-002

Live actions SHALL require a Figma token and SHALL never print it.

### REQ-figma-003

Token extraction SHALL support configured CSS, SCSS, Tailwind, and JSON outputs.

### REQ-figma-004

Component export and token diff SHALL write/read only configured project output paths and preserve the local baseline.

### REQ-figma-005

Removal guidance SHALL state that configuration and generated tokens remain intact.

## Constraints

- Live validation requires curl, jq/text tools, a valid Figma token, and API connectivity.

## Out of Scope

- Figma authentication provisioning, image export, and destructive remote mutations.
