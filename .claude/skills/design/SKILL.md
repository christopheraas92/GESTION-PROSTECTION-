---
name: ckm:design
description: "Skill design complète : identité de marque, tokens de design, UI styling, génération de logos (55 styles, Gemini AI), programme d'identité corporate (CIP, 50 livrables, mockups CIP), présentations HTML (Chart.js), conception de bannières (22 styles, social/pubs/web/impression), conception d'icônes (15 styles, SVG, Gemini 3.1 Pro), photos sociales (HTML→capture, multi-plateforme). Actions : concevoir logo, créer CIP, générer mockups, construire diapositives, concevoir bannière, générer icône, créer photos sociales, images réseaux sociaux, identité de marque, design system. Plateformes : Facebook, Twitter, LinkedIn, YouTube, Instagram, Pinterest, TikTok, Threads, Google Ads."
argument-hint: "[type-de-design] [contexte]"
license: MIT
metadata:
  author: claudekit
  version: "2.1.0"
---

# Design

Skill design unifiée : marque, tokens, UI, logo, CIP, diapositives, bannières, photos sociales, icônes.

## Quand l'utiliser

- Identité de marque, voix, assets
- Tokens et specs de design system
- UI styling avec shadcn/ui + Tailwind
- Conception de logo et génération par IA
- Livrables du programme d'identité corporate (CIP)
- Présentations et pitch decks
- Conception de bannières pour réseaux sociaux, pubs, web, impression
- Photos sociales pour Instagram, Facebook, LinkedIn, Twitter, Pinterest, TikTok

## Routage vers les sous-skills

| Tâche | Sous-skill | Détails |
|-------|------------|---------|
| Identité de marque, voix, assets | `brand` | Skill externe |
| Tokens, specs, variables CSS | `design-system` | Skill externe |
| shadcn/ui, Tailwind, code | `ui-styling` | Skill externe |
| Création de logo, génération IA | Logo (intégré) | `references/logo-design.md` |
| Mockups CIP, livrables | CIP (intégré) | `references/cip-design.md` |
| Présentations, pitch decks | Slides (intégré) | `references/slides.md` |
| Bannières, couvertures, en-têtes | Banner (intégré) | `references/banner-sizes-and-styles.md` |
| Images/photos réseaux sociaux | Social Photos (intégré) | `references/social-photos-design.md` |
| Icônes SVG, jeux d'icônes | Icon (intégré) | `references/icon-design.md` |

## Conception de logo (intégré)

55+ styles, 30 palettes de couleurs, 25 guides d'industrie. Modèles Gemini Nano Banana.

### Logo : générer un brief de design

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "tech startup modern" --design-brief -p "BrandName"
```

### Logo : rechercher styles/couleurs/industries

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "minimalist clean" --domain style
python3 ~/.claude/skills/design/scripts/logo/search.py "tech professional" --domain color
python3 ~/.claude/skills/design/scripts/logo/search.py "healthcare medical" --domain industry
```

### Logo : générer avec l'IA

**TOUJOURS** générer les images de logo en sortie avec un fond blanc.

```bash
python3 ~/.claude/skills/design/scripts/logo/generate.py --brand "TechFlow" --style minimalist --industry tech
python3 ~/.claude/skills/design/scripts/logo/generate.py --prompt "coffee shop vintage badge" --style vintage
```

**IMPORTANT :** En cas d'échec d'un script, essayer de le corriger directement.

Après la génération, **TOUJOURS** demander à l'utilisateur s'il veut un aperçu HTML via `AskUserQuestion`. Si oui, invoquer `/ui-ux-pro-max` pour la galerie.

## Conception CIP (intégré)

50+ livrables, 20 styles, 20 industries. Gemini Nano Banana (Flash/Pro).

### CIP : générer un brief

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "tech startup" --cip-brief -b "BrandName"
```

### CIP : rechercher des domaines

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "business card letterhead" --domain deliverable
python3 ~/.claude/skills/design/scripts/cip/search.py "luxury premium elegant" --domain style
python3 ~/.claude/skills/design/scripts/cip/search.py "hospitality hotel" --domain industry
python3 ~/.claude/skills/design/scripts/cip/search.py "office reception" --domain mockup
```

### CIP : générer des mockups

```bash
# Avec logo (RECOMMANDÉ)
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /chemin/logo.png --deliverable "business card" --industry "consulting"

# Set CIP complet
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /chemin/logo.png --industry "consulting" --set

# Modèle Pro (texte 4K)
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo logo.png --deliverable "business card" --model pro

# Sans logo
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TechFlow" --deliverable "business card" --no-logo-prompt
```

