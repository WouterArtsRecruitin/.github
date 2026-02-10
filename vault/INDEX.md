# Vault Index — Alles wat je ooit gebouwd hebt

> Laatste update: 10 februari 2026
> Doorzoek dit bestand met Ctrl+F / Cmd+F

---

## MCP Servers (17 servers)

| Server | Wat het doet | Locatie | Taal |
|--------|-------------|---------|------|
| `cv-parser` | CV's parsen met HuggingFace | `recruitin-mcp-servers/cv-parser/server.py` + `recruitin-automation/mcp-servers/cv-parser/` | Python |
| `cv-vacancy-matcher` | CV's matchen aan vacatures (vector similarity) | `recruitin-mcp-servers/cv-vacancy-matcher/server.py` | Python |
| `pipedrive` | CRM integratie | `recruitin-mcp-servers/pipedrive/dist/index.js` | Node.js |
| `resend` | E-mail versturen | `recruitin-mcp-servers/resend-mcp-server/index.js` | Node.js |
| `brave-search` | Web zoeken | `recruitin-mcp-servers/brave-search-mcp-server.js` | Node.js |
| `company-insights` | Bedrijfsonderzoek agent | `recruitin-mcp-servers/company-insights-agent/` | Node.js |
| `vacancy-analysis` | Vacature analyse agent | `recruitin-mcp-servers/vacancy-analysis-agent/` | Node.js |
| `notion` (custom) | Notion workspace | `recruitin-mcp-servers/notion-mcp-server.js` | Node.js |
| `notionApi` (officieel) | Notion (21 tools, fork) | `notion-mcp-server` repo | TypeScript |
| `slack` | Slack berichten | `recruitin-mcp-servers/slack-mcp-server.js` | Node.js |
| `airtable` | Airtable database | `recruitin-mcp-servers/airtable-mcp-server.js` | Node.js |
| `figma` | Design tool integratie | `recruitin-mcp-servers/figma-mcp-server.js` | Node.js |
| `jotform` | Formulieren | `recruitin-mcp-servers/jotform-mcp-server.js` | Node.js |
| `linkedin` | LinkedIn connectie | `recruitin-mcp-servers/linkedin-mcp-server.js` | Node.js |
| `leonardo-ai` | AI afbeeldingen genereren | Gist `cd1922e16...` | Python (uvx) |
| `invideo` | Video genereren | Remote SSE `mcp.invideo.io/sse` | Remote |
| `image-gen-multi` | Multi-provider images (DALL-E, Stability, Flux) | Gist `cd1922e16...` | Node.js (npx) |

**Config bestanden:**
- Hoofd config template: `recruitin-mcp-servers/claude-desktop-config.example.json`
- Image/video config: Gist `cd1922e1610f26de9d1acd8706a85d58`
- Env template: Gist `de398ceb998319014b672243107b92ac`
- Install script: Gist `d898f35a25455d032e930fc9c2854f0a`

---

## Agents (7 agents)

| Agent | Wat het doet | Locatie |
|-------|-------------|---------|
| Prospect Intelligence | Bedrijfs- en contactpersonenonderzoek via Brave Search, genereert HTML rapporten | `recruitin-mcp-servers/prospect-intelligence-agent/` |
| Company Insights | Bedrijfsprofiel, vacatures, salaris, concurrentie per sector | `recruitin-mcp-servers/company-insights-agent/` |
| Competitor Monitoring | Monitort Randstad, Adecco, Manpower, Tempo-Team, YoungCapital wekelijks | `recruitin-mcp-servers/competitor-monitoring-agent/` |
| Daily Recruitment News | 28 zoekopdrachten, categoriseert, dedupliceert, webhook naar Zapier | `recruitin-mcp-servers/daily-recruitment-news-agent/` |
| Dutch News (Final) | 8 RSS feeds (Werf&, Intelligence Group, etc.), upload naar Notion | `recruitin-mcp-servers/dutch-news-agent-final/` |
| Dutch Recruitment News Notion | Recruitment nieuws → Notion integratie | `recruitin-mcp-servers/dutch-recruitment-news-notion/` |
| Arnhem Direct Jobs | Technische vacatures Arnhem regio, filtert uitzendbureaus eruit | `recruitin-mcp-servers/arnhem-direct-jobs-agent/` |

---

## Prompts (8 systeem-prompts)

