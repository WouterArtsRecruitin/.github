# Scripts Bibliotheek

Herbruikbare scripts voor scraping, automation, deployment, data processing.

## Structuur

```
scripts/
├── {project-naam}/
│   ├── scrape-vacatures.py
│   └── deploy.sh
└── shared/
    ├── github-cleanup.sh
    ├── vercel-deploy.sh
    └── meta-ads-api.py
```

## Naamgeving

- `scrape-{bron}.py` — scraping scripts
- `deploy-{platform}.sh` — deployment scripts
- `process-{data}.py` — data verwerking
- `automate-{taak}.py` — automation scripts
