---
type: log
date_maj: 2026-06-22
---

# Journal du wiki Agence RG

Journal append-only des actions sur le wiki. Format :

```
## [YYYY-MM-DD] <type> | <résumé>
```

Types : `ingest`, `query`, `lint`, `note`, `refactor`.

Pour les 5 dernières entrées :

```bash
grep "^## \[" wiki/log.md | tail -5
```

---

## [2026-06-22] note | Initialisation du wiki

Création de l'arborescence et du schéma `CLAUDE.md` selon le pattern LLM Wiki,
transposé pour le contexte de l'Agence RG.

- Couche `raw/` : 5 sous-dossiers (prospects, clients, veille, interne, assets)
- Couche `wiki/` : 12 sous-dossiers (comptes, personnes, opportunites, projets,
  biens, secteurs, concurrents, methodes, outils, tendances, sources, templates)
- Templates créés pour les 11 types d'entités
- Config Obsidian dans `.obsidian/` (graph par type, templates, plugins
  recommandés Dataview + Templater)

## [2026-06-22] refactor | Adaptation au contexte immobilier

Le pattern initial parlait de "marketing/conseil". Découverte via le site
agence-rg.fr que l'Agence RG est une **agence immobilière indépendante**.
Adaptation du schéma :

- Ajout du type d'entité `bien` (immobilier) avec template dédié
- Vocabulaire mis à jour dans CLAUDE.md : compte = vendeur/acheteur/bailleur/
  locataire ; opportunite = mandat/recherche ; projet = transaction/gestion ;
  secteur = commune/quartier ; concurrent = agence
- Tableau "Périmètre" du CLAUDE.md aligné sur le métier

## [2026-06-22] ingest | Site agence-rg.fr → 13 pages créées

Première vraie ingestion. Source : [[site-agence-rg]].

Pages créées :

- **Fiche racine** : [[agence-rg]]
- **Personne** : [[christophe-raas]]
- **Secteurs** (7) : [[garches]], [[vaucresson]], [[saint-cloud]],
  [[la-celle-saint-cloud]], [[marnes-la-coquette]], [[ville-d-avray]],
  [[issy-les-moulineaux]]
- **Méthodes** (3) : [[estimation-bien]], [[selection-locataire]],
  [[gestion-locative]]
- **Outils** (1) : [[opinion-system]]
- **Source** (1) : [[site-agence-rg]]

Index et log mis à jour.

Pistes ouvertes (notées dans la fiche [[site-agence-rg]]) : identifier les 6
autres conseillers, documenter le dashboard "Scan/Sync", ingérer les articles du
blog, détailler la Garantie Intégrale, mapper la concurrence par secteur.

## [2026-06-22] ingest | Sites Agence Plus (CRM principal) → 2 pages créées + 3 mises à jour

Source : [[agence-plus-site]] (URLs `agence-plus.fr` marketing +
`agence-plus.net` portail login). Précision donnée par l'utilisateur : **c'est
le CRM principal de l'agence**.

Pages créées :

- [[agence-plus]] (outil) — CRM principal
- [[agence-plus-site]] (source) — trace formelle de l'ingestion
- `raw/interne/agence-plus-snapshot-2026-06-22.md` — snapshot brut consolidé

Pages mises à jour :

- [[agence-rg]] — Agence Plus mentionné comme CRM principal dans la section
  outils ; piste "Scan/Sync" reliée à Agence Plus ; ajout d'une piste workflow
  d'export
- [[estimation-bien]] — précision : le fichier acquéreurs interne consulté à
  l'étape 3 est hébergé dans Agence Plus
- [[index]] — entrée Outils + entrée Sources, total pages 13 → 15

Note de sécurité : l'utilisateur a proposé de partager les codes d'accès au
CRM. Refus motivé (creds en clair dans le chat = anti-pattern). Workflow
alternatif documenté dans [[agence-plus]] : exports CSV/PDF déposés
manuellement dans `raw/interne/exports-crm/`.
