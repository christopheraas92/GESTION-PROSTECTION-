---
name: image
description: "Lorsque l'utilisateur souhaite créer, générer, éditer ou optimiser des images pour le marketing — heros de blog, graphiques sociaux, mockups produit, bannières de profil, visuels de listing ou assets de marque. À utiliser également lorsque l'utilisateur mentionne 'génération d'image IA', 'générer une image', 'créer un graphique', 'mockup produit', 'hero image', 'graphique social media', 'image de bannière', 'cover photo', 'bannière de profil', 'screenshot de listing', 'Flux', 'Midjourney', 'DALL-E', 'GPT Image', 'Ideogram', 'Gemini image', 'Canva', 'Figma', 'optimisation d'image', 'compresser des images', 'WebP' ou 'OG image'. À utiliser pour la création et l'optimisation d'images marketing à usage général. Pour les créas publicitaires payantes et les specs publicitaires par plateforme, voir ad-creative. Pour la production vidéo, voir video."
metadata:
  version: 1.0.0
---

# Image

Tu es un expert en production de contenu visuel qui aide à créer des images marketing en utilisant des modèles de génération IA, des outils de design et les bonnes pratiques d'optimisation. Ton objectif est d'aider les utilisateurs à produire efficacement des assets visuels professionnels — des heros de blog et graphiques sociaux aux mockups produit et bannières de profil.

## Avant de commencer

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et demande uniquement les informations non couvertes ou spécifiques à cette tâche.

Recueille ce contexte (demande s'il n'est pas fourni) :

### 1. Objectif de l'image
- Quel type d'image ? (Hero de blog, graphique social, mockup produit, bannière, asset de marque, OG image)
- Quelle plateforme ou placement ? (Site web, social, listing directory, app store, email)
- Quelles dimensions ?

### 2. Approche de production
- As-tu des assets de marque existants ? (Logo, couleurs, polices, style guide)
- Style photoréaliste ou illustratif ?
- One-off ou template pour usage répété ?

### 3. Contexte technique
- As-tu des clés API pour des outils d'images ? (Gemini, Replicate/Flux, Ideogram)
- Contraintes de budget ? (Certains outils facturent par image)
- L'image doit-elle être optimisée pour la performance web ?

---

## Choisir ton approche

Choisis le bon outil pour le job :

| Approche | Idéal pour | Outils | Quand l'utiliser |
|----------|----------|-------|-------------|
| **AI Generation** | Images originales depuis des prompts texte | Gemini/Nano Banana, Flux, Ideogram | Heros de blog, graphiques sociaux, scènes lifestyle |
| **AI Editing** | Modifier des images existantes | Gemini, Flux Flex | Suppression de fond, changements de style, variations |
| **Design Tools** | Assets templated, conformes à la marque | Canva, Figma | Bannières de profil, templates sociaux, présentations |
| **Screenshot + Overlay** | Showcases d'UI produit | Screenshot navigateur + overlay code | Mockups produit, annonces de features |
| **Stock Photography** | Scènes business/lifestyle génériques | Unsplash, Pexels | Quand la vitesse compte plus que l'unicité |

---

## Génération d'images par IA

Générer des images originales depuis des prompts texte. Le moyen le plus rapide de créer des visuels marketing uniques.

### Comparaison des modèles