| Prompt | Wat het doet | Locatie |
|--------|-------------|---------|
| Vacature Analyse v5.2 | Vacaturetekst analyseren + herschrijven (score 1-10, CBS/UWV data) | Gist `c5698358a...` |
| Kandidatentekort v6.0+ Scoring | 8-criteria expert panel, 40-punten scoring | Gist `9ef4caaf3...` |
| LinkedIn Personal Post | Posts schrijven als Wouter Arts | `intelligence-hub/linkedin-newsletter-automation.py` |
| LinkedIn Article | Artikelen voor CFOs/HR directors | `intelligence-hub/linkedin-newsletter-automation.py` |
| Company Page Post | Posts voor Recruitin B.V. bedrijfspagina | `intelligence-hub/linkedin-newsletter-automation.py` |
| Email Newsletter | Wekelijkse newsletter voor HR directors | `intelligence-hub/linkedin-newsletter-automation.py` |
| Notion Content Manager | Content management instructies + toon/stijl regels | `recruitin-mcp-servers/notion-content-system/CLAUDE.md` |
| LinkedIn Content Authority | Volledige contentstrategie, ICP personas, posting schema | `recruitin-mcp-servers/docs/linkedin-content-authority.md` |

---

## Scoring & Analyse (7 tools)

| Tool | Wat het doet | Locatie |
|------|-------------|---------|
| ICP Scoring (Zapier) | 7 criteria, 28.5 punten max, target sectoren | `recruitin-content-intelligence-system/icp/icp_scoring_zapier.py` |
| Content Sentiment | LinkedIn comments analyseren met BERT/RoBERTa | `recruitin-content-intelligence-system/analyze_content_sentiment.py` |
| APK Report Generator | Recruitment assessment 5 dimensies, score 1-10 | `recruitin-mcp-servers/elite-email-composer-mcp/src/apk-report-generator.ts` |
| Email Analyzer | E-mail effectiviteit (toon, helderheid, engagement) | `recruitin-mcp-servers/elite-email-composer-mcp/src/email-analyzer.ts` |
| Jobdigger Template | Arbeidsmarktdata uit Jobdigger PDFs | `recruitin-mcp-servers/labour-market-intelligence/src/intelligence/JobdiggerAnalysisTemplate.ts` |
| Market Intelligence Engine | CBS/UWV arbeidsmarkt, salaris benchmarks | `recruitin-mcp-servers/labour-market-intelligence/src/intelligence/MarketIntelligenceEngine.ts` |
| Professional Report Gen | Recruitment assessment rapporten (85% betrouwbaarheid) | `recruitin-mcp-servers/labour-market-intelligence/src/reports/ProfessionalReportGenerator.ts` |

---

## Email Templates (6 templates)

| Template | Wat het doet | Locatie |
|----------|-------------|---------|
| Vacancy Response — Dual Option | Reactie op vacature: interim + RPO pitch | `recruitin-mcp-servers/elite-email-composer-mcp/templates/recruitment/vacancy_response_corporate_recruiter.json` |
| Vacancy Response — Interim | Snelle interim recruitment pitch | `...templates/recruitment/vacancy_response_interim_focus.json` |
| Vacancy Response — RPO | Consultative RPO pitch | `...templates/recruitment/vacancy_response_rpo_focus.json` |
| Email Composer Framework | 4 copywriting frameworks (PAS, AIDA, etc.) | `recruitin-mcp-servers/elite-email-composer-mcp/src/email-composer.ts` |
| Pipedrive Email Sequence | 6-email corporate recruiter sequence | `...elite-email-composer-mcp/src/pipedrive-email-templates.ts` |
| Template Manager | 5 generieke email templates | `...elite-email-composer-mcp/src/template-manager.ts` |

---

## LinkedIn Content Templates (4 stijlen)

| Stijl | Beschrijving | Locatie |
|-------|-------------|---------|
| Contrarian | Bold statement + plot twist | `recruitin-content-intelligence-system/notion_content_manager.py` |
| Data Story | Specifiek getal + 3 insights | zelfde |
| How-To | Stap-voor-stap tips | zelfde |
| Behind-the-Scenes | Persoonlijke learnings | zelfde |

---

## GitHub Actions Workflows (26 workflows)

### recruitin-mcp-servers (5)
| Workflow | Wat het doet |
|----------|-------------|
| `claude-code-review.yml` | AI code review bij PRs |
| `claude.yml` | Claude agent integratie |
| `daily-news-scraper.yml` | Dagelijkse recruitment nieuws scraping |
| `publish-wouter-mcp.yml` | MCP server publicatie |
| `weekly-content-gen.yml` | Wekelijkse content generatie |

