# Template: Nieuw JavaScript/TypeScript Project

## Gebruik

Zeg tegen Claude: "Maak een nieuw JS project op basis van de template"

## Structuur

```
{project-naam}/
├── README.md
├── CLAUDE.md
├── .gitignore
├── .github/
│   └── workflows/
│       └── ci.yml              # Lint + test bij PR
├── package.json
├── src/
│   └── index.js                # of index.ts
├── scripts/
│   └── (utility scripts)
└── docs/
    └── prompts/                # Gebruikte prompts
```

## package.json basis

```json
{
  "name": "{project-naam}",
  "version": "1.0.0",
  "description": "{beschrijving}",
  "main": "src/index.js",
  "scripts": {
    "start": "node src/index.js",
    "dev": "node --watch src/index.js"
  },
  "author": "WouterArtsRecruitin",
  "license": "MIT"
}
```

## .gitignore

```
node_modules/
.env
.env.local
.DS_Store
dist/
build/
*.log
*.key
*.pem
credentials*
```

## CI workflow basis

```yaml
name: CI
on:
  pull_request:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm test --if-present
```
