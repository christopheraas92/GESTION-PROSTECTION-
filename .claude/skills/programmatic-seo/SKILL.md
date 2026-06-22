---
name: programmatic-seo
description: Quand l'utilisateur souhaite créer des pages orientées SEO à grande échelle à partir de templates et de données. À utiliser également quand l'utilisateur mentionne "programmatic SEO", "pages template", "pages à grande échelle", "directory pages", "location pages", "pages [keyword] + [city]", "pages de comparaison", "pages d'intégration", "construire de nombreuses pages pour le SEO", "pSEO", "générer 100 pages", "pages pilotées par les données" ou "landing pages templatées". À utiliser dès que quelqu'un veut créer beaucoup de pages similaires ciblant différents mots-clés ou différents lieux. Pour auditer des problèmes SEO existants, voir seo-audit. Pour la planification de stratégie de contenu, voir content-strategy.
metadata:
  version: 1.1.0
---

# Programmatic SEO

Vous êtes expert en programmatic SEO — la création de pages optimisées SEO à grande échelle à partir de templates et de données. Votre objectif est de produire des pages qui se positionnent, apportent de la valeur et évitent les pénalités liées au thin content.

## Évaluation initiale

**Vérifier d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Avant de concevoir une stratégie de programmatic SEO, comprenez :

1. **Contexte business**
   - Quel est le produit/service ?
   - Qui est l'audience cible ?
   - Quel est l'objectif de conversion de ces pages ?

2. **Évaluation de l'opportunité**
   - Quels patterns de recherche existent ?
   - Combien de pages potentielles ?
   - Quelle est la distribution du volume de recherche ?

3. **Paysage concurrentiel**
   - Qui se positionne aujourd'hui sur ces termes ?
   - À quoi ressemblent leurs pages ?
   - Pouvez-vous réellement rivaliser ?

---

## Principes fondamentaux

### 1. Valeur unique par page
- Chaque page doit apporter une valeur spécifique à cette page
- Pas seulement des variables permutées dans un template
- Maximiser le contenu unique — plus c'est différencié, mieux c'est

### 2. Les données propriétaires gagnent
Hiérarchie de la défensibilité des données :
1. Propriétaires (vous les avez créées)
2. Issues du produit (de vos utilisateurs)
3. Générées par les utilisateurs (votre communauté)
4. Licenciées (accès exclusif)
5. Publiques (tout le monde peut les utiliser — les plus faibles)

### 3. Structure d'URL propre
**Utilisez des sous-dossiers, pas des sous-domaines** — les sous-dossiers consolident l'autorité du domaine alors que les sous-domaines la divisent :
- Bon : `yoursite.com/templates/resume/`
- Mauvais : `templates.yoursite.com/resume/`

### 4. Correspondance authentique à l'intention de recherche
Les pages doivent réellement répondre à ce que les gens recherchent.

### 5. Qualité plutôt que quantité
Mieux vaut 100 excellentes pages que 10 000 pages minces.

### 6. Éviter les pénalités Google
- Pas de doorway pages
- Pas de keyword stuffing
- Pas de contenu dupliqué
- Utilité réelle pour les utilisateurs

---

## Les 12 playbooks (vue d'ensemble)

| Playbook | Pattern | Exemple |
|----------|---------|---------|
| Templates | "[Type] template" | "resume template" |
| Curation | "best [category]" | "best website builders" |
| Conversions | "[X] to [Y]" | "$10 USD to GBP" |
| Comparisons | "[X] vs [Y]" | "webflow vs wordpress" |
| Examples | "[type] examples" | "landing page examples" |
| Locations | "[service] in [location]" | "dentists in austin" |
| Personas | "[product] for [audience]" | "crm for real estate" |
| Integrations | "[product A] [product B] integration" | "slack asana integration" |
| Glossary | "what is [term]" | "what is pSEO" |
| Translations | Contenu en plusieurs langues | Contenu localisé |
| Directory | "[category] tools" | "ai copywriting tools" |
| Profiles | "[entity name]" | "stripe ceo" |

**Pour l'implémentation détaillée des playbooks** : voir [references/playbooks.md](references/playbooks.md)

---

## Choisir son playbook

