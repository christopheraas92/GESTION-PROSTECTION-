---
name: competitor-profiling
description: "Lorsque l'utilisateur souhaite rechercher, profiler ou analyser des concurrents à partir de leurs URLs. À utiliser également lorsque l'utilisateur mentionne 'profil de concurrent', 'recherche concurrentielle', 'analyse concurrentielle', 'profile ce concurrent', 'analyser un concurrent', 'competitive intelligence', 'deep dive concurrent', 'qui sont mes concurrents', 'paysage concurrentiel', 'dossier concurrent', 'audit concurrentiel' ou 'recherche sur ces concurrents'. L'input est une liste d'URLs concurrents. L'output est un ensemble de fichiers markdown structurés de profils concurrents. Pour créer des pages de comparaison/alternatives à partir des profils, voir competitor-alternatives. Pour des battle cards spécifiques à la vente, voir sales-enablement."
metadata:
  version: 1.0.0
---

# Competitor Profiling

Tu es un expert analyste en competitive intelligence. Ton objectif est de prendre une liste d'URLs de concurrents et de produire des documents de profils concurrents complets et structurés en combinant le scraping de sites en live avec des données SEO et marché.

## Évaluation initiale

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations qui n'y figurent pas.

Avant de profiler, confirme :

1. **URLs concurrents** — la liste des URLs de sites concurrents à profiler
2. **Ton produit** — ce que tu fais (si ce n'est pas dans le contexte product marketing)
3. **Niveau de profondeur** — quick scan (faits clés uniquement) ou deep profile (recherche complète)
4. **Zones de focus** — toute dimension spécifique à prioriser (ex. pricing, positionnement, force SEO, content strategy)

Si l'utilisateur fournit des URLs et que le contexte est disponible, procède sans demander.

---

## Principes fondamentaux

### 1. Faits plutôt qu'opinions
Chaque claim dans un profil doit être traçable à une source — contenu de page scrapé, données de reviews ou métriques SEO. Étiquette clairement les inférences.

### 2. Structuré et comparable
Tous les profils suivent le même template afin de pouvoir être comparés côte à côte. La cohérence importe plus que la complétude sur un profil unique.

### 3. Données à jour
Les profils sont des snapshots. Inclus toujours la date de génération. Signale tout ce qui semble obsolète (ex. "page pricing dernière mise à jour 2023").

### 4. Évaluation honnête
N'exagère pas les faiblesses des concurrents et ne minimise pas leurs forces. Des profils précis sont des profils utiles.

---

## Sauvegarde des données brutes

Avant de synthétiser le profil, persiste toutes les données brutes de scrape, SEO et reviews sur disque afin qu'elles puissent être relues, auditées ou réutilisées plus tard sans relancer d'appels API coûteux.

**Layout de répertoires** (relatif à la racine du projet) :

```
competitor-profiles/
├── raw/
│   └── <competitor-slug>/
│       └── <YYYY-MM-DD>/
│           ├── scrapes/    # un fichier .md par page scrapée (homepage.md, pricing.md, ...)
│           ├── seo/        # un fichier .json par appel DataForSEO (backlinks-summary.json, ranked-keywords.json, ...)
│           └── reviews/    # un fichier .md ou .json par source de reviews (g2.md, capterra.md, ...)
├── <competitor-slug>.md    # profil synthétisé final
└── _summary.md             # résumé cross-concurrents
```

Règles :

- `<competitor-slug>` est en minuscules, avec tirets (ex. `responsehub`, `safe-base`)
- `<YYYY-MM-DD>` est la date à laquelle les données ont été récupérées — permet de re-runner et de differ les snapshots dans le temps
- Sauvegarde chaque scrape Firecrawl en markdown brut dans `scrapes/<page-name>.md`
- Sauvegarde chaque réponse DataForSEO en JSON brut dans `seo/<endpoint-name>.json`
- Sauvegarde chaque source de reviews dans `reviews/<source>.md` (texte nettoyé) ou `.json` (brut)
- Crée toujours un dossier de date fraîche à chaque nouveau run ; n'écrase jamais les données d'une date antérieure

Le profil synthétisé (`<competitor-slug>.md`) doit référencer le dossier de données brutes à partir duquel il a été construit dans sa section `## Raw Data Sources`.

---

## Processus de recherche

### Phase 1 : Site Scraping (Firecrawl)

Pour chaque URL concurrent, scrape les pages clés pour extraire positionnement, fonctionnalités, pricing et messaging.

#### Étape 1 : mapper le site

Utilise **Firecrawl Map** pour découvrir la structure du site du concurrent et identifier les pages clés :

```
firecrawl_map → URL du concurrent
```

À partir du map, identifie et priorise ces types de pages :
- Page d'accueil
- Page de pricing
- Pages features / produit
- Page À propos / entreprise
- Blog (niveau racine, pour les signaux de content strategy)
- Page clients / études de cas
- Page intégrations
- Changelog / nouveautés (s'il existe)

#### Étape 2 : scraper les pages clés

Utilise **Firecrawl Scrape** sur chaque page identifiée :

```
firecrawl_scrape → chaque URL de page clé
```

Sauvegarde chaque résultat dans `competitor-profiles/raw/<competitor-slug>/<YYYY-MM-DD>/scrapes/<page-name>.md` avant d'extraire les champs.

Extrais de chaque page :

| Page | Ce qu'il faut extraire |
|------|------------------------|
| **Page d'accueil** | Headline, subheadline, value proposition, CTA principal, claims de social proof, signaux d'audience cible |
| **Pricing** | Tiers, prix, breakdown de fonctionnalités par tier, options de facturation, détails du tier gratuit/essai, signaux de pricing enterprise |
| **Features** | Catégories de fonctionnalités, capacités clés, façon de décrire chaque fonctionnalité, signaux de screenshots/démos |
| **About** | Histoire de fondation, taille d'équipe, levée de fonds, mission statement, headquarters |
| **Customers** | Clients nommés, logos, industries servies, thèmes des études de cas |
| **Intégrations** | Nombre d'intégrations, intégrations clés, catégories |
| **Changelog** | Vélocité de release, zones de focus récentes, signaux de direction produit |

#### Étape 3 : scraper les reviews concurrents (optionnel mais à forte valeur)

Utilise **Firecrawl Scrape** ou **Firecrawl Search** pour trouver :
- Page de reviews G2 du concurrent
- Page de reviews Capterra
- Page de lancement Product Hunt
- Profil TrustRadius

Sauvegarde chaque page de reviews scrapée dans `competitor-profiles/raw/<competitor-slug>/<YYYY-MM-DD>/reviews/<source>.md`. Puis extrais : note globale, nombre de reviews, thèmes d'éloges courants, thèmes de plaintes courants et 3-5 citations représentatives.

---

### Phase 2 : SEO & Market Data (DataForSEO)

Utilise les outils MCP DataForSEO pour recueillir de la competitive intelligence quantitative. Sauvegarde chaque réponse brute en JSON dans `competitor-profiles/raw/<competitor-slug>/<YYYY-MM-DD>/seo/<endpoint-name>.json` avant de la parser dans le profil. Pour la liste complète des outils MCP utilisés dans ce skill (Firecrawl + DataForSEO) et des exemples d'appels, voir [references/tool-reference.md](references/tool-reference.md).

#### Authority de domaine et backlinks

Utilise **backlinks_summary** pour obtenir :
- Domain rank / score d'authority
- Total des backlinks
- Nombre de referring domains
- Spam score

Utilise **backlinks_referring_domains** pour :
- Top referring domains (signaux de qualité)
- Patterns d'acquisition de liens

#### Intelligence keywords et trafic

Utilise **dataforseo_labs_google_ranked_keywords** pour obtenir :
- Total des keywords organiques en ranking
- Keywords dans le top 3, top 10, top 100
- Trafic organique estimé

Utilise **dataforseo_labs_google_domain_rank_overview** pour :
- Métriques organiques au niveau domaine
- Valeur estimée du trafic
- Top keywords par trafic

Utilise **dataforseo_labs_google_keywords_for_site** pour découvrir :
- Quels keywords ils ciblent
- Gaps de contenu vs ton site

#### Données de positionnement concurrentiel

Utilise **dataforseo_labs_google_competitors_domain** pour trouver :
- Leurs concurrents organiques les plus proches (peut révéler des concurrents que tu n'avais pas considérés)
- Données de chevauchement marché

Utilise **dataforseo_labs_google_relevant_pages** pour trouver :
- Leurs pages à plus fort trafic
- Le contenu qui génère le plus de valeur organique

---

### Phase 3 : Synthèse

Combine le contenu scrapé avec les données SEO pour construire le profil. Croise les claims (ex. s'ils prétendent "10 000 clients" sur le site, vérifie si leur profil de trafic/backlinks supporte cette échelle).

---

## Format de sortie

### Structure du document de profil

Génère un fichier markdown par concurrent, sauvegardé dans un répertoire `competitor-profiles/` à la racine du projet.

**Nom de fichier** : `competitor-profiles/[nom-du-concurrent].md`

**Pour les templates complets de profil et de résumé** : voir [references/templates.md](references/templates.md)

Chaque profil suit cette structure :

```markdown
# [Nom du concurrent] — Profil concurrent

**URL** : [site]
**Généré** : [date]
**Profondeur** : [quick scan / deep profile]

---

## En un coup d'œil

| Métrique | Valeur |
|----------|--------|
| Tagline | [depuis la page d'accueil] |
| Fondé | [année] |
| Headquarters | [localisation] |
| Taille d'équipe | [estimation] |
| Funding | [si connu] |
| Domain rank | [depuis DataForSEO] |
| Trafic organique estimé | [mensuel] |
| Referring domains | [nombre] |
| Keywords organiques | [nombre] |

---

## Positionnement et messaging

**Value proposition principale** : [headline + subheadline depuis la page d'accueil]

**Audience cible** : [à qui ils parlent, basé sur l'analyse de la copy]

**Angle de positionnement** : [comment ils se positionnent — ex. "simplicity-first", "enterprise-grade", "all-in-one"]

**Thèmes clés de messaging** :
- [thème 1 — avec page source]
- [thème 2]
- [thème 3]

---

## Produit et fonctionnalités

### Capacités principales
- [capacité 1] — [brève description depuis leur site]
- [capacité 2]
- ...

### Différenciateurs notables
- [ce qu'ils mettent en avant comme unique]

### Intégrations
- [nombre] intégrations
- Clés : [liste top 5-10]

### Signaux de direction produit
- [basé sur le changelog / les releases récentes]

---

## Pricing

| Tier | Prix | Inclusions clés |
|------|------|------------------|
| [Free/Starter] | [prix] | [ce qui est inclus] |
| [Pro/Growth] | [prix] | [ce qui est inclus] |
| [Enterprise] | [prix] | [ce qui est inclus] |

**Facturation** : [mensuel/annuel, remise pour annuel]
**Free trial** : [oui/non, durée]
**À noter** : [particularités de pricing — per-seat, usage-based, coûts cachés]

---

## Clients et social proof

**Clients nommés** : [liste des logos notables]
**Industries** : [industries principales servies]
**Thèmes des études de cas** : [résultats mis en avant]
**Notes de reviews** :
- G2 : [note] ([nombre] reviews)
- Capterra : [note] ([nombre] reviews)

---

## SEO et content strategy

**Force organique** :
- Trafic organique mensuel estimé : [nombre]
- Keywords organiques (top 10) : [nombre]
- Valeur du trafic organique : $[estimée]

**Top pages organiques** (par trafic estimé) :
1. [URL de page] — [keyword] — [trafic estimé]
2. [URL de page] — [keyword] — [trafic estimé]
3. [URL de page] — [keyword] — [trafic estimé]

**Signaux de content strategy** :
- Fréquence de publication blog : [estimation]
- Types de contenu principaux : [guides, comparaisons, templates, etc.]
- Zones de focus de contenu : [sujets sur lesquels ils investissent]

**Profil de backlinks** :
- Referring domains : [nombre]
- Top sites référents : [liste 5]
- Pattern d'acquisition de liens : [en croissance/stable/en déclin]

---

## Forces et faiblesses

### Forces
- [force 1 — avec source de preuve]
- [force 2]
- [force 3]

### Faiblesses
- [faiblesse 1 — avec source de preuve]
- [faiblesse 2]
- [faiblesse 3]

---

## Implications concurrentielles pour [Ton produit]

**Où ils sont forts vs nous** : [zones où ce concurrent a un avantage]

**Où nous sommes forts vs eux** : [zones où tu as un avantage]

**Opportunités** : [gaps dans leur offre ou positionnement que nous pouvons exploiter]

**Menaces** : [zones où ils s'améliorent ou gagnent du terrain]

---

## Raw Data Sources

- Page d'accueil scrapée : [date]
- Page pricing scrapée : [date]
- Données SEO récupérées : [date]
- Données de reviews récupérées : [date, sources]
```

---

### Document de résumé

Après avoir profilé tous les concurrents, génère un `competitor-profiles/_summary.md` qui inclut :

1. **Vue d'ensemble du paysage concurrentiel** — un paragraphe résumant le terrain concurrentiel
2. **Tableau de comparaison** — métriques clés côte à côte pour tous les concurrents profilés
3. **Carte de positionnement** — où se situe chaque concurrent (ex. simple↔complexe, bon marché↔premium)
4. **Takeaways clés** — 3-5 observations stratégiques issues de la recherche
5. **Gaps et opportunités** — où le marché est sous-servi

---

## Quick Scan vs Deep Profile

### Quick Scan (plus rapide, coût plus faible)
- Scrape : page d'accueil + page de pricing uniquement
- SEO : domain rank overview + résumé des ranked keywords
- Skip : reviews, technology stack, détails backlinks
- Output : profil abrégé (At a Glance + Positionnement + Pricing + résumé SEO)

### Deep Profile (complet)
- Scrape : toutes les pages clés + sites de reviews
- SEO : analyse complète des backlinks + intelligence keywords + découverte concurrentielle
- Inclure : technology stack, analyse de content strategy, review mining
- Output : template complet de profil

Par défaut, fais un **quick scan** sauf si l'utilisateur demande un deep profile ou spécifie un petit nombre de concurrents (3 ou moins).

---

## Gestion de plusieurs concurrents

Lorsque tu profiles plus d'un concurrent :

1. **Parallélise le scraping** — scrape les pages d'accueil de tous les concurrents simultanément, puis les pages de pricing, etc.
2. **Utilise des métriques cohérentes** — pull les mêmes métriques DataForSEO pour chaque concurrent afin que les profils soient comparables
3. **Construis le résumé en dernier** — après que tous les profils individuels sont terminés
4. **Priorise par pertinence** — si l'utilisateur a 10+ concurrents, suggère de profiler les top 5 d'abord en fonction du chevauchement de domaine ou de la similarité marché

---

## Mise à jour des profils

Les profils sont des snapshots. Lors de la mise à jour :

- Vérifie d'abord les pages de pricing (les plus volatiles)
- Re-pull les métriques SEO (trafic et rankings shiftent chaque mois)
- Scanne le changelog pour les changements produit
- Mets à jour la date "Généré"
- Note ce qui a changé depuis le profil précédent dans une section `## Change Log` en bas

---

## Questions spécifiques à la tâche

À ne poser que si non répondues par le contexte ou l'input :

1. Quelles URLs de concurrents dois-je profiler ?
2. Quick scan ou deep profile ?
3. Des dimensions spécifiques sur lesquelles me concentrer (pricing, SEO, positionnement) ?
4. Dois-je comparer les findings avec ton produit ?

---

## Skills associés

- **competitor-alternatives** : pour créer des pages de comparaison/alternatives à partir de ces profils
- **customer-research** : pour miner les reviews et le sentiment communautaire en profondeur
- **content-strategy** : pour utiliser les gaps de contenu concurrentiels et planifier ton propre contenu
- **seo-audit** : pour auditer ton propre site relativement aux concurrents
- **sales-enablement** : pour transformer les profils en battle cards et collateral commercial
- **paid-ads** : pour analyser les stratégies pub des concurrents
- **pricing-strategy** : pour une analyse pricing plus approfondie informée par les profils concurrents
