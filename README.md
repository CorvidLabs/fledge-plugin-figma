# fledge-plugin-figma

Fledge plugin for syncing design tokens from Figma into your project.

## Install

```bash
fledge plugin install CorvidLabs/fledge-plugin-figma
```

## Usage

```bash
# Set your Figma personal access token
export FIGMA_TOKEN=your_token_here

# Create a config file
fledge figma init

# Sync design tokens from a Figma file
fledge figma sync <file-key>

# Extract just the tokens
fledge figma tokens <file-key>

# Export component specs
fledge figma export <file-key>

# Diff local tokens against current Figma state
fledge figma-diff <file-key>
```

The file key is in your Figma URL: `figma.com/file/<FILE_KEY>/...`

## Configuration

After running `fledge figma init`, edit `figma.toml`:

```toml
[figma]
file_key = "your-file-key"
output_dir = "tokens"
format = "css"  # css, scss, json, tailwind

[figma.tokens]
colors = true
typography = true
spacing = true

[figma.export]
format = "json"
output_dir = "specs"
```

## Output Formats

- **css** — CSS custom properties (`:root { --color-primary: ... }`)
- **scss** — Sass variables (`$color-primary: ...`)
- **tailwind** — Tailwind CSS theme extension (`tokens.tailwind.js`)
- **json** — Raw Figma style data

## Requirements

- `curl` and `jq` (for JSON processing)
- A [Figma personal access token](https://www.figma.com/developers/api#access-tokens)
