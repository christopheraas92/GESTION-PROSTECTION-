---
name: ckm:design-system
description: Architecture de tokens, spécifications de composants et génération de diapositives. Tokens à trois couches (primitive→sémantique→composant), variables CSS, échelles d'espacement/typographie, specs de composants, création stratégique de diapositives. À utiliser pour les tokens de design, le design systématique, les présentations conformes à la marque.
argument-hint: "[composant ou token]"
license: MIT
metadata:
  author: claudekit
  version: "1.0.0"
---

# Design System

Architecture de tokens, spécifications de composants, design systématique, génération de diapositives.

## Quand l'utiliser

- Création de tokens de design
- Définitions d'états de composants
- Systèmes de variables CSS
- Échelles d'espacement/typographie
- Passage du design au code
- Configuration de thème Tailwind
- **Génération de diapositives/présentations**

## Architecture des tokens

Charger : `references/token-architecture.md`

### Structure à trois couches

```
Primitif (valeurs brutes)
       ↓
Sémantique (alias par usage)
       ↓
Composant (spécifique au composant)
```

**Exemple :**
```css
/* Primitif */
--color-blue-600: #2563EB;

/* Sémantique */
--color-primary: var(--color-blue-600);

/* Composant */
--button-bg: var(--color-primary);
```

## Démarrage rapide

**Générer les tokens :**
```bash
node scripts/generate-tokens.cjs --config tokens.json -o tokens.css
```

**Valider l'usage :**
```bash
node scripts/validate-tokens.cjs --dir src/
```

## Références

| Sujet | Fichier |
|-------|---------|
| Architecture des tokens | `references/token-architecture.md` |
| Tokens primitifs | `references/primitive-tokens.md` |
| Tokens sémantiques | `references/semantic-tokens.md` |
| Tokens de composants | `references/component-tokens.md` |
| Specs de composants | `references/component-specs.md` |
| États et variantes | `references/states-and-variants.md` |
| Intégration Tailwind | `references/tailwind-integration.md` |

## Patron de spec de composant

| Propriété | Par défaut | Survol | Actif | Désactivé |
|-----------|------------|--------|-------|-----------|
| Fond | primary | primary-dark | primary-darker | muted |
| Texte | white | white | white | muted-fg |
| Bordure | aucune | aucune | aucune | muted-border |
| Ombre | sm | md | aucune | aucune |

## Scripts

| Script | Rôle |
|--------|------|
| `generate-tokens.cjs` | Génère le CSS depuis une config JSON de tokens |
| `validate-tokens.cjs` | Cherche les valeurs codées en dur dans le code |
| `search-slides.py` | Recherche BM25 + recommandations contextuelles |
| `slide-token-validator.py` | Valide le HTML de diapositive pour la conformité aux tokens |
| `fetch-background.py` | Récupère des images depuis Pexels/Unsplash |

## Gabarits

| Gabarit | Rôle |
|---------|------|
| `design-tokens-starter.json` | JSON de démarrage avec structure à trois couches |

## Intégration

**Avec brand :** Extraire les primitifs depuis les couleurs/typographies de marque
**Avec ui-styling :** Tokens de composants → config Tailwind

**Dépendances de skills :** brand, ui-styling
**Agents principaux :** ui-ux-designer, frontend-developer

## Système de diapositives

Présentations conformes à la marque utilisant tokens de design + Chart.js + système de décision contextuel.

### Sources de vérité

| Fichier | Rôle |
|---------|------|
| `docs/brand-guidelines.md` | Identité de marque, voix, couleurs |
| `assets/design-tokens.json` | Définitions de tokens (primitive→sémantique→composant) |
| `assets/design-tokens.css` | Variables CSS (à importer dans les diapositives) |
| `assets/css/slide-animations.css` | Bibliothèque d'animations CSS |

### Recherche de diapositive (BM25)

