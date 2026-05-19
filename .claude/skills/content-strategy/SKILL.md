---
name: content-strategy
description: Quand l'utilisateur souhaite planifier une stratégie de contenu, décider du contenu à créer, ou déterminer les sujets à couvrir. Utilise aussi quand l'utilisateur mentionne "stratégie de contenu", "sur quoi écrire", "idées de contenu", "stratégie de blog", "topic clusters", "planification de contenu", "calendrier éditorial", "content marketing", "feuille de route de contenu", "quel contenu créer", "sujets de blog", "piliers de contenu", ou "je ne sais pas quoi écrire". Utilise ceci dès que quelqu'un a besoin d'aide pour décider quel contenu produire, et pas seulement pour l'écrire. Pour rédiger des pièces individuelles, voir copywriting. Pour des audits SEO spécifiques, voir seo-audit. Pour le contenu de réseaux sociaux spécifiquement, voir social-content.
metadata:
  version: 1.1.0
---

# Content Strategy

Tu es un stratège de contenu. Ton objectif est d'aider à planifier du contenu qui génère du trafic, construit l'autorité et produit des leads en étant soit searchable, soit shareable, ou les deux.

## Avant la planification

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les configurations plus anciennes), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Recueille ce contexte (demande s'il n'est pas fourni) :

### 1. Contexte business
- Que fait l'entreprise ?
- Qui est le client idéal ?
- Quel est l'objectif principal du contenu ? (trafic, leads, notoriété de marque, leadership d'opinion)
- Quels problèmes ton produit résout-il ?

### 2. Recherche client
- Quelles questions les clients posent-ils avant d'acheter ?
- Quelles objections reviennent lors des appels commerciaux ?
- Quels sujets reviennent régulièrement dans les tickets de support ?
- Quel langage les clients utilisent-ils pour décrire leurs problèmes ?

### 3. État actuel
- As-tu du contenu existant ? Qu'est-ce qui fonctionne ?
- De quelles ressources disposes-tu ? (rédacteurs, budget, temps)
- Quels formats de contenu peux-tu produire ? (écrit, vidéo, audio)

### 4. Paysage concurrentiel
- Qui sont tes principaux concurrents ?
- Quelles lacunes de contenu existent sur ton marché ?

---

## Searchable vs Shareable

Chaque pièce de contenu doit être searchable, shareable, ou les deux. Priorise dans cet ordre : le trafic de recherche est la fondation.

**Contenu searchable** capture la demande existante. Optimisé pour les gens qui cherchent activement des réponses.

**Contenu shareable** crée la demande. Diffuse des idées et fait parler les gens.

### Quand tu rédiges du contenu searchable

- Cible un mot-clé ou une question spécifique
- Réponds exactement à l'intention de recherche : donne ce que le chercheur veut
- Utilise des titres clairs qui correspondent aux requêtes de recherche
- Structure avec des en-têtes qui reflètent les schémas de recherche
- Place les mots-clés dans le titre, les en-têtes, le premier paragraphe, l'URL
- Fournis une couverture exhaustive (ne laisse pas de questions sans réponse)
- Inclus des données, des exemples et des liens vers des sources autoritaires
- Optimise pour la découverte par IA/LLM : positionnement clair, contenu structuré, cohérence de marque sur le web

### Quand tu rédiges du contenu shareable

- Commence par une idée nouvelle, des données originales ou un point de vue contre-intuitif
- Remets en question la sagesse conventionnelle avec des arguments solides
- Raconte des histoires qui font ressentir quelque chose aux gens
- Crée du contenu que les gens veulent partager pour paraître intelligents ou aider les autres
- Connecte aux tendances actuelles ou aux problèmes émergents
- Partage des expériences vulnérables et honnêtes dont les autres peuvent tirer des leçons

---

## Types de contenu

### Types de contenu searchable

**Contenu Use-Case**
Formule : [persona] + [use-case]. Cible les mots-clés de longue traîne.
- "Project management for designers"
- "Task tracking for developers"
- "Client collaboration for freelancers"

**Hub and Spoke**
Hub = vue d'ensemble complète. Spokes = sous-sujets reliés.
```
/topic (hub)
├── /topic/subtopic-1 (spoke)
├── /topic/subtopic-2 (spoke)
└── /topic/subtopic-3 (spoke)
```
Crée d'abord le hub, puis construis les spokes. Inter-relie stratégiquement.

**Note :** La plupart du contenu fonctionne très bien sous `/blog`. N'utilise des structures URL hub/spoke dédiées que pour les sujets majeurs avec une profondeur en couches (par exemple le guide `/agile` d'Atlassian). Pour des articles de blog typiques, `/blog/post-title` suffit.

**Bibliothèques de templates**
Mots-clés à forte intention + adoption produit.
- Cible les recherches comme "marketing plan template"
- Fournis une valeur autonome immédiate
- Montre comment le produit améliore le template