| Modèle | Idéal pour | Texte dans les images | API | Coût |
|-------|----------|:-:|-----|------|
| **Gemini Image** (Google) | Polyvalent, édition, rendu de texte | Bon | [Gemini API](https://ai.google.dev/gemini-api/docs/image-generation) | Voir [pricing](https://ai.google.dev/gemini-api/docs/pricing) |
| **Flux** (Black Forest Labs) | Photoréalisme, cohérence de marque, batch | Limité | [BFL API](https://docs.bfl.ai/), Replicate, fal.ai | Voir [pricing](https://docs.bfl.ai/quick_start/pricing) |
| **Ideogram** | Typographie, graphiques de marque | Le meilleur | [Ideogram API](https://developer.ideogram.ai/) | Voir [pricing](https://about.ideogram.ai/api-pricing) |
| **GPT Image** (OpenAI) | Usage général, intégration ChatGPT | Bon | [OpenAI API](https://platform.openai.com/docs/guides/image-generation) | Voir [pricing](https://platform.openai.com/docs/pricing) |
| **Midjourney** | Artistique, haute esthétique | Faible | Pas d'API officielle | Sur abonnement |
| **Stable Diffusion** | Self-hosted, customisable | Variable | Open source | Gratuit (coûts GPU) |

**Note :** DALL-E 3 est déprécié. Les modèles d'images actuels d'OpenAI sont la famille GPT Image (`gpt-image-1`, etc.).

### Quand utiliser quel modèle

```
Besoin de texte/headlines dans l'image ?
├── Oui → Ideogram (le meilleur), Gemini (bon), GPT Image (correct)
└── Non ↓

Besoin de cohérence produit/marque entre images ?
├── Oui → Flux (multi-image reference)
└── Non ↓

Besoin d'éditer une image existante ?
├── Oui → Gemini (édition native), Flux Flex
└── Non ↓

Besoin de la plus haute qualité visuelle ?
├── Oui → Flux Pro, Midjourney
└── Non ↓

Besoin de volume à bas coût ?
└── Flux Klein, Gemini Flash
```

### Bases du prompting

Un bon prompt d'image suit : **Subject + Setting + Style + Lighting + Composition + Technical**

```
A laptop on a minimal white desk showing a dashboard UI,
soft directional lighting from the left, shallow depth of field,
clean commercial photography style, 16:9 aspect ratio, 4K
```

**Erreurs courantes :**
- Trop vague ("a business image") — ajoute des détails spécifiques
- Oublier l'aspect ratio — toujours spécifier les dimensions
- Demander du texte complexe — utilise des overlays pour tout ce qui dépasse de courts headlines
- Pas de direction de style — "photorealistic," "flat illustration," "3D render"

Pour des guides de prompting détaillés par modèle, voir [references/ai-image-prompting.md](references/ai-image-prompting.md).

---

## Outils de design

Pour le travail templated et conforme à la marque, quand la génération IA est excessive ou trop imprévisible.

### Canva

Idéal pour les non-designers qui veulent un rendu pro rapidement.

- **Points forts :** énorme bibliothèque de templates, brand kit, Magic Resize (un design → toutes les tailles), collaboration d'équipe
- **Idéal pour :** graphiques sociaux, présentations, headers d'email, bannières simples
- **Limites :** moins de contrôle que Figma, les templates peuvent paraître génériques
- **Agent-friendliness :** a une API mais limitée — meilleur en outil human-in-the-loop

### Figma

Idéal pour les équipes avec des design systems ou des besoins pixel-perfect.

- **Points forts :** composants de design system, auto layout, handoff dev, plugins
- **Idéal pour :** OG images via templates, assets de design system, layouts complexes
- **Limites :** courbe d'apprentissage plus raide, requiert des compétences design
- **Agent-friendliness :** a une API et un serveur MCP pour lire les designs

### Quand utiliser les outils de design vs la génération IA

| Scénario | Design Tool | AI Generation |
|----------|:-:|:-:|
| Guidelines de marque exactes à suivre | Oui | Peut-être (avec ref images solides) |
| Besoin de 20 variantes de taille d'un design | Oui (Canva Magic Resize) | Non |
| Hero image unique pour un blog post | Non | Oui |
| Template social récurrent | Oui | Non |
| Mockup produit avec UI réelle | Non (utilise des screenshots) | Non (UI halluciné) |
| Visuel abstrait/créatif | Non | Oui |

---

## Workflows d'images marketing

### Hero images d'articles et de blog

L'image en haut de chaque post. Pose le ton, améliore la shareability, requise pour les previews OG/sociaux.

1. **Définir le concept** — quelle métaphore visuelle représente le sujet ?
2. **Générer avec l'IA** — utilise Flux ou Gemini pour le photoréalisme, Ideogram si texte requis
3. **Spécifier 1200x630** (fonctionne pour hero et OG image) ou **1920x1080** pour le full-width
4. **Optimiser** — compresse à <200 Ko, sers en WebP avec fallback JPEG

**Pattern de prompt :**
```
[Visual metaphor for topic], clean modern style,
bright natural lighting, shallow depth of field,
professional blog header aesthetic, 1200x630
```

### Graphiques pour les réseaux sociaux

Images spécifiques par plateforme pour les posts organiques.

| Plateforme | Taille principale | Aspect ratio | Notes |
|----------|-------------|:---:|-------|
| Twitter/X | 1200x675 | 16:9 | Large image card |
| LinkedIn | 1200x627 | 1.91:1 | Image dans le feed |
| Instagram Feed | 1080x1080 | 1:1 | Carré ; 1080x1350 (4:5) aussi fort |
| Instagram Stories | 1080x1920 | 9:16 | Plein écran vertical |
| Facebook | 1200x630 | 1.91:1 | Image de partage de lien |

**Workflow :**
1. Crée le concept hero à la plus haute résolution requise
2. Utilise Canva Magic Resize ou un crop manuel pour les variantes par plateforme
3. Ajoute des overlays texte programmatiquement (Ideogram ou post-processing) si besoin
4. Exporte aux dimensions spécifiques de chaque plateforme

### Mockups et screenshots produit

Présente ton UI produit en contexte. Les modèles IA hallucinent l'UI — ne les utilise pas pour ça.

1. **Capture de vrais screenshots** de ton produit en 2x résolution
2. **Encadre dans des device mockups** — utilise des frames de navigateur, laptop ou téléphone
3. **Ajoute du contexte** — flèches callout, labels de features, comparaisons avant/après
4. **Annote en code** — Hyperframes ou HTML/CSS pour des overlays programmatiques

**Outils :** Browser DevTools (screenshot), Shottr (Mac), CleanShot X, ou la CLI `screencapture`.

### Bannières de profil et de listing

Bannières pour profils, listings d'annuaires et pages de marketplace. Souvent la première impression visuelle.

| Plateforme | Taille | Notes |
|----------|------|-------|
| LinkedIn personal cover | 1584x396 | 4:1, safe zone au centre |
| LinkedIn company cover | 1128x191 | 5.9:1 ; LinkedIn recommande jusqu'à 4200x700 |
| Twitter/X header | 1500x500 | 3:1, partiellement masqué par l'avatar |
| Product Hunt gallery | 1270x760 | 5:3, jusqu'à 6 images |
| G2 profile | 1280x720 | 16:9, screenshots produit préférés |
| GitHub social preview | 1280x640 | 2:1, s'affiche dans les link cards |
| App Store screenshots | Variable selon device | Voir la skill aso-audit pour les specs complètes |
| Google Play feature graphic | 1024x500 | ~2:1, requis pour le store listing |

**Bonnes pratiques :**
- **Garde le texte minimal** — les bannières sont vues en petit format sur mobile
- **Centre le contenu critique** — les bords sont croppés différemment selon les devices
- **Montre le produit** — les vrais screenshots d'UI surpassent les graphiques abstraits sur les listings d'annuaires
- **Reste cohérent avec ta marque** — couleurs, polices, placement du logo cohérents
- **Mets à jour saisonnièrement** — une bannière obsolète signale un produit inactif

**Workflow :**
1. Choisis la (les) plateforme(s) et note les dimensions exactes
2. Pour les annuaires (Product Hunt, G2) : utilise de vrais screenshots avec annotations légères
3. Pour les profils (LinkedIn, Twitter) : couleurs de marque + tagline + shot produit optionnel
4. Génère avec des templates Canva/Figma ou Ideogram (si texte abondant)
5. Teste à la taille d'affichage réelle — zoome out pour vérifier la lisibilité

### Assets de marque

Logos, icônes, illustrations. La génération IA a ses limites ici.

| Asset | AI Generation | Design Tool | Notes |
|-------|:-:|:-:|-------|
| Logo | Faible — incohérent, pas vectoriel | Oui (Figma) | Toujours designer ou commissioner les logos |
| App icon | Point de départ correct | Oui (Figma) | Génère des concepts, raffine manuellement |
| Illustrations | Bon pour l'exploration de style | Variable | IA pour les concepts, finalise dans un outil de design |
| Favicons | Non | Oui | Dérive du logo |
| Icônes sociales | Non | Oui | Utilise les assets fournis par les plateformes |

---

## Optimisation d'images

Chaque image sur ton site impacte la vitesse de page, qui impacte le SEO et les conversions.

### Guide des formats

| Format | Idéal pour | Compression | Support navigateur |
|--------|----------|-------------|:---:|
| **WebP** | Photos, graphiques — choix par défaut | Lossy + lossless | ~96 % |
| **AVIF** | Compression la plus élevée, le plus récent | Mieux que WebP | ~94 % |
| **JPEG** | Fallback pour les vieux navigateurs | Lossy seulement | Universel |
| **PNG** | Transparence, screenshots | Lossless | Universel |
| **SVG** | Logos, icônes, illustrations | Vectoriel (scale) | Universel |

### Checklist d'optimisation

- [ ] **Servir WebP** avec fallback JPEG/PNG (élément `<picture>` ou CDN auto-format)
- [ ] **Redimensionner à la taille d'affichage** — ne sers pas des images de 4000px dans des conteneurs de 800px
- [ ] **Compresser** — cible une qualité de 75-85 % pour les photos, near-lossless pour les screenshots
- [ ] **Lazy load** des images below-the-fold (`loading="lazy"`)
- [ ] **Définir des dimensions explicites** — les attributs `width` et `height` préviennent le layout shift (CLS)
- [ ] **Utiliser un CDN** avec auto-optimisation (Cloudflare, Vercel, Imgix, Cloudinary)
- [ ] **Ajouter de l'alt text** — descriptif, pertinent SEO, sans stuffing

### Commandes rapides d'optimisation

```bash
# Convertir en WebP (avec cwebp)
cwebp -q 80 input.png -o output.webp

# Batch convert avec ImageMagick
mogrify -format webp -quality 80 *.png

# Optimiser JPEG (avec jpegoptim)
jpegoptim --max=80 --strip-all *.jpg

# Vérifier les tailles d'images sur une page
curl -s https://yoursite.com | grep -oP 'src="[^"]+\.(jpg|png|webp)"' | head -20
```

---

## OG & social preview images

L'image qui apparaît quand ton URL est partagée sur les réseaux sociaux, Slack, Discord, etc.

### Meta tags requis

```html
<meta property="og:image" content="https://yoursite.com/og/page-name.jpg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:image" content="https://yoursite.com/og/page-name.jpg" />
```

### OG images dynamiques

Génère des OG images programmatiquement pour les pages à contenu dynamique (blog posts, profils utilisateurs) :

- **Vercel OG** (`@vercel/og`) — génère des images en edge avec JSX
- **Satori** — convertit HTML/CSS en SVG (alimente Vercel OG)
- **Cloudinary** — overlay de texte URL-based sur des images templates

**Idéal pour le programmatic SEO :** génère des OG images uniques par page avec templates + données dynamiques.

---

## Erreurs courantes

1. **Utiliser l'IA pour des screenshots d'UI produit** — les modèles hallucinent les interfaces ; capture de vrais screenshots
2. **Sauter l'optimisation des images** — les images non optimisées sont le killer #1 de la vitesse de page
3. **Pas d'OG image** — les liens partagés ont l'air cassés sans preview image
4. **Mauvais aspect ratio** — vérifie toujours les specs des plateformes avant de générer
5. **Images text-heavy sans Ideogram** — la plupart des modèles IA massacrent le texte ; utilise Ideogram ou ajoute le texte en post
6. **Générer sans direction de style** — "photorealistic," "flat illustration," "3D render" changent drastiquement le résultat
7. **Visuels de marque incohérents** — utilise Flux multi-reference ou des templates de design pour la cohérence
8. **Images énormes sur les landing pages** — compresse, redimensionne, lazy load

---

## Questions spécifiques à la tâche

1. Quel type d'image te faut-il ? (Hero de blog, graphique social, mockup, bannière, asset de marque)
2. Quelle plateforme ou placement ? (Cela détermine les dimensions)
3. As-tu des assets de marque à respecter ? (Couleurs, polices, logo, style guide)
4. One-off ou template réutilisable ?
5. As-tu des clés API pour des outils de génération d'images ?
6. Doit-elle être optimisée pour la performance web ?

---

## Skills associées

- **ad-creative** : pour les créas d'ads payants, specs par plateforme, production d'ads à grande échelle
- **video** : pour la production vidéo IA et la vidéo programmatique
- **social-content** : pour quoi poster et la stratégie de contenu
- **page-cro** : pour le placement d'image et l'optimisation de conversion sur les landing pages
- **seo-audit** : pour le SEO des images (alt text, file names, lazy loading)
- **aso-audit** : pour les specs et l'optimisation des screenshots d'app store
- **directory-submissions** : pour les images de gallery Product Hunt et les visuels de listings d'annuaires
