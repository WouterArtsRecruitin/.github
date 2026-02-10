# Template: Nieuwe MCP Server

## Gebruik

Zeg tegen Claude: "Maak een nieuwe MCP server op basis van de template"

## Structuur

```
{server-naam}/
├── README.md
├── CLAUDE.md
├── .gitignore
├── package.json
├── src/
│   ├── index.js                # Server entry point
│   ├── tools/                  # Tool definities
│   │   └── {tool-naam}.js
│   └── utils/                  # Gedeelde helpers
│       └── api-client.js
├── config/
│   └── default.json            # Default configuratie (GEEN secrets)
├── docs/
│   ├── prompts/                # Gebruikte prompts
│   └── tools.md                # Documentatie per tool
└── scripts/
    └── test-server.sh
```

## claude_desktop_config.json snippet

```json
{
  "mcpServers": {
    "{server-naam}": {
      "command": "node",
      "args": ["/pad/naar/{server-naam}/src/index.js"],
      "env": {
        "API_KEY": ""
      }
    }
  }
}
```

## Na het bouwen

1. Kopieer de config snippet naar `vault/mcp-configs/{server-naam}.json`
2. Voeg toe aan `vault/mcp-configs/claude-desktop-full.json`
3. Documenteer tools in `vault/agents/` als de server een agent aanstuurt