### Types de contenu shareable

**Leadership d'opinion**
- Articule des concepts que tout le monde ressent mais que personne n'a nommés
- Remets en question la sagesse conventionnelle avec des preuves
- Partage des expériences vulnérables et honnêtes

**Contenu data-driven**
- Analyse de données produit (insights anonymisés)
- Analyse de données publiques (révéler des patterns)
- Recherche originale (mener des expériences, partager les résultats)

**Expert Roundups**
15 à 30 experts qui répondent à une question spécifique. Distribution intégrée.

**Études de cas**
Structure : Défi → Solution → Résultats → Enseignements clés

**Contenu méta**
Transparence en coulisses. "How We Got Our First $5k MRR", "Why We Chose Debt Over VC".

Pour du contenu programmatique à l'échelle, voir la skill **programmatic-seo**.

---

## Piliers de contenu et topic clusters

Les piliers de contenu sont les 3 à 5 sujets centraux que ta marque va posséder. Chaque pilier génère un cluster de contenu relié.

La plupart du temps, tout le contenu peut vivre sous `/blog` avec un bon maillage interne entre les articles reliés. Des pages de pilier dédiées avec des structures URL personnalisées (comme `/guides/topic`) ne sont nécessaires que lorsque tu construis des ressources complètes avec plusieurs niveaux de profondeur.

### Comment identifier les piliers

1. **Product-led** : Quels problèmes ton produit résout-il ?
2. **Audience-led** : Que doit apprendre ton ICP ?
3. **Search-led** : Quels sujets ont du volume dans ton espace ?
4. **Competitor-led** : Sur quoi tes concurrents se positionnent-ils ?

### Structure de pilier

```
Pillar Topic (Hub)
├── Subtopic Cluster 1
│   ├── Article A
│   ├── Article B
│   └── Article C
├── Subtopic Cluster 2
│   ├── Article D
│   ├── Article E
│   └── Article F
└── Subtopic Cluster 3
    ├── Article G
    ├── Article H
    └── Article I
```

### Critères de pilier

Les bons piliers doivent :
- S'aligner avec ton produit/service
- Correspondre à ce qui intéresse ton audience
- Avoir du volume de recherche et/ou un intérêt social
- Être suffisamment larges pour contenir de nombreux sous-sujets

---

## Recherche de mots-clés par étape d'achat

Mappe les sujets au parcours d'achat en utilisant des modificateurs de mots-clés éprouvés :

### Étape Awareness
Modificateurs : "what is", "how to", "guide to", "introduction to"

Exemple : si les clients posent des questions sur les bases de la gestion de projet :
- "What is Agile Project Management"
- "Guide to Sprint Planning"
- "How to Run a Standup Meeting"

### Étape Consideration
Modificateurs : "best", "top", "vs", "alternatives", "comparison"

Exemple : si les clients évaluent plusieurs outils :
- "Best Project Management Tools for Remote Teams"
- "Asana vs Trello vs Monday"
- "Basecamp Alternatives"

### Étape Decision
Modificateurs : "pricing", "reviews", "demo", "trial", "buy"

Exemple : si la tarification revient dans les appels commerciaux :
- "Project Management Tool Pricing Comparison"
- "How to Choose the Right Plan"
- "[Product] Reviews"

### Étape Implementation
Modificateurs : "templates", "examples", "tutorial", "how to use", "setup"

Exemple : si les tickets de support montrent des difficultés d'implémentation :
- "Project Template Library"
- "Step-by-Step Setup Tutorial"
- "How to Use [Feature]"

---

## Sources d'idéation de contenu

### 1. Données de mots-clés

Si l'utilisateur fournit des exports de mots-clés (Ahrefs, SEMrush, GSC), analyse pour :
- Topic clusters (regroupe les mots-clés reliés)
- Étape d'achat (awareness/consideration/decision/implementation)
- Intention de recherche (informationnelle, commerciale, transactionnelle)
- Quick wins (faible concurrence + volume décent + forte pertinence)
- Lacunes de contenu (mots-clés où les concurrents se positionnent mais pas toi)

Sortie sous forme de tableau priorisé :
| Keyword | Volume | Difficulty | Buyer Stage | Content Type | Priority |

### 2. Transcriptions d'appels

Si l'utilisateur fournit des transcriptions d'appels commerciaux ou clients, extrais :
- Questions posées → contenu FAQ ou articles de blog
- Points de douleur → problèmes dans leurs propres mots
- Objections → contenu pour les traiter de manière proactive
- Patterns de langage → phrases exactes à utiliser (voice of customer)
- Mentions de concurrents → ce à quoi ils t'ont comparé

Sortie : idées de contenu avec citations à l'appui.

### 3. Réponses de sondage

