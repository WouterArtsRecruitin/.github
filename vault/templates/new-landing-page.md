# Template: Nieuwe Landing Page / Website

## Gebruik

Zeg tegen Claude: "Maak een nieuwe landing page op basis van de template"

## Structuur

```
{site-naam}/
├── README.md
├── CLAUDE.md
├── .gitignore
├── index.html                  # Of Next.js/React app
├── styles/
│   └── main.css
├── assets/
│   └── (images, icons — houd klein, gebruik CDN voor grote bestanden)
├── scripts/
│   └── main.js
├── netlify.toml                # Of vercel.json
└── docs/
    └── design-specs.md         # Design keuzes en specs
```

## Deploy configuratie

### Vercel (vercel.json)
```json
{
  "buildCommand": null,
  "outputDirectory": ".",
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

### Netlify (netlify.toml)
```toml
[build]
  publish = "."

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

## Na het bouwen

1. Voeg deploy URL toe aan repo beschrijving (homepage)
2. Als er design specs zijn, kopieer naar `vault/designs/`
