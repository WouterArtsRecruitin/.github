# CLAUDE.md — Instructies voor Claude bij elk project

## Over de gebruiker

Wouter Arts — eigenaar van Recruitin. Bouwt recruitment-technologie, AI agents, MCP servers en automation flows. Werkt met JavaScript, TypeScript, Python en HTML. Deployt naar Vercel en Netlify. Gebruikt Claude Projects voor elk nieuw project.

Wouter is zelf-beschreven "chaotisch" in organisatie. Raakt vaak prompts, configs, scripts en workflows kwijt. Daarom bestaat dit systeem.

## Vault: Centraal Register

Alles wat herbruikbaar is wordt opgeslagen in `/vault/` in de `.github` repo:

```
vault/
├── prompts/          # Systeem-prompts, agent-prompts
├── mcp-configs/      # MCP server configuraties
├── workflows/        # GitHub Actions templates
├── scripts/          # Herbruikbare scripts
├── templates/        # Project boilerplates
├── agents/           # Agent definities
└── designs/          # Design specs
```

## Regels bij NIEUW project

Wanneer Wouter een nieuw project start, doe ALTIJD:

### 1. Mappenstructuur

Maak deze structuur aan in de project-root:

```
{project}/
├── README.md               # Wat het is, hoe het werkt, hoe te runnen
├── CLAUDE.md               # Project-specifieke Claude instructies
├── .gitignore              # Altijd, met .env en credentials
├── .github/
│   └── workflows/          # Als er automation nodig is
├── src/                    # Broncode
├── docs/                   # Alleen als er complexe documentatie is
│   ├── prompts/            # Prompts die bij dit project horen
│   └── architecture.md     # Alleen bij complexe projecten
└── scripts/                # Utility scripts
```

### 2. CLAUDE.md in elk project

Maak altijd een `CLAUDE.md` in de project-root met:

```markdown
# CLAUDE.md — {Projectnaam}

## Wat is dit project?
[Eén alinea]

## Tech stack
- Taal: [JS/TS/Python]
- Framework: [Next.js/Express/Flask/etc]
- Deploy: [Vercel/Netlify/etc]
- MCP servers: [welke, indien van toepassing]

## Mappenstructuur
[Korte beschrijving van wat waar staat]

## Hoe te runnen
[Commando's om lokaal te draaien]

## Gerelateerde projecten
[Links naar vault en gerelateerde repos]
```

### 3. Registreer in de vault

Na het aanmaken van een nieuw project of een nieuw herbruikbaar onderdeel:

- **Prompt gemaakt?** → Kopieer naar `vault/prompts/{project}/`
- **MCP config gemaakt?** → Kopieer naar `vault/mcp-configs/`
- **Workflow gemaakt?** → Kopieer naar `vault/workflows/{project}/`
- **Script dat herbruikbaar is?** → Kopieer naar `vault/scripts/`
- **Agent ontworpen?** → Documenteer in `vault/agents/`

### 4. .gitignore altijd aanwezig

Minimale .gitignore voor elk project:

```
.env
.env.local
.env.*.local
node_modules/
__pycache__/
*.pyc
.DS_Store
*.log
dist/
build/
*.key
*.pem
*.secret
credentials*
```

## Regels bij BESTAAND project

Wanneer Wouter werkt aan een bestaand project:

1. Check of er een `CLAUDE.md` is — zo niet, maak er een aan
2. Check of er prompts/configs/scripts zijn die nog niet in de vault staan
3. Als je iets herbruikbaars maakt, registreer het in de vault

## Naamgevingsconventies

### Repositories
- `recruitin-{functie}` voor Recruitin projecten (bijv. `recruitin-mcp-servers`)
- `{projectnaam}` voor standalone projecten (bijv. `prompt-gym`)
- Geen spaties, geen hoofdletters, geen trailing hyphens

### Bestanden
- Scripts: `{actie}-{onderwerp}.{ext}` (bijv. `scrape-vacatures.py`)
- Prompts: `{type}-prompt.md` (bijv. `system-prompt.md`, `agent-scraper.md`)
- Configs: `{service}.json` (bijv. `notion.json`, `github.json`)

### Branches
- `main` — productie
- `dev` — ontwikkeling (als nodig)
- `feature/{korte-beschrijving}` — nieuwe features

## Lokale structuur (MacBook)

Wouter's lokale MacBook is georganiseerd als:

```
~/Recruitin/
├── projects/         # Alle git repos (clone hier)
├── vault/            # Symlink naar .github/vault
├── sandbox/          # Experimenten en tests
└── tools/            # Lokale configs (claude_desktop_config.json, .env.master)
```

### Regels lokaal
- **Nieuwe projecten** altijd aanmaken in `~/Recruitin/projects/`
- **Experimenten** in `~/Recruitin/sandbox/` — opruimen of promoveren naar projects
- **Nooit** losse projecten op Desktop of Downloads laten staan
- `~/Recruitin/tools/claude_desktop_config.json` is de backup van de werkende MCP config

## Vault Index

De volledige index van ALLES wat Wouter ooit gebouwd heeft staat in:
`vault/INDEX.md`

Dit bevat: alle 17 MCP servers, 7 agents, 8 systeem-prompts, 7 scoring tools, 6 email templates, 26 workflows, 67 scripts, 9 gists.

Raadpleeg deze index als Wouter iets zoekt of als je wilt weten of iets al bestaat.

## Stijl & Voorkeuren

- Taal in code: Engels
- Taal in documentatie: Nederlands, tenzij het voor een internationaal publiek is
- Houd bestanden klein en gefocust — liever 3 kleine bestanden dan 1 groot bestand
- Geen credentials in code — altijd .env of GitHub Secrets
- Beschrijf WAAROM, niet WAT in comments
