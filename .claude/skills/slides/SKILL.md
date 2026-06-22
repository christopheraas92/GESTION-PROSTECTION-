---
name: ckm:slides
description: Créer des présentations HTML stratégiques avec Chart.js, tokens de design, mises en page responsives, formules de rédaction et stratégies de diapositives contextuelles.
argument-hint: "[sujet] [nombre-de-diapos]"
metadata:
  author: claudekit
  version: "1.0.0"
---

# Diapositives

Conception stratégique de présentations HTML avec visualisation de données.

<args>$ARGUMENTS</args>

## Quand l'utiliser

- Présentations marketing et pitch decks
- Diapositives orientées données avec Chart.js
- Conception stratégique de diapositives avec patterns de mise en page
- Contenu de présentation optimisé pour la rédaction

## Sous-commandes

| Sous-commande | Description | Référence |
|---------------|-------------|-----------|
| `create` | Créer des diapositives de présentation stratégique | `references/create.md` |

## Références (base de connaissances)

| Sujet | Fichier |
|-------|---------|
| Patterns de mise en page | `references/layout-patterns.md` |
| Gabarit HTML | `references/html-template.md` |
| Formules de rédaction | `references/copywriting-formulas.md` |
| Stratégies de diapositives | `references/slide-strategies.md` |

## Routage

1. Analyser la sous-commande depuis `$ARGUMENTS` (premier mot)
2. Charger le `references/{sous-commande}.md` correspondant
3. Exécuter avec les arguments restants
