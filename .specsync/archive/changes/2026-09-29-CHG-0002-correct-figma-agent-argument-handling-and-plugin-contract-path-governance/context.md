---
change: CHG-0002-correct-figma-agent-argument-handling-and-plugin-contract-path-governance
artifact: context
---

# Context

The generated create-spec guidance selected the first whitespace-delimited word as the module name before deciding
whether the user supplied a bare identifier or a natural-language description. A request such as “I want CSV
export” could therefore scaffold module `I`. Gemini change creation also displayed `{{args}}` but instructed the
agent to execute the unrelated `$ARGUMENTS` shell variable.

The SDD meaningful-path policy omitted `plugin.toml`, `README.md`, and `docs/`, allowing public command or
documentation changes to bypass the lifecycle. This correction fixes all three agent command variants and brings
the plugin contract/documentation paths under governance without changing runtime behavior.
