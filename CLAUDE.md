# CLAUDE.md — Wiki Agence RG

Ce repo est un wiki personnel maintenu par Claude pour **l'Agence RG**, une
**agence immobilière indépendante** des Hauts-de-Seine (Garches et Vaucresson),
fondée en 1989 par Christophe Raas. Voir [[wiki/agence-rg]] pour la fiche
d'identité.

Tu (Claude) en es le mainteneur principal. L'humain curate les sources, pose les
questions et lit le wiki dans Obsidian. Tu fais le reste : résumés, cross-references,
maintenance, synthèses.

Ce fichier est **le schéma** : il décrit comment le wiki est structuré, les
conventions à respecter et les workflows à suivre. Il co-évolue avec le wiki au fil
des sessions.

---

## Architecture en 3 couches

1. **`raw/`** — sources brutes immuables (emails, briefs PDF, transcripts d'appels,
   articles, podcasts, captures d'écran). Tu **lis** uniquement ; tu n'écris jamais
   dedans. C'est la source de vérité.
2. **`wiki/`** — pages markdown que tu écris et maintiens. Une couche compilée,
   interconnectée par wikilinks `[[Page]]`. Tu en es 100 % propriétaire.
3. **`CLAUDE.md`** (ce fichier) — le contrat entre toi et l'humain. À mettre à jour
   ensemble quand on découvre une convention qui marche mieux.

---

## Périmètre du wiki

Le wiki Agence RG couvre **trois domaines interconnectés** adaptés au métier
d'agence immobilière :

| Domaine | Entités principales | Sources typiques |
|---|---|---|
| **Pipeline commercial** | comptes (prospects vendeurs / acheteurs / bailleurs / locataires), personnes, opportunités (mandats, recherches) | emails entrants, transcripts d'appels prospects, demandes formulaire, signalements de bien à vendre |
| **Clients & dossiers** | comptes (clients actifs), biens immobiliers, projets (transactions, gestions locatives) | mandats signés, compromis, baux, comptes-rendus de visite, courriers locataires |
| **Marché & connaissance** | secteurs (communes/quartiers), concurrents (agences), méthodes, outils, tendances | annonces concurrents, statistiques notaires, baromètres, articles immobiliers |

Les trois domaines s'interconnectent : un bien est rattaché à un compte vendeur ET
à un secteur ; un mandat (opportunité) est issu d'un appel à un secteur ; une
gestion locative implique un bien, un bailleur, un locataire. Tu maintiens ces
liens.

**Vocabulaire local** :
- `compte` = personne morale ou physique côté marché (vendeur, acheteur, bailleur,
  locataire) ou notaire/partenaire
- `opportunite` = mandat (vente ou gestion) ou mission de recherche acquéreur
- `projet` = dossier en cours de gestion (transaction signée jusqu'à l'acte, ou
  bail jusqu'à sa résiliation)
- `bien` = bien immobilier (maison, appartement, terrain, immeuble, local)
- `secteur` = commune ou micro-secteur géographique
- `concurrent` = autre agence immobilière du périmètre

---

## Structure des dossiers

```
raw/
├── prospects/       # ce qui vient du pipeline commercial
├── clients/         # briefs, contrats, livrables clients
├── veille/          # articles, podcasts, rapports externes
├── interne/         # documents internes de l'agence
└── assets/          # images, captures, PDF référencés par les sources
```

```
wiki/
├── agence-rg.md     # fiche de l'agence elle-même (racine du wiki)
├── index.md         # catalogue maître (toutes les pages classées)
├── log.md           # journal chronologique append-only
├── comptes/         # 1 page par compte (prospect OU client)
├── personnes/       # 1 page par contact identifié
├── opportunites/    # 1 page par mandat ou recherche
├── projets/         # 1 page par dossier en cours (transaction, gestion)
├── biens/           # 1 page par bien immobilier suivi
├── secteurs/        # 1 page par commune ou micro-secteur
├── concurrents/     # 1 page par agence concurrente
├── methodes/        # frameworks et pratiques de l'agence
├── outils/          # outils utilisés ou évalués
├── tendances/       # tendances marché observées
├── sources/         # 1 page par source ingérée (résumé + liens)
└── templates/       # modèles YAML pour chaque type d'entité
```

---

## Conventions

### Nommage des fichiers

- **kebab-case** : `acme-corp.md`, `marie-dupont.md`, `refonte-site-acme.md`.
- Pour les personnes : `prenom-nom.md` (sans accents, sans espaces).
- Pour les comptes : nom court reconnaissable, sans suffixe juridique (`acme` plutôt
  que `acme-sas`).
- Pour les opportunités : `<compte>-<objet-court>.md` (ex : `acme-refonte-site.md`).

### Wikilinks

- Toujours utiliser `[[Nom de la page]]` pour référencer une autre page du wiki.
  Obsidian s'occupe de la résolution.
- Pour pointer vers une source brute : `[[raw/clients/acme/brief-2026-01.md]]`
  (chemin relatif explicite).

### Frontmatter YAML obligatoire

Toutes les pages `wiki/` portent un frontmatter. Le schéma dépend du type :

```yaml
---
type: compte | personne | opportunite | projet | bien | secteur | concurrent | methode | outil | tendance | source
statut: <selon le type — voir templates/>
date_creation: 2026-06-22
date_maj: 2026-06-22
tags: [tag1, tag2]
sources: ["[[raw/clients/acme/brief.md]]"]
---
```

Voir `wiki/templates/` pour le schéma exact de chaque type.

### Ton et style

- Français, professionnel, concis.
- Pas d'emoji.
- Pas de prose inutile : préférer listes, tableaux, sections courtes.
- Citer les sources : à la fin de chaque affirmation forte, mettre `([[source]])`.
- Quand une donnée change, ne pas perdre l'ancienne — la déplacer dans une section
  `## Historique` avec la date.

### Confidentialité

Les sources peuvent contenir des données sensibles (noms de prospects, montants de
deals, briefs confidentiels, emails clients). Avant tout commit/push :

- Vérifier qu'aucun secret n'est exposé (clés API, mots de passe).
- Ne **jamais** proposer de rendre ce repo public sans validation explicite.

---

## Workflows

### Ingest — intégrer une nouvelle source

Quand l'humain dépose un fichier dans `raw/<catégorie>/` et demande de l'ingérer :

1. **Lire** la source intégralement.
2. **Restituer** en 3-5 bullets les takeaways clés et demander confirmation/inflexion.
3. **Créer** `wiki/sources/<nom-source>.md` : résumé structuré, faits clés extraits,
   citations notables, entités/concepts mentionnés (avec wikilinks).
4. **Toucher** toutes les pages d'entités concernées :
   - Comptes (créer s'il faut, sinon mettre à jour `## Historique` + faits)
   - Personnes
   - Opportunités/projets
   - Secteurs, concurrents, méthodes, outils, tendances
5. **Signaler les contradictions** : si la nouvelle source contredit une page
   existante, le noter dans la page concernée ET dans `log.md`.
6. **Append** dans `log.md` :
   `## [YYYY-MM-DD] ingest | <titre source> → <N pages touchées>`
7. **Mettre à jour** `wiki/index.md` si de nouvelles pages ont été créées.

### Query — répondre à une question

1. **Lire** `wiki/index.md` pour repérer les pages pertinentes.
2. **Lire** ces pages, suivre les wikilinks si nécessaire.
3. **Répondre** en citant chaque affirmation forte (`[[Page]]`).
4. **Proposer** de filer la réponse comme nouvelle page si elle est dense (analyse,
   comparatif, synthèse). Les explorations doivent compounder dans le wiki, pas
   disparaître dans le chat.
5. **Append** dans `log.md` : `## [YYYY-MM-DD] query | <question courte>`.

### Lint — health-check du wiki

À demander périodiquement (toutes les 5-10 ingestions). Vérifier :

- **Contradictions** entre pages
- **Pages orphelines** : aucun inbound link → soit supprimer, soit relier
- **Concepts implicites** : termes répétés sans page dédiée → suggérer création
- **Cross-references manquantes** : page A mentionne B sans `[[B]]`
- **Pages obsolètes** : `date_maj` > 6 mois pour des entités censées être actives
- **Lacunes** : concepts importants peu sourcés → suggérer recherche
- **Pistes** : questions intéressantes à explorer, sources à chercher

Append rapport dans `log.md` : `## [YYYY-MM-DD] lint | <N issues, N suggestions>`.

---

## Indexation et journal

### `wiki/index.md`

Catalogue de toutes les pages du wiki, classées par section. Pour chaque page :
lien wikilink + une ligne de description + métadonnées utiles (statut, date_maj).
À tenir à jour à chaque ingest.

### `wiki/log.md`

Journal append-only. Format strict pour permettre `grep "^## \[" log.md`:

```
## [YYYY-MM-DD] <type> | <résumé>

<détails optionnels en bullets>
```

Types : `ingest`, `query`, `lint`, `note` (action humaine), `refactor` (réorganisation du wiki).

---

## Outils disponibles

- **Obsidian** : front-end de lecture. Wikilinks `[[]]`, graph view, Dataview pour
  requêtes YAML.
- **Skills marketing** : ce repo contient 47 skills dans `.claude/skills/` —
  `customer-research`, `competitor-profiling`, `cold-email`, `seo-audit`, etc. Tu
  peux les invoquer quand pertinent pour le contenu wiki (ex : `competitor-profiling`
  pour structurer une nouvelle page concurrent).
- **Git** : versionning gratuit. Branche par grosse refonte.

---

## Notes d'évolution

Ce schéma est un **point de départ**. Quand on découvre qu'une convention marche
mieux, on l'écrit ici. Quand un workflow se précise, on l'affine. Le wiki et son
schéma co-évoluent.

Dernière mise à jour : 2026-06-22.
