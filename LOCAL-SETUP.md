# Lokale MacBook Setup — Nooit meer kwijt

## Het probleem

Projecten, downloads, scripts en configs staan overal: Desktop, Downloads, random mappen, losse bestanden. Je vindt niks terug.

## De oplossing: Eén boom

Maak **één map** aan die alles bevat. Clone deze map naar je MacBook.

```
~/Recruitin/
├── projects/               # Alle git repos
│   ├── recruitin-mcp-servers/
│   ├── intelligence-hub/
│   ├── kandidatentekort/         # Geconsolideerd
│   ├── prompt-gym/
│   └── ...
├── vault/                  # Symlink naar .github/vault (of clone)
│   ├── prompts/
│   ├── mcp-configs/
│   ├── scripts/
│   ├── agents/
│   └── ...
├── sandbox/                # Experimenteer hier, niet in projects
│   ├── test-iets/
│   └── probeersel/
└── tools/                  # Lokale tools en configs
    ├── claude_desktop_config.json   # Jouw werkende config
    └── .env.master                   # Master env (NOOIT in git)
```

## Eenmalige setup

Kopieer en plak dit in je terminal:

```bash
# 1. Maak de structuur
mkdir -p ~/Recruitin/{projects,vault,sandbox,tools}

# 2. Clone je vault
cd ~/Recruitin
git clone https://github.com/WouterArtsRecruitin/.github.git vault-repo
ln -s ~/Recruitin/vault-repo/vault ~/Recruitin/vault

# 3. Clone je actieve projecten
cd ~/Recruitin/projects
git clone https://github.com/WouterArtsRecruitin/recruitin-mcp-servers.git
git clone https://github.com/WouterArtsRecruitin/intelligence-hub.git
git clone https://github.com/WouterArtsRecruitin/TechnicalRecruitmentNews.git
git clone https://github.com/WouterArtsRecruitin/prompt-gym.git
git clone https://github.com/WouterArtsRecruitin/recruitin-content-intelligence-system.git

# 4. Kopieer je werkende claude config naar tools
cp ~/Library/Application\ Support/Claude/claude_desktop_config.json ~/Recruitin/tools/
```

## Regels (voor jezelf en voor Claude)

### Regel 1: Alles in ~/Recruitin/
Geen losse projecten op Desktop of Downloads. Alles staat in `~/Recruitin/projects/`.

### Regel 2: Sandbox voor experimenten
Wil je iets uitproberen? Doe het in `~/Recruitin/sandbox/`. Ruim op als je klaar bent of verplaats naar `projects/` als het een echt project wordt.

### Regel 3: Eén project per repo
Geen 4 kandidatentekort repos. Eén repo per project.

### Regel 4: Claude kent de structuur
Voeg dit toe aan je Claude Project instructions:

```
Alle projecten staan in ~/Recruitin/projects/
De vault met prompts, configs en templates staat in ~/Recruitin/vault/
Experimenteer in ~/Recruitin/sandbox/
Sla nieuwe prompts/configs/agents altijd op in de vault
```

## Lokale bestanden terugvinden

### "Waar was die MCP config?"
```bash
# Optie 1: in de vault
cat ~/Recruitin/vault/mcp-configs/

# Optie 2: je werkende config
cat ~/Recruitin/tools/claude_desktop_config.json

# Optie 3: zoek lokaal
grep -r "mcpServers" ~/Recruitin/ --include="*.json" -l
```

### "Waar was dat script?"
```bash
# Vault index doorzoeken
grep -i "zoekterm" ~/Recruitin/vault/INDEX.md

# Of zoek bestanden
find ~/Recruitin/projects -name "*.py" | grep -i "zoekterm"
```

### "Waar was die prompt?"
```bash
# Vault prompts
ls ~/Recruitin/vault/prompts/

# Of zoek in de index
grep -i "vacature\|scoring\|linkedin" ~/Recruitin/vault/INDEX.md
```

## Claude Desktop Config syncen

Als je je MCP config wijzigt, sla een kopie op:

```bash
# Na elke wijziging
cp ~/Library/Application\ Support/Claude/claude_desktop_config.json ~/Recruitin/tools/
cd ~/Recruitin/vault-repo && git add -A && git commit -m "update claude config" && git push
```

Of maak een alias in `~/.zshrc`:

```bash
alias sync-claude='cp ~/Library/Application\ Support/Claude/claude_desktop_config.json ~/Recruitin/tools/ && echo "Config opgeslagen"'
```

## Downloads opruimen

Zet dit in je `~/.zshrc` om downloads automatisch te sorteren:

```bash
alias cleanup-downloads='
  mv ~/Downloads/*.py ~/Recruitin/sandbox/ 2>/dev/null
  mv ~/Downloads/*.js ~/Recruitin/sandbox/ 2>/dev/null
  mv ~/Downloads/*.json ~/Recruitin/sandbox/ 2>/dev/null
  mv ~/Downloads/*.md ~/Recruitin/sandbox/ 2>/dev/null
  echo "Scripts verplaatst naar ~/Recruitin/sandbox/"
'
```