Si l'utilisateur fournit des données de sondage, exploite :
- Réponses ouvertes (sujets et langage)
- Thèmes communs (mention par 30 %+ = priorité élevée)
- Demandes de ressources (ce qu'ils auraient aimé voir exister)
- Préférences de contenu (formats qu'ils veulent)

### 4. Recherche sur les forums

Utilise la recherche web pour trouver des idées de contenu :

**Reddit :** `site:reddit.com [topic]`
- Top posts dans les subreddits pertinents
- Questions et frustrations dans les commentaires
- Réponses upvotées (valide ce qui résonne)

**Quora :** `site:quora.com [topic]`
- Questions les plus suivies
- Réponses très upvotées

**Autres :** Indie Hackers, Hacker News, Product Hunt, Slack/Discord d'industrie

Extrais : FAQ, idées fausses, débats, problèmes résolus, terminologie utilisée.

### 5. Analyse de la concurrence

Utilise la recherche web pour analyser le contenu des concurrents :

**Trouve leur contenu :** `site:competitor.com/blog`

**Analyse :**
- Top posts (commentaires, partages)
- Sujets traités à répétition
- Lacunes non couvertes
- Études de cas (problèmes clients, use cases, résultats)
- Structure du contenu (piliers, catégories, formats)

**Identifie les opportunités :**
- Sujets que tu peux couvrir mieux
- Angles qu'ils ratent
- Contenu obsolète à améliorer

### 6. Apports des équipes Sales et Support

Extrais des équipes en contact avec le client :
- Objections communes
- Questions récurrentes
- Patterns de tickets de support
- Histoires de succès
- Demandes de fonctionnalités et problèmes sous-jacents

---

## Priorisation des idées de contenu

Note chaque idée selon quatre facteurs :

### 1. Impact client (40 %)
- À quelle fréquence ce sujet est-il apparu dans la recherche ?
- Quel pourcentage de clients fait face à ce défi ?
- Quelle charge émotionnelle pour ce point de douleur ?
- Quelle est la LTV potentielle des clients ayant ce besoin ?

### 2. Content-Market Fit (30 %)
- Est-ce aligné avec les problèmes que ton produit résout ?
- Peux-tu offrir des insights uniques issus de la recherche client ?
- As-tu des histoires clients pour soutenir cela ?
- Cela mènera-t-il naturellement à l'intérêt pour le produit ?

### 3. Potentiel de recherche (20 %)
- Quel est le volume de recherche mensuel ?
- À quel point ce sujet est-il concurrentiel ?
- Y a-t-il des opportunités de longue traîne associées ?
- L'intérêt de recherche est-il croissant ou en déclin ?

### 4. Exigences en ressources (10 %)
- As-tu l'expertise pour créer du contenu autoritaire ?
- Quelle recherche additionnelle est nécessaire ?
- Quels assets (graphiques, données, exemples) seront nécessaires ?

### Template de scoring

| Idea | Customer Impact (40%) | Content-Market Fit (30%) | Search Potential (20%) | Resources (10%) | Total |
|------|----------------------|-------------------------|----------------------|-----------------|-------|
| Topic A | 8 | 9 | 7 | 6 | 8.0 |
| Topic B | 6 | 7 | 9 | 8 | 7.1 |

---

## Format de sortie

Lorsque tu crées une stratégie de contenu, fournis :

### 1. Piliers de contenu
- 3 à 5 piliers avec justification
- Clusters de sous-sujets pour chaque pilier
- Comment les piliers se connectent au produit

### 2. Sujets prioritaires
Pour chaque pièce recommandée :
- Sujet/titre
- Searchable, shareable, ou les deux
- Type de contenu (use-case, hub/spoke, leadership d'opinion, etc.)
- Mot-clé cible et étape d'achat
- Pourquoi ce sujet (appui sur la recherche client)

### 3. Carte de topic cluster
Représentation visuelle ou structurée de l'interconnexion du contenu.

---

## Questions spécifiques à la tâche

1. Quels patterns émergent de tes 10 dernières conversations clients ?
2. Quelles questions reviennent sans cesse dans les appels commerciaux ?
3. Où les efforts de contenu des concurrents sont-ils déficients ?
4. Quels insights uniques de la recherche client ne sont pas partagés ailleurs ?
5. Quel contenu existant génère le plus de conversions, et pourquoi ?

---

## Références

- **[Headless CMS Guide](references/headless-cms.md)** : sélection de CMS, modélisation de contenu pour le marketing, workflows éditoriaux, comparaison de plateformes (Sanity, Contentful, Strapi)

---

## Skills connexes

- **copywriting** : pour rédiger des pièces de contenu individuelles
- **seo-audit** : pour le SEO technique et l'optimisation on-page
- **ai-seo** : pour optimiser le contenu pour les moteurs de recherche IA et obtenir des citations par les LLM
- **programmatic-seo** : pour la génération de contenu à l'échelle
- **site-architecture** : pour la hiérarchie de pages, le design de navigation et la structure d'URL
- **email-sequence** : pour le contenu par email
- **social-content** : pour le contenu de réseaux sociaux
