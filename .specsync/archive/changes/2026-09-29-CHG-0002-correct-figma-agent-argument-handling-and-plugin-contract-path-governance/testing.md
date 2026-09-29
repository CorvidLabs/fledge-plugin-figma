---
change: CHG-0002-correct-figma-agent-argument-handling-and-plugin-contract-path-governance
artifact: testing
---

# Testing

- Inspect Claude, Cursor, and Gemini create-spec guidance with a bare module name, a multi-word feature request,
  and either form containing `--minimal`; module selection must occur only after flag removal and full-input
  classification.
- Confirm Gemini change creation uses the displayed raw arguments and one shell-escaping step.
- Run the repository Fledge verification lane and strict SpecSync at 100% file and LOC coverage.
- Confirm `plugin.toml`, `README.md`, and `docs/` are committed meaningful paths.
