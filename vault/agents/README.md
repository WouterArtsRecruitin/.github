# Agents Bibliotheek

Alle agent-definities: wie ze zijn, wat ze doen, welke tools ze gebruiken.

## Format per agent

```
agents/
├── {agent-naam}.md
└── {project}/{agent-naam}.md
```

Elk bestand:

```markdown
---
agent: scraping-agent
project: intelligence-hub
type: autonomous | assisted | scheduled
tools: [web-scraper, github-api, notion]
trigger: daily-cron | on-demand | webhook
created: 2026-02-10
---

# Agent naam

## Doel
Wat doet deze agent in één zin.

## Systeem prompt
De volledige prompt die deze agent aanstuurt.

## Tools & MCP servers
Welke tools/servers deze agent nodig heeft.

## Input
Wat verwacht de agent als input.

## Output
Wat levert de agent op.

## Voorbeeld
Een concreet voorbeeld van input → output.
```