### intelligence-hub (12)
| Workflow | Wat het doet |
|----------|-------------|
| `claude-code-review.yml` | AI code review bij PRs |
| `claude.yml` | Claude agent integratie |
| `intelligence-hub.yml` | Core intelligence pipeline |
| `linkedin-newsletter.yml` | LinkedIn newsletter generatie |
| `weekly-concurrent-activity.yml` | Wekelijkse concurrent analyse |
| `weekly-dashboard.yml` | Dashboard data update |
| `weekly-email-engagement.yml` | E-mail engagement metrics |
| `weekly-icp-activity.yml` | ICP activity tracking |
| `weekly-intent-signals.yml` | Buyer intent signalen |
| `weekly-job-board.yml` | Job board scraping |
| `weekly-market-trends.yml` | Arbeidsmarkt trends |
| `yaml-lint.yml` | YAML validatie |

### TechnicalRecruitmentNews (4)
| Workflow | Wat het doet |
|----------|-------------|
| `claude-code-review.yml` | AI code review bij PRs |
| `claude.yml` | Claude agent integratie |
| `update-dashboard.yml` | Dashboard update |
| `weekly-scrape.yml` | Wekelijkse scraping |

### Kandidatentekortfull (2)
| Workflow | Wat het doet |
|----------|-------------|
| `claude-code-review.yml` | AI code review bij PRs |
| `claude.yml` | Claude agent integratie |

### recruitin-content-intelligence-system (3)
| Workflow | Wat het doet |
|----------|-------------|
| `claude-code-review.yml` | AI code review bij PRs |
| `claude.yml` | Claude agent integratie |
| `notion-content-automation.yml` | Content pipeline via Notion |

---

## Scripts (67 scripts)

### kandidatentekort-v6 — Meta Ads automation (34 scripts)
| Script | Type | Wat het doet |
|--------|------|-------------|
| `app.py` | web | Flask applicatie |
| `analyze_fomo_campaigns.py` | automation | FOMO campagne analyse |
| `check_all_accounts_for_fomo.py` | automation | Check alle Meta accounts |
| `create_fomo_campaigns.py` | automation | FOMO campagnes aanmaken |
| `create_complete_campaigns.py` | automation | Volledige campagne pipeline |
| `create_kt_audiences.py` | automation | Custom audiences aanmaken |
| `create_kt_audiences_v2.py` | automation | Custom audiences v2 |
| `create_kt_campaigns.py` | automation | Kandidatentekort campagnes |
| `meta_ads_create_audiences.py` | automation | Meta Ads audiences |
| `meta_ads_create_campaign.py` | automation | Meta Ads campagnes |
| `meta_ads_utm_analyzer.py` | utility | UTM analyse |
| `meta_ads_utm_fix.py` | utility | UTM reparatie |
| `track_fomo_performance.py` | automation | Performance tracking |
| `deploy_to_render.py` | deploy | Deploy naar Render |
| `deploy_old_design.sh` | deploy | Oude design deployen |
| `meta_ads_automated_deploy.sh` | deploy | Geautomatiseerde Meta Ads deploy |
| _(+ 18 meer)_ | | Zie `kandidatentekort-v6` repo |

### kandidatentekort-automation — CRM & email (11 scripts)
| Script | Type | Wat het doet |
|--------|------|-------------|
| `kandidatentekort_auto.py` | automation | Core automation (actueel) |
| `apollo-integration.py` | automation | Apollo.io lead enrichment |
| `email-service.js` | automation | E-mail service (Resend) |
| `pipedrive-service.js` | automation | Pipedrive CRM integratie |
| `zapier-apollo-mcp-bridge.js` | automation | Zapier ↔ Apollo ↔ MCP bridge |
| `netlify/functions/track-conversion.js` | serverless | Conversion tracking |
| _(+ 5 meer)_ | | Zie `kandidatentekort-automation` repo |

---

## Gists (9)

| Gist | Wat het is |
|------|-----------|
| `ac7e00696...` | GA4 + Meta Pixel + UTM tracking snippet (HTML) |
| `9ef4caaf3...` | Kandidatentekort v6.0+ scoring systeem (Python) |
| `d898f35a2...` | MCP servers install script (Shell) |
| `de398ceb9...` | Environment variables template (env) |
| `cd1922e16...` | Claude Desktop MCP config — Leonardo AI + InVideo (JSON) |
| `99d07966a...` | MCP Servers documentatie (README) |
| `c5698358a...` | Vacature analyse prompt v1.0 (Python) |
| `b3e9052d8...` | Cosmos Predictions Morphing (HTML) |
| `3a3d08217...` | Cosmos Predictions Canvas (HTML) |

---

## Commando's Bibliotheek

De volledige Recruitin Commands Library (50+ prompt-templates) staat in:
`recruitin-mcp-servers/docs/RECRUITIN-COMMANDS-LIBRARY-COMPLETE.md`

Categorieën: dagelijks, wekelijks, maandelijks, deal-specifiek, kandidaatbeheer, marketing, analytics, automation chains, emergency protocols.
