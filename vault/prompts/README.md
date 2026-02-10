# Prompts Bibliotheek

Alle prompts opgeslagen per project of als losse herbruikbare prompt.

## Naamgeving

```
prompts/
├── {project-naam}/
│   ├── system-prompt.md        # Hoofd systeem-prompt
│   ├── agent-{naam}.md         # Specifieke agent prompts
│   └── analysis-{naam}.md     # Analyse prompts
└── shared/
    ├── code-review.md          # Herbruikbaar: code review prompt
    ├── recruitment-analysis.md # Herbruikbaar: vacature analyse
    └── content-generation.md   # Herbruikbaar: content generatie
```

## Hoe toe te voegen

Claude doet dit automatisch. Als je handmatig wilt toevoegen:

1. Maak een `.md` bestand in de juiste map
2. Gebruik dit format bovenaan:

```markdown
---
project: intelligence-hub
type: system-prompt | agent | analysis | template
created: 2026-02-10
last-used: 2026-02-10
tags: [scraping, recruitment, market-intelligence]
---

# Prompt naam

[De prompt tekst hier]
```
