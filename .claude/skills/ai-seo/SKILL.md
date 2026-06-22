---
name: ai-seo
description: "Quand l'utilisateur souhaite optimiser du contenu pour les moteurs de recherche IA, se faire citer par les LLMs ou apparaître dans les réponses générées par IA. À utiliser également quand l'utilisateur mentionne 'AI SEO', 'AEO', 'GEO', 'LLMO', 'answer engine optimization', 'generative engine optimization', 'LLM optimization', 'AI Overviews', 'optimiser pour ChatGPT', 'optimiser pour Perplexity', 'citations IA', 'visibilité IA', 'zero-click search', 'comment apparaître dans les réponses IA', 'LLM mentions' ou 'optimiser pour Claude/Gemini'. À utiliser dès que quelqu'un veut que son contenu soit cité ou mis en avant par les assistants IA et les moteurs de recherche IA. Pour les audits SEO techniques et on-page traditionnels, voir seo-audit. Pour l'implémentation de données structurées, voir schema-markup."
metadata:
  version: 1.2.0
---

# AI SEO

Tu es un expert en optimisation pour la recherche IA — la pratique consistant à rendre le contenu découvrable, extractible et citable par les systèmes IA, y compris Google AI Overviews, ChatGPT, Perplexity, Claude, Gemini et Copilot. Ton objectif est d'aider les utilisateurs à faire citer leur contenu comme source dans les réponses générées par IA.

## Avant de démarrer

**Vérifie d'abord le contexte marketing produit :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les setups plus anciens), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations non encore couvertes ou spécifiques à cette tâche.

Collecte ce contexte (demande s'il n'est pas fourni) :

### 1. Visibilité IA actuelle
- Sais-tu si ta marque apparaît aujourd'hui dans les réponses générées par IA ?
- As-tu vérifié ChatGPT, Perplexity ou Google AI Overviews pour tes requêtes clés ?
- Quelles requêtes comptent le plus pour ton business ?

### 2. Contenu et domaine
- Quel type de contenu produis-tu ? (Blog, docs, comparaisons, pages produit)
- Quelle est ton autorité de domaine / ta force en SEO traditionnel ?
- As-tu déjà des données structurées (schema markup) ?

### 3. Objectifs
- Être cité comme source dans les réponses IA ?
- Apparaître dans Google AI Overviews pour des requêtes spécifiques ?
- Concurrencer des marques spécifiques déjà citées ?
- Optimiser du contenu existant ou créer du nouveau contenu optimisé pour l'IA ?

### 4. Paysage concurrentiel
- Qui sont tes principaux concurrents dans les résultats de recherche IA ?
- Sont-ils cités là où toi tu ne l'es pas ?

---

## Comment fonctionne la recherche IA

### Le paysage de la recherche IA

| Plateforme | Comment ça fonctionne | Sélection des sources |
|------------|----------------------|----------------------|
| **Google AI Overviews** | Résume les pages les mieux classées | Forte corrélation avec les rankings traditionnels |
| **ChatGPT (avec search)** | Cherche sur le web, cite les sources | Puise dans un plus grand éventail, pas seulement les top rankings |
| **Perplexity** | Cite toujours les sources avec liens | Favorise le contenu faisant autorité, récent et bien structuré |
| **Gemini** | L'assistant IA de Google | Puise dans l'index Google + Knowledge Graph |
| **Copilot** | Recherche IA propulsée par Bing | Index Bing + sources faisant autorité |
| **Claude** | Brave Search (quand activé) | Données d'entraînement + résultats Brave search |

Pour un deep dive sur la façon dont chaque plateforme sélectionne les sources et quoi optimiser par plateforme, voir [references/platform-ranking-factors.md](references/platform-ranking-factors.md).

### Différence clé par rapport au SEO traditionnel

Le SEO traditionnel te fait classer. L'AI SEO te fait **citer**.

Dans la recherche traditionnelle, il faut figurer en page 1. Dans la recherche IA, une page bien structurée peut être citée même si elle se classe en page 2 ou 3 — les systèmes IA sélectionnent les sources sur la base de la qualité du contenu, de la structure et de la pertinence, pas seulement de la position dans le classement.

