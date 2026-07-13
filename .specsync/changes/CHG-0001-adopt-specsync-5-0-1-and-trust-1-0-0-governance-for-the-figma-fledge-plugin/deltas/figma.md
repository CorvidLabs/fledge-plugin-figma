## MODIFIED

### REQUIREMENT REQ-figma-001

The plugin SHALL initialize configuration without a token and refuse to overwrite an existing file.

Acceptance Criteria
- The offline install and remove hook smokes complete without a Figma token.
- Existing user configuration remains outside destructive lifecycle-hook behavior.
