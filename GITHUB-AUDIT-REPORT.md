# GitHub Audit Report — WouterArtsRecruitin

**Datum:** 10 februari 2026
**Account:** [WouterArtsRecruitin](https://github.com/WouterArtsRecruitin)
**Totaal repositories:** 74 (publiek) | **Gists:** 9 | **Followers:** 2 | **Following:** 13
**Account aangemaakt:** 22 april 2025

---

## Inhoudsopgave

1. [Executive Summary](#1-executive-summary)
2. [KRITIEK — Beveiligingsproblemen](#2-kritiek--beveiligingsproblemen)
3. [Profiel & Branding](#3-profiel--branding)
4. [Repository Analyse](#4-repository-analyse)
5. [Repository Hygiëne](#5-repository-hygiëne)
6. [GitHub Actions & Automation](#6-github-actions--automation)
7. [Security Best Practices](#7-security-best-practices)
8. [Ontbrekende GitHub Features](#8-ontbrekende-github-features)
9. [Actieplan](#9-actieplan)

---

## 1. Executive Summary

Je GitHub-account wordt actief gebruikt voor recruitment-technologie en AI-automatie, maar heeft significante verbeterpunten op het gebied van **beveiliging**, **organisatie**, en **professionele presentatie**. De grootste risico's zijn gelekte credentials in publieke repos en het ontbreken van een duidelijke structuur.

### Scores per categorie

| Categorie | Score | Status |
|-----------|-------|--------|
| Beveiliging | 2/10 | KRITIEK |
| Profiel & Branding | 2/10 | Slecht |
| Repository Organisatie | 3/10 | Matig |
| CI/CD & Automation | 5/10 | Redelijk |
| Documentatie | 3/10 | Matig |
| Community & Visibility | 2/10 | Slecht |

---

## 2. KRITIEK — Beveiligingsproblemen

### 2.1 Gelekte credentials in publieke repositories

**`kandidatentekort-v6`** bevat bestanden met gevoelige informatie die publiek toegankelijk zijn:

| Bestand | Probleem |
|---------|----------|
| `IMPORTANT_ACCOUNTS.md` | Meta/Facebook Ad Account IDs, campagne-details |
| `CREDENTIALS_UPDATED.md` | Meta Access Tokens, Facebook Pixel IDs, App IDs |
| `fomo_image_hashes.json` | Interne campagne-data |
| `found_campaigns.json` | Campagne-structuur en IDs |

**Impact:** Iedereen kan deze credentials zien en misbruiken voor ongeautoriseerde API-calls op jouw Meta-advertentieaccounts.

**Actie (VANDAAG):**
1. Maak de `kandidatentekort-v6` repo **privé** of verwijder gevoelige bestanden
2. **Roteer ALLE gelekte tokens** — ze zijn gecompromitteerd zodra ze in git history staan
3. Gebruik `git filter-branch` of [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/) om credentials uit git history te verwijderen
4. Gebruik voortaan **GitHub Secrets** voor alle tokens en API keys

### 2.2 Geen branch protection

Geen enkele repository heeft branch protection rules op `main`. Dit betekent:
- Iedereen met write-access kan direct naar `main` pushen
- Geen verplichte code reviews
- Geen status checks vereist voor merge

### 2.3 Geen SECURITY.md

Er is nergens een security policy gedefinieerd. Bezoekers weten niet hoe ze beveiligingsproblemen moeten melden.

---

## 3. Profiel & Branding

### 3.1 Ontbrekende profielinformatie

| Veld | Status | Aanbeveling |
|------|--------|-------------|
| Naam | Ontbreekt | Voeg je volledige naam toe |
| Bio | Ontbreekt | "Recruitment Tech & AI Automation — Founder Recruitin.nl" |
| Locatie | Ontbreekt | Voeg locatie toe (Arnhem/Gelderland?) |
| Website | Ontbreekt | Link naar recruitin.nl of kandidatentekort.nl |
| Company | Ontbreekt | "@Recruitin" of bedrijfsnaam |
| Social links | Ontbreken | LinkedIn profiel toevoegen |

### 3.2 Profiel README ontbreekt

Je hebt geen persoonlijk profiel README (`WouterArtsRecruitin/WouterArtsRecruitin` repo). Dit is het eerste wat bezoekers zien.

**Aanbeveling:** Maak een `WouterArtsRecruitin` repo met een `README.md` die bevat:
- Wie je bent en wat je doet
- Belangrijkste projecten (recruitment MCP servers, intelligence hub)
- Tech stack
- Contact informatie

### 3.3 `.github` repo is een Canva fork

De huidige `.github` repo (organisatie profiel) is een **fork van Canva's developer platform** en bevat nog steeds hun content:
> "This GitHub organization contains repos for Canva's developer platform"

Dit is verwarrend voor bezoekers en niet relevant voor jouw gebruik.

**Actie:** Vervang de content in `profile/README.md` met je eigen organisatieprofiel.

### 3.4 Geen gepinde repositories

Je hebt geen repositories gepind op je profiel. De automatisch getoonde repos (`agent-browser` fork) representeren je werk niet goed.

**Aanbeveling — Pin deze repos:**
1. `recruitin-mcp-servers` — vlaggenschipproject (43+ MCP servers)
2. `intelligence-hub` — market intelligence systeem
3. `TechnicalRecruitmentNews` — dagelijkse nieuwsverzameling
4. `prompt-gym` — interactief prompt-tool
5. `cosmos-particles` — visueel aantrekkelijk project
6. `kandidatentekort-v6` — (na opschoning) recruitment platform

---

## 4. Repository Analyse

### 4.1 Overzicht per categorie

#### Kern Recruitment Projecten (actief, waardevol)
| Repo | Taal | Laatste push | Status |
|------|------|-------------|--------|
| `recruitin-mcp-servers` | JS | 2026-02-09 | Actief, 8 open issues |
| `intelligence-hub` | JS | 2026-02-09 | Actief, goed gestructureerd |
| `TechnicalRecruitmentNews` | JS | 2026-02-09 | Actief |
| `recruitin-content-intelligence-system` | HTML | 2026-02-09 | Actief |
| `Kandidatentekortfull` | Python | 2026-01-14 | Actief |
| `kandidatentekort-v6` | Python | 2025-12-23 | Beveiligingsrisico |
| `kandidatentekort-automation` | Python | 2025-12-29 | Actief |
| `kandidatentekort-tracking` | HTML | 2025-12-21 | Actief |

#### Creative/Demo Projecten
| Repo | Taal | Laatste push | Status |
|------|------|-------------|--------|
| `cosmos-particles` | TS | 2026-02-10 | Actief, heeft Vercel deploy |
| `cosmos-predictions-` | TS | 2026-02-07 | Actief |
| `prompt-gym` | TS | 2026-02-10 | Actief, heeft Vercel deploy |
| `Gelre-advocatuur-redesign` | HTML | 2026-02-06 | Eenmalig concept |

#### Mogelijk Verouderd/Ongebruikt
| Repo | Probleem |
|------|----------|
| `recruitpro-enterprise` | Leeg (0 KB) |
| `Flowmasterlive` | Leeg (0 KB) |
| `vacature-analyse` | Leeg (0 KB) |
| `Meteoor-Operations` | Leeg (0 KB) |
| `aebi-recruitment-site` | Leeg (0 KB) |
| `recruitment-dashboard-v2` | 7 KB, geen updates sinds okt 2025 |
| `recruitin-api` | 33 KB, geen updates sinds okt 2025 |
| `test-recruitmentapk-pdf` | Test repo, 8 KB |
| `evp-landing-recruitin` | Eenmalig, geen updates sinds aug 2025 |

#### Forks — Geen Wijzigingen
| Repo | Oorsprong | Actie nodig |
|------|-----------|-------------|
| `.github` | Canva | Vervangen of verwijderen |
| `embed` | Typeform | Niet gewijzigd, verwijderen |
| `apollo-api-docs` | Apollo | Niet gewijzigd, verwijderen |
| `apollo-io-mcp` | Apollo | Niet gewijzigd, verwijderen |
| `canva-apps-sdk-starter-kit` | Canva | Niet gewijzigd, verwijderen |
| `canva-connect-api-starter-kit` | Canva | Niet gewijzigd, verwijderen |
| `linkedin-api-python-client` | LinkedIn | Niet gewijzigd, verwijderen |
| `linkedin-capi-tag-template` | LinkedIn | Niet gewijzigd, verwijderen |
| `recruiter-system-connect-development-tools` | LinkedIn | Niet gewijzigd, verwijderen |
| `kapture` | MCP browser | Niet gewijzigd, verwijderen |
| `prompt-eng-interactive-tutorial` | Anthropic | Niet gewijzigd, verwijderen |
| `claude-quickstarts` | Anthropic | Niet gewijzigd, verwijderen |
| `clawdbot` | Clawdbot | Niet gewijzigd, verwijderen |

### 4.2 Duplicate/Overlappende Repos

Er zijn meerdere overlappende projecten die geconsolideerd moeten worden:

| Groep | Repos | Aanbeveling |
|-------|-------|-------------|
| Kandidatentekort | `Kandidatentekortfull`, `kandidatentekort-v6`, `kandidatentekort-automation`, `kandidatentekort-tracking` | Consolideer naar 1 repo |
| FlowMaster | `flowmaster-live`, `Flowmasterlive`, `flowmaster-assessment` | Consolideer of archiveer |
| Recruitment APK | `Recruitmentapk`, `Recruitment-APK`, `recruitment-apk-landing`, `recruitmentapk-website`, `test-recruitmentapk-pdf` | Consolideer naar 1-2 repos |
| RecruitPro | `recruitpro-web`, `recruitpro-enterprise`, `Recruitpro-assessment` | Consolideer of archiveer |
| MCP Servers | `recruitin-mcp-servers`, `recruitin-automation`, `notion-mcp-server` (fork) | Houd bij `recruitin-mcp-servers` |

---

## 5. Repository Hygiëne

### 5.1 Ontbrekende essentiële bestanden

| Bestand | Hoeveel repos missen dit | Waarom belangrijk |
|---------|--------------------------|-------------------|
| `LICENSE` | ~60 van 74 repos | Zonder licentie is code juridisch niet te gebruiken door anderen |
| `README.md` (kwalitatief) | ~40 repos | Typos in beschrijvingen ("recruitmentb trends", "interactive promptgme") |
| `.gitignore` | Meerdere repos | Voorkomt per ongeluk committen van gevoelige bestanden |
| `CONTRIBUTING.md` | Alle repos | Niet nodig tenzij je bijdragen wilt |
| `CODE_OF_CONDUCT.md` | Alle repos | Niet strikt nodig voor solo-projecten |

### 5.2 Grote bestanden in repos

| Repo | Grootte | Probleem |
|------|---------|---------|
| `clawdbot` (fork) | 152 MB | Enorme fork, verwijderen indien ongewijzigd |
| `recruitment-apk-landing` | 45 MB | Bevat waarschijnlijk assets die in CDN horen |
| `Kandidatentekortfull` | 33 MB | PNG-bestanden en data in repo |
| `kandidatentekort-v6` | 41 MB | Images, JSON data, campagnebestanden |
| `canva-connect-api-starter-kit` | 27 MB | Fork, verwijderen |
| `report-templates` | 25 MB | Templates met assets |
| `recruitmentapk-website` | 23 MB | Webbestanden met assets |
| `nederlandse-vacature-optimizer` | 13 MB | Assets in repo |

**Aanbeveling:** Gebruik een CDN (Cloudflare R2, AWS S3, of Vercel Blob) voor afbeeldingen en grote assets in plaats van git.

### 5.3 Topics/Tags ontbreken

**Geen enkele repository heeft topics/tags.** Dit is slecht voor:
- Vindbaarheid op GitHub
- Organisatie van je eigen repos
- SEO van je projecten

**Aanbevolen topics per repo:**
- `recruitin-mcp-servers`: `mcp`, `recruitment`, `ai-automation`, `model-context-protocol`, `claude`
- `intelligence-hub`: `recruitment`, `market-intelligence`, `web-scraping`, `automation`
- `TechnicalRecruitmentNews`: `recruitment`, `news`, `scraping`, `automation`
- `kandidatentekort-v6`: `recruitment`, `vacancy-analysis`, `ai`, `netherlands`
- `cosmos-particles`: `threejs`, `particles`, `hand-tracking`, `creative-coding`
- `prompt-gym`: `prompt-engineering`, `ai`, `education`, `interactive`

---

## 6. GitHub Actions & Automation

### 6.1 Huidige workflows

Je maakt goed gebruik van GitHub Actions in je kernprojecten:

**`recruitin-mcp-servers` (5 workflows):**
- `claude-code-review.yml` — AI code review
- `claude.yml` — Claude integration
- `daily-news-scraper.yml` — Dagelijkse scraping
- `publish-wouter-mcp.yml` — Publishing
- `weekly-content-gen.yml` — Wekelijkse content generatie

**`intelligence-hub` (12 workflows):**
- Uitgebreide set voor market intelligence, dashboard, engagement tracking
- `yaml-lint.yml` — Code kwaliteit

**`TechnicalRecruitmentNews` (4 workflows):**
- Dashboard updates, wekelijkse scraping

**`Kandidatentekortfull` (2 workflows):**
- Claude code review en integratie

### 6.2 Verbeterpunten

| Probleem | Impact | Aanbeveling |
|----------|--------|-------------|
| Geen dependency scanning | Kwetsbare packages worden niet gedetecteerd | Voeg `dependabot.yml` toe aan alle JS/Python repos |
| Geen test workflows | Geen geautomatiseerde tests | Voeg test CI toe voor kernprojecten |
| Geen linting (behalve intelligence-hub) | Inconsistente code kwaliteit | Voeg ESLint/Prettier workflows toe |
| Geen build checks | Broken code kan gemerged worden | Voeg build verification toe |
| Geen caching in workflows | Langzamere builds | Voeg `actions/cache` toe voor node_modules/pip |

### 6.3 Aanbevolen nieuwe workflows

```
# Voeg toe aan alle kernrepos:
1. dependabot.yml          — Automatische dependency updates
2. codeql-analysis.yml     — Security scanning van code
3. lint-and-test.yml       — Linting + tests bij elke PR
4. stale.yml               — Automatisch sluiten van oude issues
```

---

## 7. Security Best Practices

### 7.1 Huidige status

| Maatregel | Status | Prioriteit |
|-----------|--------|------------|
| Credentials in publieke repos | GELEKT | KRITIEK |
| Branch protection | Niet ingesteld | Hoog |
| Dependabot alerts | Niet ingeschakeld | Hoog |
| Code scanning (CodeQL) | Niet ingeschakeld | Hoog |
| Secret scanning | Niet ingeschakeld | Hoog |
| Signed commits (GPG) | Geen GPG keys | Medium |
| 2FA | Onbekend (niet zichtbaar via API) | Hoog |
| SSH keys | Onbekend | Medium |
| SECURITY.md | Ontbreekt overal | Medium |

### 7.2 Aanbevolen acties

1. **Schakel GitHub Secret Scanning in** — detecteert automatisch gelekte API keys
2. **Schakel Dependabot in** voor alle repos met dependencies
3. **Schakel CodeQL Analysis in** voor JavaScript en Python repos
4. **Stel branch protection in** op `main` voor kernrepos:
   - Require pull request before merge
   - Require status checks to pass
   - Require signed commits (optioneel)
5. **Verifieer dat 2FA is ingeschakeld** op je account

---

## 8. Ontbrekende GitHub Features

Features die je niet gebruikt maar die waarde toevoegen:

| Feature | Nut voor jouw use case |
|---------|----------------------|
| **GitHub Projects** | Kanban-bord voor je recruitment tool development |
| **GitHub Discussions** | Community feedback op je MCP servers |
| **GitHub Pages** | Documentatie-site voor recruitin-mcp-servers |
| **GitHub Releases** | Versioned releases van je tools |
| **GitHub Packages** | Publiceer MCP servers als npm packages |
| **Issue Templates** | Gestandaardiseerde bug reports en feature requests |
| **PR Templates** | Consistente pull request beschrijvingen |
| **CODEOWNERS** | Automatische review assignments |
| **GitHub Wiki** | Wel ingeschakeld, maar nergens gebruikt |
| **Pinned Repos** | Highlight je beste werk |

---

## 9. Actieplan

### Fase 1 — DIRECT (Beveiliging)
- [ ] Maak `kandidatentekort-v6` privé
- [ ] Roteer ALLE gelekte Meta/Facebook tokens en API keys
- [ ] Verwijder credentials uit git history met BFG Repo-Cleaner
- [ ] Controleer alle andere repos op gelekte secrets
- [ ] Schakel GitHub Secret Scanning in (Settings > Code security)
- [ ] Verifieer dat 2FA actief is

### Fase 2 — Deze week (Opschoning)
- [ ] Verwijder 13 ongewijzigde forks (lijst in sectie 4.1)
- [ ] Archiveer 5+ lege repositories
- [ ] Archiveer verouderde/eenmalige projecten
- [ ] Fix typos in repo-beschrijvingen ("recruitmentb" → "recruitment")
- [ ] Voeg topics/tags toe aan alle actieve repos

### Fase 3 — Deze maand (Profiel & Structuur)
- [ ] Vul profielinformatie in (naam, bio, website, locatie)
- [ ] Maak `WouterArtsRecruitin/WouterArtsRecruitin` repo met profiel README
- [ ] Vervang Canva-content in `.github/profile/README.md` met eigen profiel
- [ ] Pin 6 beste repositories
- [ ] Consolideer duplicate repos (Kandidatentekort, FlowMaster, RecruitPro, Recruitment APK)
- [ ] Voeg LICENSE (MIT) toe aan alle eigen projecten

### Fase 4 — Doorlopend (Kwaliteit & Groei)
- [ ] Voeg `dependabot.yml` toe aan alle actieve repos
- [ ] Stel branch protection in op `main` voor kernrepos
- [ ] Voeg CodeQL scanning toe
- [ ] Maak issue templates en PR templates
- [ ] Overweeg GitHub Organization voor "Recruitin"
- [ ] Publiceer recruitin-mcp-servers als npm package
- [ ] Zet GitHub Pages op voor documentatie
- [ ] Gebruik GitHub Releases voor versioning

---

## Bijlage: Volledige Repository Inventaris

### Eigen Repos (niet-forks)

| # | Repo | Taal | Grootte | Laatste Push | Licentie | Aanbeveling |
|---|------|------|---------|-------------|----------|-------------|
| 1 | recruitin-mcp-servers | JS | 2 MB | 2026-02-09 | Geen | Behouden, licentie toevoegen |
| 2 | intelligence-hub | JS | 2.3 MB | 2026-02-09 | Geen | Behouden, licentie toevoegen |
| 3 | TechnicalRecruitmentNews | JS | 180 KB | 2026-02-09 | Geen | Behouden |
| 4 | cosmos-particles | TS | 89 KB | 2026-02-10 | Geen | Behouden |
| 5 | prompt-gym | TS | 381 KB | 2026-02-10 | Geen | Behouden |
| 6 | cosmos-predictions- | TS | 312 KB | 2026-02-07 | Geen | Behouden (fix repo naam: trailing hyphen) |
| 7 | recruitin-content-intelligence-system | HTML | 3.3 MB | 2026-02-09 | Geen | Behouden |
| 8 | Gelre-advocatuur-redesign | HTML | 50 KB | 2026-02-06 | Geen | Archiveren (eenmalig concept) |
| 9 | Kandidatentekortfull | Python | 33 MB | 2026-01-14 | Geen | Consolideren |
| 10 | kandidatentekort-v6 | Python | 41 MB | 2025-12-23 | Geen | PRIVÉ MAKEN, opschonen |
| 11 | kandidatentekort-automation | Python | 184 KB | 2025-12-29 | Geen | Consolideren |
| 12 | kandidatentekort-tracking | HTML | 122 KB | 2025-12-21 | Geen | Consolideren |
| 13 | recruitin-unified-platform | JS | 39 KB | 2026-01-16 | Geen | Evalueren |
| 14 | Recruitment-APK | TS | 350 KB | 2025-12-25 | Geen | Consolideren |
| 15 | recruitmentapk-website | Shell | 23 MB | 2025-10-18 | Geen | Consolideren |
| 16 | recruitment-apk-landing | HTML | 45 MB | 2025-08-19 | Geen | Assets naar CDN, consolideren |
| 17 | Recruitmentapk | HTML | 7 MB | 2025-07-29 | Geen | Consolideren |
| 18 | test-recruitmentapk-pdf | HTML | 8 KB | 2025-08-05 | Geen | Verwijderen (test repo) |
| 19 | recruitpro-web | JS | 145 KB | 2025-08-02 | Geen | Evalueren/archiveren |
| 20 | recruitpro-enterprise | - | 0 KB | 2025-07-29 | Geen | Verwijderen (leeg) |
| 21 | Recruitpro-assessment | TS | 24 KB | 2025-07-30 | Geen | Evalueren/archiveren |
| 22 | flowmaster-live | HTML | 175 KB | 2025-08-06 | Geen | Evalueren/archiveren |
| 23 | Flowmasterlive | - | 0 KB | 2025-07-29 | Geen | Verwijderen (leeg) |
| 24 | flowmaster-assessment | HTML | 34 KB | 2025-08-04 | Geen | Evalueren/archiveren |
| 25 | Whitepaper-EVP | HTML | 208 KB | 2025-08-09 | Geen | Evalueren/archiveren |
| 26 | vacature-analyse | - | 0 KB | 2025-08-09 | Geen | Verwijderen (leeg) |
| 27 | nederlandse-vacature-optimizer | HTML | 13 MB | 2025-11-29 | Geen | Evalueren |
| 28 | evp-landing-recruitin | JS | 24 KB | 2025-08-12 | Geen | Archiveren |
| 29 | Meteoor-Operations | - | 0 KB | 2025-08-22 | Geen | Verwijderen (leeg) |
| 30 | meteoor-operations-manager | HTML | - | 2025-08-22 | Geen | Archiveren (eenmalig) |
| 31 | report-templates | Python | 25 MB | 2025-12-02 | Geen | Evalueren |
| 32 | labour-market-intelligence-landing | Python | 441 KB | 2025-11-03 | Geen | Evalueren |
| 33 | recruitin-api | Python | 33 KB | 2025-10-16 | Geen | Evalueren/archiveren |
| 34 | recruitment-dashboard-v2 | HTML | 7 KB | 2025-10-13 | Geen | Archiveren |
| 35 | recruitin-automation | Python | 10 KB | 2025-12-18 | Geen | Consolideren met MCP servers |
| 36 | aebi-recruitment-site | - | 0 KB | 2025-11-03 | Geen | Verwijderen (leeg) |

### Forks

| # | Repo | Oorsprong | Gewijzigd? | Aanbeveling |
|---|------|-----------|------------|-------------|
| 1 | .github | Canva | Nee* | Vervang content |
| 2 | embed | Typeform | Nee | Verwijderen |
| 3 | apollo-api-docs | Apollo | Nee | Verwijderen |
| 4 | apollo-io-mcp | Apollo | Nee | Verwijderen |
| 5 | canva-apps-sdk-starter-kit | Canva | Nee | Verwijderen |
| 6 | canva-connect-api-starter-kit | Canva | Nee | Verwijderen |
| 7 | linkedin-api-python-client | LinkedIn | Nee | Verwijderen |
| 8 | linkedin-capi-tag-template | LinkedIn | Nee | Verwijderen |
| 9 | recruiter-system-connect-development-tools | LinkedIn | Nee | Verwijderen |
| 10 | kapture | MCP | Nee | Verwijderen |
| 11 | prompt-eng-interactive-tutorial | Anthropic | Nee | Verwijderen |
| 12 | claude-quickstarts | Anthropic | Nee | Verwijderen |
| 13 | claude-plugins-official | Anthropic | Nee | Verwijderen |
| 14 | clawdbot | Clawdbot | Nee | Verwijderen (152 MB!) |
| 15 | notion-mcp-server | Notion | Ja | Behouden als nodig |

---

*Dit rapport is gegenereerd op basis van publiek beschikbare GitHub API data en repository-analyse.*
