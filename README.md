# Wiki Agence RG

Wiki personnel maintenu par Claude pour l'Agence RG.

Ce repo applique le pattern **LLM Wiki** : Claude lit les sources brutes que tu
déposes dans `raw/`, et écrit/maintient un wiki structuré dans `wiki/`. Tu lis le
wiki dans **Obsidian**, tu poses des questions à Claude, et le wiki s'enrichit à
chaque ingestion.

## Architecture

```
.
├── CLAUDE.md         # Le schéma : conventions et workflows. Lu par Claude à chaque session.
├── raw/              # Sources brutes immuables (tu déposes, Claude lit)
├── wiki/             # Pages markdown maintenues par Claude (tu lis)
├── .obsidian/        # Config Obsidian (graph, templates, plugins)
└── .claude/          # 47 skills marketing à disposition de Claude
```

Voir [CLAUDE.md](CLAUDE.md) pour le détail du pattern, des conventions et des
workflows (ingest, query, lint).

## Démarrer

### Avec Obsidian

1. **Ouvrir le repo comme vault Obsidian** : File > Open vault > sélectionner ce
   dossier.
2. **Activer les plugins recommandés** : Settings > Community plugins, installer
   `Dataview` et `Templater`.
3. **Configurer les templates** : Settings > Templates > "Template folder
   location" → `wiki/templates`.
4. **Naviguer** : ouvrir `wiki/index.md` ou utiliser la graph view (Ctrl+G).

### Avec Claude Code

Demander à Claude :

- **Ingérer une source** : *"J'ai déposé `raw/clients/acme/brief.pdf`, ingère-le."*
- **Poser une question** : *"Que sait-on sur Acme et leur secteur ?"*
- **Health-check** : *"Lance un lint du wiki."*

## Workflow typique

1. Tu reçois un brief, un email, un transcript d'appel, un article.
2. Tu le déposes dans le bon sous-dossier de `raw/` (utilise Obsidian Web Clipper
   pour les articles web).
3. Tu demandes à Claude de l'ingérer.
4. Claude crée/met à jour les pages d'entités touchées (comptes, personnes,
   opportunités, secteurs…), met à jour `wiki/index.md` et logge dans
   `wiki/log.md`.
5. Tu lis le résultat dans Obsidian, suis les wikilinks, regardes la graph view.

## Confidentialité

Ce repo contient potentiellement des données sensibles (briefs clients, montants
de deals, contacts prospects). **Ne pas rendre public**. Toujours vérifier avant
chaque push qu'aucune donnée confidentielle ne se retrouve dans un commit
involontaire.

## Référence

Pattern inspiré du *LLM Wiki pattern* — un guide abstrait qui décrit comment
construire un wiki incrémentalement maintenu par un LLM. Transposé pour le
contexte d'une agence française couvrant prospection, gestion de comptes clients
et veille marketing.
