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

Création de l'arborescence et du schéma `CLAUDE.md` selon le pattern LLM Wiki
(https://www.dwarkesh.com/p/llm-wiki, transposé).

- Couche `raw/` : 5 sous-dossiers (prospects, clients, veille, interne, assets)
- Couche `wiki/` : 11 sous-dossiers (comptes, personnes, opportunites, projets,
  secteurs, concurrents, methodes, outils, tendances, sources, templates)
- Templates créés pour les 10 types d'entités
- Config Obsidian minimale dans `.obsidian/`

Aucune source ingérée encore. Prochaine étape : déposer une première source dans
`raw/` et demander l'ingestion.