Modèles : `flash` (par défaut, `gemini-2.5-flash-image`), `pro` (`gemini-3-pro-image-preview`)

### CIP : rendu de présentation HTML

```bash
python3 ~/.claude/skills/design/scripts/cip/render-html.py --brand "TopGroup" --industry "consulting" --images /chemin/cip-output
```

**Astuce :** S'il n'y a pas de logo, utiliser d'abord la section Conception de logo ci-dessus.

## Slides (intégré)

Présentations HTML stratégiques avec Chart.js, tokens de design, formules de rédaction.

Charger `references/slides-create.md` pour le workflow de création.

### Slides : base de connaissances

| Sujet | Fichier |
|-------|---------|
| Guide de création | `references/slides-create.md` |
| Patterns de mise en page | `references/slides-layout-patterns.md` |
| Gabarit HTML | `references/slides-html-template.md` |
| Rédaction | `references/slides-copywriting-formulas.md` |
| Stratégies | `references/slides-strategies.md` |

## Conception de bannières (intégré)

22 styles de direction artistique pour social, pubs, web, impression. Utilise les skills `frontend-design`, `ai-artist`, `ai-multimodal`, `chrome-devtools`.

Charger `references/banner-sizes-and-styles.md` pour la référence complète des tailles et styles.

### Bannière : workflow

1. **Recueillir les besoins** via `AskUserQuestion` — objectif, plateforme, contenu, marque, style, quantité
2. **Recherche** — Activer `ui-ux-pro-max`, parcourir Pinterest pour références
3. **Conception** — Créer une bannière HTML/CSS avec `frontend-design`, générer les visuels avec `ai-artist`/`ai-multimodal`
4. **Export** — Capturer en PNG aux dimensions exactes via `chrome-devtools`
5. **Présenter** — Montrer toutes les options côte à côte, itérer sur les retours

### Bannière : référence rapide des tailles

| Plateforme | Type | Taille (px) |
|------------|------|-------------|
| Facebook | Couverture | 820 x 312 |
| Twitter/X | En-tête | 1500 x 500 |
| LinkedIn | Personnel | 1584 x 396 |
| YouTube | Bannière de chaîne | 2560 x 1440 |
| Instagram | Story | 1080 x 1920 |
| Instagram | Post | 1080 x 1080 |
| Google Ads | Med Rectangle | 300 x 250 |
| Site web | Hero | 1920 x 600-1080 |

### Bannière : top styles artistiques

| Style | Idéal pour |
|-------|------------|
| Minimaliste | SaaS, tech |
| Typographie audacieuse | Annonces |
| Dégradé | Marques modernes |
| Basé photo | Lifestyle, e-com |
| Géométrique | Tech, fintech |
| Glassmorphisme | SaaS, apps |
| Néon/Cyberpunk | Gaming, événements |

### Bannière : règles de design

- Zones de sécurité : contenu critique dans les 70-80 % centraux
- Un seul CTA par bannière, en bas à droite, hauteur min 44 px
- Max 2 polices, corps min 16 px, titre ≥ 32 px
- Texte sous 20 % pour les publicités (Meta pénalise)
- Impression : 300 DPI, CMJN, fond perdu 3-5 mm

## Conception d'icônes (intégré)

15 styles, 12 catégories. Gemini 3.1 Pro Preview génère du SVG en sortie texte.

### Icône : générer une icône

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "settings gear" --style outlined
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "shopping cart" --style filled --color "#6366F1"
python3 ~/.claude/skills/design/scripts/icon/generate.py --name "dashboard" --category navigation --style duotone
```

### Icône : générer des variations en lot

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "cloud upload" --batch 4 --output-dir ./icons
```