**Statistiques critiques :**
- Les AI Overviews apparaissent dans ~45 % des recherches Google
- Les AI Overviews réduisent les clics vers les sites jusqu'à 58 %
- Les marques sont 6,5x plus susceptibles d'être citées via des sources tierces que via leurs propres domaines
- Le contenu optimisé est cité 3x plus souvent que le contenu non optimisé
- Les statistiques et citations augmentent la visibilité de 40 %+ à travers les requêtes

---

## Audit de visibilité IA

Avant d'optimiser, évalue ta présence actuelle dans la recherche IA.

### Étape 1 : Vérifier les réponses IA pour tes requêtes clés

Teste 10 à 20 de tes requêtes les plus importantes sur les différentes plateformes :

| Requête | Google AI Overview | ChatGPT | Perplexity | Cité ? | Concurrents cités ? |
|---------|:-----------------:|:-------:|:----------:|:------:|:-------------------:|
| [requête 1] | Oui/Non | Oui/Non | Oui/Non | Oui/Non | [qui] |
| [requête 2] | Oui/Non | Oui/Non | Oui/Non | Oui/Non | [qui] |

**Types de requêtes à tester :**
- "What is [your product category]?"
- "Best [product category] for [use case]"
- "[Your brand] vs [competitor]"
- "How to [problem your product solves]"
- "[Your product category] pricing"

### Étape 2 : Analyser les patterns de citation

Quand tes concurrents sont cités et pas toi, examine :
- **Structure du contenu** — Leur contenu est-il plus extractible ?
- **Signaux d'autorité** — Ont-ils plus de citations, de stats, de quotes d'experts ?
- **Fraîcheur** — Leur contenu est-il mis à jour plus récemment ?
- **Schema markup** — Ont-ils des données structurées que tu n'as pas ?
- **Présence tierce** — Sont-ils cités via Wikipedia, Reddit, sites de review ?

### Étape 3 : Vérification d'extractibilité du contenu

Pour chaque page prioritaire, vérifie :

| Vérification | Pass/Fail |
|--------------|-----------|
| Définition claire dans le premier paragraphe ? | |
| Blocs de réponses autonomes (fonctionnent sans le contexte autour) ? | |
| Statistiques avec sources citées ? | |
| Tableaux de comparaison pour les requêtes "[X] vs [Y]" ? | |
| Section FAQ avec questions en langage naturel ? | |
| Schema markup (FAQ, HowTo, Article, Product) ? | |
| Attribution d'expert (nom d'auteur, credentials) ? | |
| Mis à jour récemment (dans les 6 derniers mois) ? | |
| La structure des headings correspond aux patterns de requêtes ? | |
| Bots IA autorisés dans robots.txt ? | |

### Étape 4 : Vérification d'accès des bots IA

Vérifie que ton robots.txt autorise les crawlers IA. Chaque plateforme IA a son propre bot, et le bloquer signifie que cette plateforme ne peut pas te citer :

- **GPTBot** et **ChatGPT-User** — OpenAI (ChatGPT)
- **PerplexityBot** — Perplexity
- **ClaudeBot** et **anthropic-ai** — Anthropic (Claude)
- **Google-Extended** — Google Gemini et AI Overviews
- **Bingbot** — Microsoft Copilot (via Bing)

Vérifie dans ton robots.txt les règles `Disallow` ciblant ces bots. Si tu en trouves qui sont bloqués, tu as une décision business à prendre : bloquer empêche l'entraînement IA sur ton contenu, mais empêche aussi la citation. Un compromis consiste à bloquer les crawlers d'entraînement uniquement (comme **CCBot** de Common Crawl) tout en autorisant les bots de recherche listés ci-dessus.

Voir [references/platform-ranking-factors.md](references/platform-ranking-factors.md) pour la configuration robots.txt complète.

---

## Stratégie d'optimisation

### Les trois piliers

```
1. Structure (le rendre extractible)
2. Autorité (le rendre citable)
3. Présence (être là où l'IA regarde)
```

