---
type: meta
date_maj: 2026-06-22
---

# Templates du wiki Agence RG

Modèles markdown pour chaque type d'entité. Utilisables avec le plugin **Templates**
d'Obsidian (assigner le dossier `wiki/templates/` comme dossier de templates).

Chaque template définit :
- Le frontmatter YAML attendu (clés et valeurs autorisées)
- La structure des sections du corps
- Les wikilinks habituels

Quand Claude crée une nouvelle page, il suit le template du type concerné.

## Liste des templates

| Type | Fichier | Champ `statut` autorisé |
|---|---|---|
| Compte (prospect/client) | [[compte]] | `prospect` · `client_actif` · `client_inactif` |
| Personne (contact) | [[personne]] | `actif` · `inactif` |
| Opportunité (deal) | [[opportunite]] | `qualification` · `proposition` · `negociation` · `gagne` · `perdu` |
| Projet | [[projet]] | `en_cours` · `termine` · `suspendu` |
| Secteur | [[secteur]] | — |
| Concurrent | [[concurrent]] | `direct` · `indirect` · `historique` |
| Méthode | [[methode]] | `active` · `archive` |
| Outil | [[outil]] | `utilise` · `evalue` · `abandonne` |
| Tendance | [[tendance]] | `emergente` · `etablie` · `declin` |
| Source | [[source]] | — |