### Icône : export multi-tailles

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "user profile" --sizes "16,24,32,48" --output-dir ./icons
```

### Icône : top styles

| Style | Idéal pour |
|-------|------------|
| outlined | Interfaces UI, applications web |
| filled | Apps mobiles, barres de nav |
| duotone | Marketing, landing pages |
| rounded | Apps amicales, santé |
| sharp | Tech, fintech, entreprise |
| flat | Material design, style Google |
| gradient | Marques modernes, SaaS |

**Modèle :** `gemini-3.1-pro-preview` — sortie texte uniquement (le SVG est du texte XML). Pas besoin d'API de génération d'image.

## Photos sociales (intégré)

Conception d'images sociales multi-plateformes : HTML/CSS → export par capture. Utilise les skills `ui-ux-pro-max`, `brand`, `design-system`, `chrome-devtools`.

Charger `references/social-photos-design.md` pour les tailles, gabarits, bonnes pratiques.

### Photos sociales : workflow

1. **Orchestrer** — skill `project-management` pour les tâches TODO ; sous-agents parallèles pour le travail indépendant
2. **Analyser** — Décomposer le prompt : sujet, plateformes, style, contexte de marque, éléments de contenu
3. **Idéation** — 3-5 concepts, présenter via `AskUserQuestion`
4. **Concevoir** — `/ckm:brand` → `/ckm:design-system` → invoquer aléatoirement `/ck:ui-ux-pro-max` OU `/ck:frontend-design` ; HTML par idée × taille
5. **Exporter** — `chrome-devtools` ou capture Playwright aux px exacts (deviceScaleFactor 2x)
6. **Vérifier** — Utiliser Chrome MCP ou la skill `chrome-devtools` pour inspecter visuellement les designs exportés ; corriger les problèmes de mise en page/style et ré-exporter
7. **Rapporter** — Synthèse dans `plans/reports/` avec les décisions de design
8. **Organiser** — Invoquer la skill `assets-organizing` pour trier les fichiers de sortie et rapports

### Photos sociales : tailles clés

| Plateforme | Taille (px) | Plateforme | Taille (px) |
|------------|-------------|------------|-------------|
| Post IG | 1080×1080 | Post FB | 1200×630 |
| Story IG | 1080×1920 | Post X | 1200×675 |
| Carrousel IG | 1080×1350 | LinkedIn | 1200×627 |
| Miniature YT | 1280×720 | Pinterest | 1000×1500 |

## Workflows

### Package de marque complet

1. **Logo** → `scripts/logo/generate.py` → Générer les variantes de logo
2. **CIP** → `scripts/cip/generate.py --logo ...` → Créer les mockups de livrables
3. **Présentation** → Charger `references/slides-create.md` → Bâtir le pitch deck

### Nouveau design system

1. **Brand** (skill brand) → Définir couleurs, typographie, voix
2. **Tokens** (skill design-system) → Créer les couches de tokens sémantiques
3. **Implémenter** (skill ui-styling) → Configurer Tailwind, shadcn/ui

## Références

| Sujet | Fichier |
|-------|---------|
| Routage design | `references/design-routing.md` |
| Guide de conception de logo | `references/logo-design.md` |
| Styles de logo | `references/logo-style-guide.md` |
| Couleurs de logo | `references/logo-color-psychology.md` |
| Prompts de logo | `references/logo-prompt-engineering.md` |
| Guide de conception CIP | `references/cip-design.md` |
| Livrables CIP | `references/cip-deliverable-guide.md` |
| Styles CIP | `references/cip-style-guide.md` |
| Prompts CIP | `references/cip-prompt-engineering.md` |
| Slides : création | `references/slides-create.md` |
| Slides : mises en page | `references/slides-layout-patterns.md` |
| Slides : gabarit | `references/slides-html-template.md` |
| Slides : rédaction | `references/slides-copywriting-formulas.md` |
| Slides : stratégie | `references/slides-strategies.md` |
| Bannières : tailles et styles | `references/banner-sizes-and-styles.md` |
| Photos sociales : guide | `references/social-photos-design.md` |
| Guide de conception d'icônes | `references/icon-design.md` |

## Scripts

| Script | Rôle |
|--------|------|
| `scripts/logo/search.py` | Rechercher styles, couleurs et industries de logo |
| `scripts/logo/generate.py` | Générer des logos avec Gemini AI |
| `scripts/logo/core.py` | Moteur de recherche BM25 pour les données de logo |
| `scripts/cip/search.py` | Rechercher livrables, styles et industries CIP |
| `scripts/cip/generate.py` | Générer les mockups CIP avec Gemini |
| `scripts/cip/render-html.py` | Rendre la présentation HTML à partir des mockups CIP |
| `scripts/cip/core.py` | Moteur de recherche BM25 pour les données CIP |
| `scripts/icon/generate.py` | Générer des icônes SVG avec Gemini 3.1 Pro |

## Installation

```bash
export GEMINI_API_KEY="votre-clé"  # https://aistudio.google.com/apikey
pip install google-genai pillow
```

## Intégration

**Sous-skills externes :** brand, design-system, ui-styling
**Skills associées :** frontend-design, ui-ux-pro-max, ai-multimodal, chrome-devtools