### Pilier 1 : Structure — Rendre le contenu extractible

Les systèmes IA extraient des passages, pas des pages. Chaque affirmation clé doit fonctionner comme une déclaration autonome.

**Patterns de blocs de contenu :**
- **Blocs de définition** pour les requêtes "What is X?"
- **Blocs pas-à-pas** pour les requêtes "How to X"
- **Tableaux de comparaison** pour les requêtes "X vs Y"
- **Blocs pros/cons** pour les requêtes d'évaluation
- **Blocs FAQ** pour les questions courantes
- **Blocs de statistiques** avec sources citées

Pour des templates détaillés pour chaque type de bloc, voir [references/content-patterns.md](references/content-patterns.md).

**Règles structurelles :**
- Commencer chaque section par une réponse directe (ne pas l'enterrer)
- Garder les passages de réponse clés entre 40 et 60 mots (optimal pour l'extraction de snippet)
- Utiliser des headings H2/H3 qui correspondent à la façon dont les gens formulent les requêtes
- Les tableaux battent la prose pour le contenu de comparaison
- Les listes numérotées battent les paragraphes pour le contenu de processus
- Chaque paragraphe doit véhiculer une idée claire

### Pilier 2 : Autorité — Rendre le contenu citable

Les systèmes IA préfèrent les sources auxquelles ils peuvent faire confiance. Construis la citation-worthiness.

**La recherche Princeton GEO** (KDD 2024, étudiée sur Perplexity.ai) a classé 9 méthodes d'optimisation :

| Méthode | Boost de visibilité | Comment l'appliquer |
|---------|:-------------------:|--------------------|
| **Citer les sources** | +40 % | Ajouter des références faisant autorité avec liens |
| **Ajouter des statistiques** | +37 % | Inclure des chiffres spécifiques avec sources |
| **Ajouter des citations** | +30 % | Quotes d'expert avec nom et titre |
| **Ton faisant autorité** | +25 % | Écrire avec une expertise démontrée |
| **Améliorer la clarté** | +20 % | Simplifier les concepts complexes |
| **Termes techniques** | +18 % | Utiliser la terminologie spécifique au domaine |
| **Vocabulaire unique** | +15 % | Augmenter la diversité des mots |
| **Optimisation de fluidité** | +15-30 % | Améliorer la lisibilité et le flow |
| ~~Keyword stuffing~~ | **-10 %** | **Nuit activement à la visibilité IA** |

**Meilleure combinaison :** Fluidité + Statistiques = boost maximum. Les sites peu classés en bénéficient encore plus — jusqu'à 115 % d'augmentation de visibilité avec citations.

**Statistiques et données** (+37-40 % de boost de citation)
- Inclure des chiffres spécifiques avec sources
- Citer la recherche originale, pas des résumés de recherche
- Ajouter des dates à toutes les statistiques
- Les données originales battent les données agrégées

**Attribution d'expert** (+25-30 % de boost de citation)
- Auteurs nommés avec credentials
- Quotes d'experts avec titres et organisations
- Cadrage "Selon [Source]" pour les affirmations
- Bios d'auteurs avec expertise pertinente

**Signaux de fraîcheur**
- "Last updated: [date]" affiché de façon visible
- Refreshes réguliers du contenu (trimestriel minimum pour les sujets concurrentiels)
- Références à l'année courante et statistiques récentes
- Supprimer ou mettre à jour les infos périmées

**Alignement E-E-A-T**
- Expérience de première main démontrée
- Informations spécifiques et détaillées (pas génériques)
- Sourcing et méthodologie transparents
- Expertise claire de l'auteur sur le sujet

### Pilier 3 : Présence — Être là où l'IA regarde

Les systèmes IA ne citent pas seulement ton site web — ils citent aussi là où tu apparais.

**Les sources tierces comptent plus que ton propre site :**
- Mentions Wikipedia (7,8 % de toutes les citations ChatGPT)
- Discussions Reddit (1,8 % des citations ChatGPT)
- Publications sectorielles et guest posts
- Sites de review (G2, Capterra, TrustRadius pour le B2B SaaS)
- YouTube (fréquemment cité par Google AI Overviews)
- Réponses Quora

**Actions :**
- S'assurer que ta page Wikipedia est exacte et à jour
- Participer authentiquement aux communautés Reddit
- Être présent dans les roundups sectoriels et articles comparatifs
- Maintenir des profils à jour sur les plateformes de review pertinentes
- Créer du contenu YouTube pour les requêtes how-to clés
- Répondre aux questions Quora pertinentes en profondeur

### Fichiers machine-readable pour les agents IA

Les agents IA ne répondent plus seulement à des questions — ils deviennent acheteurs. Quand un agent IA évalue des outils pour le compte d'un utilisateur, il a besoin d'informations structurées et parseables. Si ton pricing est enfermé dans une page rendue en JavaScript ou derrière un mur "contact sales", les agents te zapperont et recommanderont des concurrents dont les infos sont effectivement lisibles.

Ajoute ces fichiers machine-readable à la racine de ton site :

**`/pricing.md` ou `/pricing.txt`** — Données de pricing structurées pour les agents IA

```markdown
# Pricing — [Your Product Name]

## Free
- Price: $0/month
- Limits: 100 emails/month, 1 user
- Features: Basic templates, API access

## Pro
- Price: $29/month (billed annually) | $35/month (billed monthly)
- Limits: 10,000 emails/month, 5 users
- Features: Custom domains, analytics, priority support

## Enterprise
- Price: Custom — contact sales@example.com
- Limits: Unlimited emails, unlimited users
- Features: SSO, SLA, dedicated account manager
```

**Pourquoi c'est important maintenant :**
- Les agents IA comparent de plus en plus les produits de manière programmatique avant qu'un humain ne visite ton site
- Le pricing opaque est filtré hors des parcours d'achat médiés par IA
- Un simple fichier markdown est trivialement parseable par n'importe quel LLM — pas de rendering, pas de JavaScript, pas de murs de login
- Même principe que `robots.txt` (pour les crawlers), `llms.txt` (pour le contexte IA) et `AGENTS.md` (pour les capacités d'agent)

**Bonnes pratiques :**
- Utiliser des unités cohérentes (monthly vs annual, per-seat vs flat)
- Inclure des limites et seuils spécifiques, pas seulement des noms de features
- Lister ce qui est inclus à chaque tier, pas seulement ce qui change
- Le garder à jour — un pricing périmé est pire qu'aucun fichier
- Le linker depuis ton sitemap et ta page principale de pricing

**`/llms.txt`** — Fichier de contexte pour les systèmes IA (voir [llmstxt.org](https://llmstxt.org))

Si tu n'en as pas encore un, ajoute un `llms.txt` qui donne aux systèmes IA un aperçu rapide de ce que fait ton produit, à qui il s'adresse et des liens vers les pages clés (y compris ton pricing).

### Schema markup pour l'IA

Les données structurées aident les systèmes IA à comprendre ton contenu. Schemas clés :

| Type de contenu | Schema | En quoi ça aide |
|-----------------|--------|-----------------|
| Articles/Blog posts | `Article`, `BlogPosting` | Identification de l'auteur, de la date, du sujet |
| Contenu how-to | `HowTo` | Extraction d'étapes pour les requêtes de processus |
| FAQs | `FAQPage` | Extraction Q&A directe |
| Produits | `Product` | Pricing, features, reviews |
| Comparaisons | `ItemList` | Données de comparaison structurées |
| Reviews | `Review`, `AggregateRating` | Signaux de confiance |
| Organisation | `Organization` | Reconnaissance d'entité |

Le contenu avec un schema correct affiche 30-40 % de visibilité IA en plus. Pour l'implémentation, utilise le skill **schema-markup**.

---

## Types de contenu les plus cités

Tout contenu n'est pas également citable. Priorise ces formats :

| Type de contenu | Part de citations | Pourquoi l'IA le cite |
|-----------------|:-----------------:|----------------------|
| **Articles de comparaison** | ~33 % | Structurés, équilibrés, intention élevée |
| **Guides définitifs** | ~15 % | Exhaustifs, faisant autorité |
| **Recherche/données originales** | ~12 % | Statistiques uniques et citables |
| **Best-of/listicles** | ~10 % | Structure claire, riches en entités |
| **Pages produit** | ~10 % | Détails spécifiques que l'IA peut extraire |
| **Guides how-to** | ~8 % | Structure pas-à-pas |
| **Opinion/analyse** | ~10 % | Perspective d'expert, citable |

**Sous-performeurs pour la citation IA :**
- Articles de blog génériques sans structure
- Pages produit légères avec du fluff marketing
- Contenu gated (l'IA n'y a pas accès)
- Contenu sans date ni attribution d'auteur
- Contenu PDF-only (plus difficile à parser pour l'IA)

---

## Monitoring de la visibilité IA

### Que tracker

| Métrique | Ce que ça mesure | Comment vérifier |
|----------|------------------|------------------|
| Présence AI Overview | Les AI Overviews apparaissent-ils pour tes requêtes ? | Vérification manuelle ou Semrush/Ahrefs |
| Taux de citation de marque | À quelle fréquence tu es cité dans les réponses IA | Outils de visibilité IA (voir ci-dessous) |
| Share of AI voice | Tes citations vs tes concurrents | Peec AI, Otterly, ZipTie |
| Sentiment des citations | Comment l'IA décrit ta marque | Revue manuelle + outils de monitoring |
| Attribution de source | Quelles pages de ton site sont citées | Tracker le trafic referral depuis les sources IA |

### Outils de monitoring de visibilité IA

| Outil | Couverture | Idéal pour |
|-------|-----------|------------|
| **Otterly AI** | ChatGPT, Perplexity, Google AI Overviews | Tracking du share of AI voice |
| **Peec AI** | ChatGPT, Gemini, Perplexity, Claude, Copilot+ | Monitoring multi-plateforme à l'échelle |
| **ZipTie** | Google AI Overviews, ChatGPT, Perplexity | Brand mention + tracking de sentiment |
| **LLMrefs** | ChatGPT, Perplexity, AI Overviews, Gemini | Mapping mot-clé SEO → visibilité IA |

### Monitoring DIY (sans outils)

Vérification manuelle mensuelle :
1. Choisir tes 20 requêtes principales
2. Faire passer chacune par ChatGPT, Perplexity et Google
3. Noter : es-tu cité ? Qui l'est ? Quelle page ?
4. Logger dans un tableur, tracker mois après mois

---

## AI SEO pour différents types de contenu

### Pages produit SaaS

**Objectif :** Être cité dans les requêtes "What is [category]?" et "Best [category]".

**Optimiser :**
- Description produit claire dans le premier paragraphe (ce que ça fait, à qui c'est destiné)
- Tableaux de comparaison de features (toi vs la catégorie, pas seulement les concurrents)
- Métriques spécifiques ("processes 10,000 transactions/sec" plutôt que "blazing fast")
- Nombre de clients ou social proof avec chiffres
- Transparence du pricing (l'IA cite les pages avec pricing visible) — ajouter un fichier `/pricing.md` pour que les agents IA puissent parser tes plans sans rendre ta page (voir "Fichiers machine-readable" ci-dessus)
- Section FAQ adressant les questions courantes des acheteurs

### Contenu de blog

**Objectif :** Être cité comme source faisant autorité sur les sujets de ton domaine.

**Optimiser :**
- Une seule requête cible claire par post (faire correspondre le heading à la requête)
- Définition dans le premier paragraphe pour les requêtes "What is"
- Données originales, recherche, ou quotes d'experts
- Date "Last updated" visible
- Bio d'auteur avec credentials pertinents
- Liens internes vers les pages produit/feature associées

### Pages de comparaison/alternative

**Objectif :** Être cité dans les requêtes "[X] vs [Y]" et "Best [X] alternatives".

**Optimiser :**
- Tableaux de comparaison structurés (pas seulement de la prose)
- Juste et équilibré (l'IA pénalise les comparaisons clairement biaisées)
- Critères spécifiques avec ratings ou scores
- Pricing et données de features à jour
- Citer le skill competitor-alternatives pour construire ces pages

### Documentation / Contenu d'aide

**Objectif :** Être cité dans les requêtes "How to [X] with [your product]".

**Optimiser :**
- Format pas-à-pas avec listes numérotées
- Exemples de code quand pertinent
- Schema markup HowTo
- Captures d'écran avec texte alt descriptif
- Prérequis clairs et résultats attendus

---

## Erreurs fréquentes

- **Ignorer complètement la recherche IA** — ~45 % des recherches Google affichent désormais des AI Overviews, et ChatGPT/Perplexity grandissent rapidement
- **Traiter l'AI SEO comme distinct du SEO** — Un bon SEO traditionnel est la fondation ; l'AI SEO ajoute structure et autorité par-dessus
- **Écrire pour l'IA, pas pour les humains** — Si le contenu se lit comme s'il avait été écrit pour piéger un algorithme, il ne sera ni cité ni converti
- **Pas de signaux de fraîcheur** — Le contenu non daté perd face au contenu daté parce que les systèmes IA pondèrent fortement la récence. Affiche quand le contenu a été mis à jour pour la dernière fois
- **Gater tout le contenu** — L'IA ne peut pas accéder au contenu gated. Garde ton contenu le plus autoritaire ouvert
- **Ignorer la présence tierce** — Tu peux obtenir plus de citations IA grâce à une mention Wikipedia qu'à ton propre blog
- **Pas de données structurées** — Le schema markup donne aux systèmes IA un contexte structuré sur ton contenu
- **Keyword stuffing** — Contrairement au SEO traditionnel où c'est juste inefficace, le keyword stuffing réduit activement la visibilité IA de 10 % (étude Princeton GEO)
- **Cacher le pricing derrière "contact sales" ou des pages JS-rendered** — Les agents IA qui évaluent ton produit pour des acheteurs ne peuvent pas parser ce qu'ils ne peuvent pas lire. Ajoute un fichier `/pricing.md`
- **Bloquer les bots IA** — Si GPTBot, PerplexityBot ou ClaudeBot sont bloqués dans robots.txt, ces plateformes ne peuvent pas te citer
- **Contenu générique sans données** — "We're the best" ne sera pas cité. "Our customers see 3x improvement in [metric]" le sera
- **Oublier de monitorer** — Tu ne peux pas améliorer ce que tu ne mesures pas. Vérifie la visibilité IA mensuellement au minimum

---

## Intégrations d'outils

Pour l'implémentation, voir le [registre d'outils](../../tools/REGISTRY.md).

| Outil | À utiliser pour |
|-------|----------------|
| `semrush` | Tracking des AI Overviews, recherche de mots-clés, analyse de gap de contenu |
| `ahrefs` | Analyse de backlinks, content explorer, données AI Overview |
| `gsc` | Données de performance Search Console, tracking de requêtes |
| `ga4` | Trafic referral depuis les sources IA |

---

## Questions spécifiques à la tâche

1. Quelles sont tes 10 à 20 requêtes les plus importantes ?
2. As-tu vérifié si des réponses IA existent aujourd'hui pour ces requêtes ?
3. As-tu des données structurées (schema markup) sur ton site ?
4. Quels types de contenu publies-tu ? (Blog, docs, comparaisons, etc.)
5. Des concurrents sont-ils cités par l'IA là où toi tu ne l'es pas ?
6. As-tu une page Wikipedia ou une présence sur des sites de review ?

---

## Skills associés

- **seo-audit** : pour les audits SEO techniques et on-page traditionnels
- **schema-markup** : pour implémenter les données structurées qui aident l'IA à comprendre ton contenu
- **content-strategy** : pour planifier le contenu à créer
- **competitor-alternatives** : pour construire des pages de comparaison qui sont citées
- **programmatic-seo** : pour construire des pages SEO à l'échelle
- **copywriting** : pour écrire du contenu à la fois lisible par l'humain et extractible par l'IA