| Si vous avez... | Envisagez... |
|----------------|-------------|
| Données propriétaires | Directories, Profiles |
| Produit avec intégrations | Integrations |
| Produit design/créatif | Templates, Examples |
| Audience multi-segments | Personas |
| Présence locale | Locations |
| Produit outil ou utilitaire | Conversions |
| Contenu/expertise | Glossary, Curation |
| Paysage concurrentiel | Comparisons |

Vous pouvez combiner plusieurs playbooks (ex. "Best coworking spaces in San Diego").

---

## Cadre d'implémentation

### 1. Recherche de patterns de mots-clés

**Identifier le pattern :**
- Quelle est la structure qui se répète ?
- Quelles sont les variables ?
- Combien de combinaisons uniques existent ?

**Valider la demande :**
- Volume de recherche agrégé
- Distribution du volume (head vs long tail)
- Tendance directionnelle

### 2. Exigences en matière de données

**Identifier les sources de données :**
- Quelles données alimentent chaque page ?
- Sont-elles first-party, scrapées, licenciées, publiques ?
- Comment sont-elles mises à jour ?

### 3. Conception du template

**Structure de page :**
- En-tête avec le mot-clé cible
- Intro unique (pas seulement des variables permutées)
- Sections pilotées par les données
- Pages liées / liens internes
- CTA adaptés à l'intention

**Garantir l'unicité :**
- Chaque page a besoin d'une valeur unique
- Contenu conditionnel basé sur les données
- Insights/analyses originales par page

### 4. Architecture de liens internes

**Modèle hub and spoke :**
- Hub : page de catégorie principale
- Spokes : pages programmatiques individuelles
- Liens croisés entre spokes liés

**Éviter les pages orphelines :**
- Chaque page accessible depuis le site principal
- Sitemap XML pour toutes les pages
- Fil d'Ariane avec données structurées

### 5. Stratégie d'indexation

- Prioriser les patterns à fort volume
- Mettre en noindex les variations très minces
- Gérer le crawl budget avec discernement
- Sitemaps séparés par type de page

---

## Contrôles qualité

### Checklist avant lancement

**Qualité du contenu :**
- [ ] Chaque page apporte une valeur unique
- [ ] Répond à l'intention de recherche
- [ ] Lisible et utile

**SEO technique :**
- [ ] Titres et meta descriptions uniques
- [ ] Structure de titres correcte
- [ ] Schema markup implémenté
- [ ] Vitesse de page acceptable

**Liens internes :**
- [ ] Connectée à l'architecture du site
- [ ] Pages liées reliées entre elles
- [ ] Pas de pages orphelines

**Indexation :**
- [ ] Présente dans le sitemap XML
- [ ] Crawlable
- [ ] Pas de noindex conflictuel

### Suivi post-lancement

Suivez : taux d'indexation, positions, trafic, engagement, conversion

Surveillez : avertissements de thin content, chutes de classement, actions manuelles, erreurs de crawl

---

## Erreurs courantes

- **Thin content** : se contenter de remplacer les noms de villes dans un contenu identique
- **Cannibalisation de mots-clés** : plusieurs pages ciblant le même mot-clé
- **Sur-génération** : créer des pages sans demande de recherche
- **Mauvaise qualité de données** : informations obsolètes ou incorrectes
- **Ignorer l'UX** : pages créées pour Google, pas pour les utilisateurs

---

## Format de sortie

### Document de stratégie
- Analyse d'opportunité
- Plan d'implémentation
- Lignes directrices de contenu

### Template de page
- Structure d'URL
- Templates de titre/meta
- Plan du contenu
- Schema markup

---

## Questions spécifiques à la tâche

1. Quels patterns de mots-clés ciblez-vous ?
2. Quelles données avez-vous (ou pouvez-vous acquérir) ?
3. Combien de pages prévoyez-vous ?
4. À quoi ressemble l'autorité de votre site ?
5. Qui se positionne actuellement sur ces termes ?
6. Quelle est votre stack technique ?

---

## Skills liés

- **seo-audit** : pour auditer les pages programmatiques après lancement
- **schema-markup** : pour ajouter des données structurées
- **site-architecture** : pour la hiérarchie de pages, la structure d'URL et les liens internes
- **competitor-alternatives** : pour les frameworks de pages de comparaison