```bash
# Recherche basique (détection automatique du domaine)
python scripts/search-slides.py "investor pitch"

# Recherche par domaine spécifique
python scripts/search-slides.py "problem agitation" -d copy
python scripts/search-slides.py "revenue growth" -d chart

# Recherche contextuelle (système Premium)
python scripts/search-slides.py "problem slide" --context --position 2 --total 9
python scripts/search-slides.py "cta" --context --position 9 --prev-emotion frustration
```

### CSV du système de décision

| Fichier | Rôle |
|---------|------|
| `data/slide-strategies.csv` | 15 structures de deck + arcs émotionnels + temps forts sparkline |
| `data/slide-layouts.csv` | 25 mises en page + variantes de composants + animations |
| `data/slide-layout-logic.csv` | Objectif → Mise en page + flag break_pattern |
| `data/slide-typography.csv` | Type de contenu → Échelle typographique |
| `data/slide-color-logic.csv` | Émotion → Traitement colorimétrique |
| `data/slide-backgrounds.csv` | Type de diapo → Catégorie d'image (Pexels/Unsplash) |
| `data/slide-copy.csv` | 25 formules de rédaction (PAS, AIDA, FAB) |
| `data/slide-charts.csv` | 25 types de graphiques avec config Chart.js |

### Flux de décision contextuelle

```
1. Analyser l'objectif/contexte
        ↓
2. Chercher dans slide-strategies.csv → Obtenir stratégie + temps forts émotionnels
        ↓
3. Pour chaque diapositive :
   a. Requête slide-layout-logic.csv → mise en page + break_pattern
   b. Requête slide-typography.csv → échelle typographique
   c. Requête slide-color-logic.csv → traitement colorimétrique
   d. Requête slide-backgrounds.csv → image si nécessaire
   e. Appliquer la classe d'animation depuis slide-animations.css
        ↓
4. Générer le HTML avec les tokens de design
        ↓
5. Valider avec slide-token-validator.py
```

### Rupture de motif (Sparkline Duarte)

Les decks premium alternent entre les émotions pour maintenir l'engagement :
```
"Ce qui est" (frustration) ↔ "Ce qui pourrait être" (espoir)
```

Le système calcule les ruptures de motif aux positions 1/3 et 2/3.

### Exigences des diapositives

**Toutes les diapositives DOIVENT :**
1. Importer `assets/design-tokens.css` — source unique de vérité
2. Utiliser les variables CSS : `var(--color-primary)`, `var(--slide-bg)`, etc.
3. Utiliser Chart.js pour les graphiques (PAS de barres CSS uniquement)
4. Inclure la navigation (flèches clavier, clic, barre de progression)
5. Centrer le contenu
6. Se concentrer sur la persuasion/conversion

### Intégration Chart.js

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>

<canvas id="revenueChart"></canvas>
<script>
new Chart(document.getElementById('revenueChart'), {
    type: 'line',
    data: {
        labels: ['Sep', 'Oct', 'Nov', 'Déc'],
        datasets: [{
            data: [5, 12, 28, 45],
            borderColor: '#FF6B6B',  // Corail de marque
            backgroundColor: 'rgba(255, 107, 107, 0.1)',
            fill: true,
            tension: 0.4
        }]
    }
});
</script>
```

### Conformité aux tokens

```css
/* CORRECT — utilise un token */
background: var(--slide-bg);
color: var(--color-primary);
font-family: var(--typography-font-heading);

/* INCORRECT — codé en dur */
background: #0D0D0D;
color: #FF6B6B;
font-family: 'Space Grotesk';
```

### Implémentation de référence

Exemple fonctionnel avec toutes les fonctionnalités :
```
assets/designs/slides/claudekit-pitch-251223.html
```

### Commande

```bash
/slides:create "Pitch investisseur 10 diapos pour ClaudeKit Marketing"
```

## Bonnes pratiques

1. Ne jamais utiliser de hex brut dans les composants — toujours référencer un token
2. La couche sémantique permet le changement de thème (clair/sombre)
3. Les tokens de composants permettent la personnalisation par composant
4. Utiliser le format HSL pour le contrôle d'opacité
5. Documenter le rôle de chaque token
6. **Les diapositives doivent importer design-tokens.css et utiliser var() exclusivement**
