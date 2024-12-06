# MCP Obsidian

Model Context Protocol server for Obsidian vault integration. This allows Claude Desktop (or any MCP client) to search and read your Obsidian notes.

## Quick Start (For Users)

### Prerequisites
- Node.js 18+ (install via `brew install node`)
- Obsidian vault
- Claude Desktop (install from https://claude.ai/desktop)

### Configuration

1. Open your Claude Desktop configuration file at:
`~/Library/Application Support/Claude/claude_desktop_config.json`

You can find this through the Claude Desktop menu:
1. Open Claude Desktop
2. Click Claude on the Mac menu bar
3. Click "Settings"
4. Click "Developer"

2. Add the following to your configuration:

```json
{
  "tools": {
    "obsidian": {
      "command": "npx",
      "args": ["-y", "@kazuph/mcp-obsidian"],
      "env": {
        "OBSIDIAN_VAULT_PATH": "/path/to/your/obsidian/vault"
      }
    }
  }
}
```

Note: Replace `/path/to/your/obsidian/vault` with your actual Obsidian vault path.

## For Developers

### Prerequisites
- Node.js 18+ (install via `brew install node`)
- Obsidian vault
- Claude Desktop (install from https://claude.ai/desktop)
- tsx (install via `npm install -g tsx`)

## Installation

```bash
git clone https://github.com/kazuph/mcp-obsidian.git
cd mcp-obsidian
npm install
npm run build
```

## Configuration

1. Make sure Claude Desktop is installed and running.

2. Install tsx globally if you haven't:
```bash
npm install -g tsx
# or
pnpm add -g tsx
```

3. Modify your Claude Desktop config located at:
`~/Library/Application Support/Claude/claude_desktop_config.json`

You can easily find this through the Claude Desktop menu:
1. Open Claude Desktop
2. Click Claude on the Mac menu bar
3. Click "Settings"
4. Click "Developer"

Add the following to your MCP client's configuration:

```json
{
  "tools": {
    "obsidian": {
      "args": ["tsx", "/path/to/mcp-obsidian/index.ts"],
      "env": {
        "OBSIDIAN_VAULT_PATH": "/path/to/your/obsidian/vault"
      }
    }
  }
}
```

## Available Tools

- `obsidian_read_notes`: Read the contents of multiple notes. Each note's content is returned with its path as a reference.
- `obsidian_search_notes`: Search for notes by name (case-insensitive, supports partial matches and regex).
- `obsidian_read_notes_dir`: List the directory structure under a specified path.
- `obsidian_write_note`: Create a new note at the specified path.
