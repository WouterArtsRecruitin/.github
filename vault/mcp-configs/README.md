# MCP Configuraties

Alle MCP server configuraties op één plek.

## Bestanden

```
mcp-configs/
├── claude-desktop-full.json     # Volledige claude_desktop_config.json
├── {project-naam}.json          # Per-project MCP config
└── snippets/
    ├── notion.json              # Losse server configs
    ├── github.json
    ├── filesystem.json
    └── ...
```

## Format

Elk bestand bevat een werkende MCP configuratie die je direct kunt kopiëren naar `claude_desktop_config.json`:

```json
{
  "_meta": {
    "project": "intelligence-hub",
    "created": "2026-02-10",
    "description": "MCP servers voor market intelligence scraping"
  },
  "mcpServers": {
    "server-naam": {
      "command": "...",
      "args": ["..."],
      "env": {
        "API_KEY": "VERVANG_DIT"
      }
    }
  }
}
```
