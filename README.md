# Obsidian Model Context Protocol

This is a connector to allow Claude Desktop (or any MCP client) to read and search any directory containing Markdown notes (such as an Obsidian vault).

## Prerequisites
- Node.js (install via `brew install node`)
- Claude Desktop

## Installation
1. Make sure Claude Desktop is installed.

2. Install tsx globally:
```bash
npm install -g tsx
# or
pnpm add -g tsx
```

3. Clone this repository and install dependencies:
```bash
git clone <repository-url>
cd mcp-obsidian
npm install
# or
pnpm install
```

4. Simply modify your Claude Desktop config located here:
`~/Library/Application\ Support/Claude/claude_desktop_config.json`

You can easily find this through the Claude Desktop menu:
1. Open Claude Desktop
2. Click Claude on the Mac menu bar
3. Click "Settings"
4. Click "Developer"

If you don't have this config, you can create an empty file at this location.

Add the following to the config file, replacing:
- `<YOUR_NAME>` with your macOS username
- `<CLONE_DIR>` with the directory where you cloned this repository
- `<OBSIDIAN_VAULT_PATH>` with the path to your Obsidian vault

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": [
        "tsx",
        "/Users/<YOUR_NAME>/<CLONE_DIR>/mcp-obsidian/index.ts",
        "/Users/<YOUR_NAME>/<OBSIDIAN_VAULT_PATH>"
      ]
    }
  }
}
```

## Available Commands

The following MCP tools will be available in Claude Desktop:

- `obsidian_read_notes`: Read the contents of multiple notes. Each note's content is returned with its path as a reference.
- `obsidian_search_notes`: Search for notes by name (case-insensitive, supports partial matches and regex).
- `obsidian_read_notes_dir`: List the directory structure under a specified path.
- `obsidian_write_note`: Create a new note at the specified path.
