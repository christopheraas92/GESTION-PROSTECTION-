---
type: source
source_type: site_web
source_path: "[[raw/interne/agence-plus-snapshot-2026-06-22.md]]"
auteur: "Agence Plus"
date_publication: ""
date_ingest: 2026-06-22
date_creation: 2026-06-22
date_maj: 2026-06-22
tags: [crm, outil-interne]
---

# Sites Agence Plus (consultation du 2026-06-22)

> Source consolidant deux pages : agence-plus.fr (marketing) et agence-plus.net
> (portail login). Ingérée après précision utilisateur : *« C'est le CRM
> principal »* de l'agence.

## Référence

- **URLs** :
  - https://agence-plus.fr (marketing)
  - https://agence-plus.net (portail utilisateur)
- **Snapshot local** : [[raw/interne/agence-plus-snapshot-2026-06-22.md]]
- **Date de consultation** : 2026-06-22

## Résumé

Agence Plus est un éditeur de CRM immobilier basé à Levallois-Perret. Propose
un logiciel transaction (Habitation et Professionnel), un module de création
de site web pour agences, des Agents IA pour qualification automatique et une
offre modulaire. Promesse : « relation client continue sans effort ».

Précision donnée par Christophe Raas : **c'est le CRM principal de
[[agence-rg]]** — donc un outil structurant du quotidien de l'agence, pas une
simple piste à évaluer.

## Faits clés extraits

- Éditeur basé au 55 rue Chaptal, 92300 Levallois-Perret.
- Téléphone : 01 40 89 39 80 / Email : contact@agence-plus.com.
- SAV lundi-vendredi 9h30-17h30.
- Cinq produits : Habitation, Professionnel, Site web, Agents IA, modules
  marketplace.
- Cible : agences indépendantes, réseaux d'agences, mandataires.
- Tarification non publique.
- Promesse : autonomie en 2 semaines.

## Citations notables

> *« La confiance fait la différence, mais trop d'opportunités se perdent sans
> suivi rigoureux. »*

> *« Une relation client continue sans effort par les agents IA. »*

## Entités mentionnées

- **Outils** : [[agence-plus]]
- **Fiche racine** : [[agence-rg]]

## Pages wiki touchées par l'ingestion

- [[agence-plus]] — création (page outil)
- [[agence-rg]] — mise à jour (mention du CRM principal)
- [[estimation-bien]] — mise à jour (le fichier acquéreurs interne passe par
  Agence Plus)
- [[index]] — mise à jour
- [[log]] — entrée ingest

## Contradictions avec le wiki existant

Aucune. Précise la piste ouverte du dashboard "Scan/Sync" mentionné sur
agence-rg.fr — il pourrait s'agir d'un module Agence Plus (à confirmer).

## Questions ouvertes / pistes à creuser

- [ ] Quels modules Agence Plus sont effectivement utilisés à l'Agence RG ?
- [ ] Quels portails d'annonces sont synchronisés depuis le CRM ?
- [ ] Le dashboard "Scan/Sync" cité sur agence-rg.fr fait-il partie d'Agence
      Plus ?
- [ ] Mettre en place un workflow d'export récurrent CRM → `raw/interne/exports-crm/`
- [ ] Existe-t-il une API ou un connecteur Agence Plus → outils tiers (Notion,
      Airtable, etc.) qui pourrait alimenter le wiki automatiquement ?
- [ ] Tarification : quel coût pour l'agence (à des fins de calcul ROI / lint
      du wiki) ?

## Sécurité

> Les identifiants Agence Plus ne doivent **jamais** être stockés dans ce repo,
> ni partagés dans le chat Claude Code. Le wiki vit avec des exports
> contrôlés.
