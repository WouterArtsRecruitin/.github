# Template: Nieuw Python Project

## Gebruik

Zeg tegen Claude: "Maak een nieuw Python project op basis van de template"

## Structuur

```
{project-naam}/
├── README.md
├── CLAUDE.md
├── .gitignore
├── .github/
│   └── workflows/
│       └── ci.yml
├── requirements.txt
├── src/
│   ├── __init__.py
│   └── main.py
├── scripts/
│   └── (utility scripts)
└── docs/
    └── prompts/
```

## .gitignore

```
.env
.env.local
__pycache__/
*.pyc
*.pyo
venv/
.venv/
dist/
build/
*.egg-info/
.DS_Store
*.log
*.key
*.pem
credentials*
data/
*.csv
*.xlsx
```

## CI workflow basis

```yaml
name: CI
on:
  pull_request:
    branches: [main]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
          cache: pip
      - run: pip install -r requirements.txt
      - run: python -m pytest --if-present
```
