---
name: ckm:brand
description: Voix de marque, identité visuelle, frameworks de messages, gestion des assets, cohérence de marque. À activer pour le contenu de marque, le ton de voix, les supports marketing, la conformité de marque, les guides de style.
argument-hint: "[update|review|create] [args]"
metadata:
  author: claudekit
  version: "1.0.0"
---

# Marque

Identité de marque, voix, messages, gestion des assets et frameworks de cohérence.

## Quand l'utiliser

- Définition de la voix de marque et orientation du ton du contenu
- Standards d'identité visuelle et développement de guide de style
- Création de framework de messages
- Revue et audit de cohérence de marque
- Organisation, nommage et validation des assets
- Gestion de palette de couleurs et spécifications typographiques

## Démarrage rapide

**Injecter le contexte de marque dans les prompts :**
```bash
node scripts/inject-brand-context.cjs
node scripts/inject-brand-context.cjs --json
```

**Valider un asset :**
```bash
node scripts/validate-asset.cjs <chemin-asset>
```

**Extraire/comparer des couleurs :**
```bash
node scripts/extract-colors.cjs --palette
node scripts/extract-colors.cjs <chemin-image>
```

## Workflow de synchronisation de marque

```bash
# 1. Éditer docs/brand-guidelines.md (ou utiliser /brand update)
# 2. Synchroniser vers les tokens de design
node scripts/sync-brand-to-tokens.cjs
# 3. Vérifier
node scripts/inject-brand-context.cjs --json | head -20
```

**Fichiers synchronisés :**
- `docs/brand-guidelines.md` → Source de vérité
- `assets/design-tokens.json` → Définitions des tokens
- `assets/design-tokens.css` → Variables CSS

## Sous-commandes

| Sous-commande | Description | Référence |
|---------------|-------------|-----------|
| `update` | Mettre à jour l'identité de marque et synchroniser tous les design systems | `references/update.md` |

## Références

| Sujet | Fichier |
|-------|---------|
| Framework de voix | `references/voice-framework.md` |
| Identité visuelle | `references/visual-identity.md` |
| Messages | `references/messaging-framework.md` |
| Cohérence | `references/consistency-checklist.md` |
| Gabarit de guidelines | `references/brand-guideline-template.md` |
| Organisation des assets | `references/asset-organization.md` |
| Gestion des couleurs | `references/color-palette-management.md` |
| Typographie | `references/typography-specifications.md` |
| Usage du logo | `references/logo-usage-rules.md` |
| Checklist de validation | `references/approval-checklist.md` |

## Scripts

| Script | Rôle |
|--------|------|
| `scripts/inject-brand-context.cjs` | Extrait le contexte de marque pour injection dans les prompts |
| `scripts/sync-brand-to-tokens.cjs` | Synchronise brand-guidelines.md → design-tokens.json/css |
| `scripts/validate-asset.cjs` | Valide le nommage, la taille et le format des assets |
| `scripts/extract-colors.cjs` | Extrait et compare les couleurs vs la palette |

## Gabarits

| Gabarit | Rôle |
|---------|------|
| `templates/brand-guidelines-starter.md` | Gabarit de démarrage complet pour nouvelles marques |

## Routage

1. Analyser la sous-commande depuis `$ARGUMENTS` (premier mot)
2. Charger le `references/{sous-commande}.md` correspondant
3. Exécuter avec les arguments restants
