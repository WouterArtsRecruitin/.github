# Template: Nieuwe Scraper / Data Pipeline

## Gebruik

Zeg tegen Claude: "Maak een nieuwe scraper op basis van de template"

## Structuur

```
{scraper-naam}/
├── README.md
├── CLAUDE.md
├── .gitignore
├── .github/
│   └── workflows/
│       ├── scrape-daily.yml     # Dagelijkse cron
│       └── scrape-weekly.yml    # Wekelijkse cron (kies wat past)
├── src/
│   ├── scraper.js               # Hoofd scraping logica
│   ├── parser.js                # Data parsing/transformatie
│   └── output.js                # Output naar bestand/API/database
├── data/                        # .gitignore dit!
│   └── .gitkeep
├── config/
│   └── sources.json             # Welke bronnen te scrapen
└── scripts/
    └── run-local.sh
```

## Cron workflow basis

```yaml
name: Daily Scrape
on:
  schedule:
    - cron: '0 7 * * *'     # Elke dag 07:00 UTC
  workflow_dispatch:          # Handmatig triggeren

jobs:
  scrape:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: node src/scraper.js
        env:
          API_KEY: ${{ secrets.API_KEY }}
```

## Na het bouwen

1. Kopieer workflow naar `vault/workflows/{project}/`
2. Als er prompts gebruikt worden voor AI-analyse, kopieer naar `vault/prompts/{project}/`
3. Registreer in vault README
