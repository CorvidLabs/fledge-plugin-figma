---
id: CHG-0002-correct-figma-agent-argument-handling-and-plugin-contract-path-governance
state: accepted
type: bug_fix
base_commit: ce4c21c4256674609fcb02de4e0bf510c5197dae
---

# Correct Figma agent argument handling and plugin contract path governance

## Intent

Correct Figma agent argument handling and plugin contract path governance

## Affected Canonical Specs

- None

## Acceptance Criteria

- Claude
- Cursor
- and Gemini classify the complete post-flag input before choosing a module name; Gemini change creation uses its displayed raw arguments with one shell-escaping step; plugin.toml
- README.md
- and docs are meaningful lifecycle paths; native verification and strict SpecSync 100% coverage pass

## No-spec Rationale

These corrections affect generated contributor guidance and governance path coverage, not the Figma plugin runtime contract or behavior.
