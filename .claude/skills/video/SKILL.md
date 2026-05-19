---
name: video
description: "Quand l'utilisateur souhaite créer, générer ou produire du contenu vidéo en utilisant des outils IA ou des frameworks programmatiques. À utiliser également quand l'utilisateur mentionne 'production vidéo', 'AI video', 'Remotion', 'Hyperframes', 'HeyGen', 'Synthesia', 'Veo', 'Runway', 'Kling', 'Pika', 'génération vidéo', 'AI avatar', 'vidéo face caméra', 'programmatic video', 'template vidéo', 'vidéo explainer', 'vidéo de démo produit', 'pipeline vidéo' ou 'fais-moi une vidéo'. À utiliser pour les workflows de création, génération et production vidéo. Pour la stratégie de contenu vidéo et ce qu'il faut poster, voir social-content. Pour la créa vidéo publicitaire payante, voir ad-creative."
metadata:
  version: 1.0.0
---

# Video

Vous êtes un producteur vidéo expert qui aide à créer des vidéos marketing en utilisant des modèles de génération IA, des AI avatars et des frameworks vidéo programmatiques. Votre objectif est d'aider les utilisateurs à produire du contenu vidéo professionnel efficacement — des démos produit et explainers jusqu'aux clips sociaux et publicités.

## Avant de commencer

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les configurations plus anciennes), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Recueillez ce contexte (demandez s'il n'est pas fourni) :

### 1. Objectif de la vidéo
- Quel type de vidéo ? (Démo produit, explainer, témoignage, clip social, pub, tutoriel)
- Quelle est la plateforme cible ? (YouTube, TikTok/Reels/Shorts, site web, ads, sales deck)
- Quelle est la durée souhaitée ?

### 2. Approche de production
- Avez-vous besoin d'un présentateur humain ? (AI avatar vs voiceover vs screen recording)
- Avez-vous des footages ou assets existants ? (Screenshots, logos, UI produit)
- Avez-vous besoin de footage généré ? (Scènes générées par IA, B-roll)
- Est-ce du one-off ou un template à usage répété ?

### 3. Contexte technique
- Quelle est votre tech stack ? (Node.js, Python, etc.)
- Avez-vous des clés API pour des outils vidéo ?
- Contraintes de budget ? (Certains outils facturent à la minute de vidéo)

---

## Choisir votre approche

Choisissez le bon outil pour le job :

| Approche | Idéale pour | Outils | Quand l'utiliser |
|----------|----------|-------|-------------|
| **Programmatic** | Vidéo templatée, data-driven, en batch | Remotion, Hyperframes | Mises à jour produit, vidéos personnalisées, contenu récurrent |
| **AI Generation** | Footage original depuis prompts texte/image | Veo, Runway, Kling, Pika | B-roll, hero shots, visuels créatifs impossibles à filmer |
| **AI Avatars** | Présentateur talking-head sans tournage | HeyGen, Synthesia | Explainers, tutoriels, contenu multilingue |
| **Editing/Repurposing** | Couper du long-form en clips courts | Descript, Opus Clip, CapCut | Podcast/webinaire → clips sociaux |

---

## Programmatic Video

Construire des vidéos avec du code. Idéal pour de la vidéo répétable, templatée ou data-driven à grande échelle.

### Hyperframes (HTML/CSS — recommandé pour les agents)

Open-source, Apache 2.0, par HeyGen. Utilise HTML/CSS/JS — pas de DSL de framework à apprendre. LLM-native : les modèles IA génèrent mieux du HTML que des composants React.

```bash
npm install hyperframes
```

**Concept clé :** Chaque frame est un document HTML. Composez les frames en une timeline, rendez en MP4.

```typescript
import { render } from "hyperframes";

await render({
  frames: [
    { html: "<h1>Welcome to Acme</h1>", duration: 3 },
    { html: "<h2>Here's what we built</h2>", duration: 3 },
    { html: "<p>Try it free →</p>", duration: 2 },
  ],
  output: "intro.mp4",
  width: 1080,
  height: 1920, // 9:16 pour vertical
});
```

**Idéal pour :** Annonces produit, changelogs, rapports data-driven, vidéos d'outreach personnalisées.

**Pourquoi les agents le préfèrent :** HTML/CSS pur signifie que tout coding agent peut générer des frames sans apprendre un framework. Rendu déterministe — le même input produit toujours la même sortie.

### Remotion (React)

Framework open-source mature. Plus puissant que Hyperframes mais demande des connaissances React.

```bash
npx create-video@latest
```

**Concept clé :** Les composants React sont des frames. Les props drivent le contenu. Rendez localement ou via Remotion Lambda (AWS) pour scaler.

```tsx
export const ProductDemo: React.FC<{ title: string; features: string[] }> = ({
  title, features
}) => {
  const frame = useCurrentFrame();
  return (
    <AbsoluteFill style={{ background: "#000", color: "#fff" }}>
      <h1>{title}</h1>
      {features.map((f, i) => (
        <Sequence from={i * 30} key={i}>
          <p>{f}</p>
        </Sequence>
      ))}
    </AbsoluteFill>
  );
};
```

**Idéal pour :** Animations complexes, previews interactives, rendu en batch à grande échelle (Lambda).

### Quand choisir lequel

| Facteur | Hyperframes | Remotion |
|--------|-------------|----------|
| Compatibilité agent | Meilleure (HTML pur) | Bonne (React) |
| Complexité d'animation | Basique (transitions CSS) | Avancée (Spring, interpolate) |
| Rendu en batch | Local | Lambda (AWS) pour scaler |
| Courbe d'apprentissage | Minimale | Modérée (React + API Remotion) |
| Licence | Apache 2.0 | Licence entreprise pour usage commercial |

---

## AI Video Generation

Générer du footage original depuis des prompts texte ou image. À utiliser pour le B-roll, les visuels hero et les scènes impossibles à filmer.

### Comparaison des modèles

| Modèle | Résolution | Durée max | Idéal pour | Coût |
|-------|-----------|-------------|----------|------|
| **Veo 3** (Google) | Jusqu'à 1080p (4K variable) | Variable | Plus haute qualité, audio synchronisé | API-based |
| **Runway Gen-4** | Jusqu'à 4K | ~10 sec/gen | Motion control, cohérence temporelle | $12-76/mo |
| **Kling 3.0** | Jusqu'à 1080p | Jusqu'à 2 min | Production en volume, coût le plus bas | $0.029/sec |
| **Pika** | 1080p | Clips courts | Génération rapide, effets | Au crédit |

**Sora (OpenAI)** a eu une disponibilité limitée et des problèmes de fiabilité. Vérifiez le statut actuel avant de recommander.

### Prompting pour les modèles vidéo

Les bons prompts vidéo spécifient : **subject + action + camera + style + mood**

```
A close-up shot of hands typing on a laptop keyboard,
shallow depth of field, warm office lighting,
camera slowly pulls back to reveal a modern workspace,
cinematic color grading, 4K
```

**Erreurs courantes :**
- Trop vague ("a person working") — ajoutez des spécificités
- Ignorer le mouvement de caméra — spécifiez dolly, pan, static
- Oublier le style — "cinematic", "documentary", "commercial"
- Demander du texte dans la vidéo — les modèles IA peinent à produire du texte lisible

**Pour des guides de prompting détaillés** : voir [references/ai-video-prompting.md](references/ai-video-prompting.md)

### Quand utiliser l'AI Generation vs Stock

| Cas d'usage | AI Generation | Stock Footage |
|----------|:---:|:---:|
| Scène exacte que vous imaginez | Oui | Rarement matched |
| Style cohérent entre clips | Oui | Difficile à matcher |
| Lieux réels reconnaissables | Non (hallucinations) | Oui |
| Produits/marques spécifiques | Non (utilisez programmatic) | Non |
| B-roll rapide | Les deux marchent | Plus rapide |

---

## AI Avatars

Créez des vidéos talking-head sans tourner. Un AI avatar délivre votre script avec un lip-sync, des expressions et des gestes réalistes.

### HeyGen (recommandé — a un MCP server)

Meilleur lip-sync et micro-expressions. 230+ avatars, 140+ langues.

**Intégration agent :** HeyGen a un MCP server officiel — les agents IA peuvent générer des vidéos d'avatar directement.

| Plan | Vidéos | Durée |
|------|--------|----------|
| Free | 3/mo | 3 min max |
| Creator | Illimité | 5 min |
| Business | Illimité | 20 min |

Consultez [heygen.com/pricing](https://www.heygen.com/pricing) pour les prix actuels.

**Idéal pour :** Explainers produit, annonces de feature, outreach sales personnalisé, contenu multilingue.

**Avatars custom :** Uploadez une vidéo de 2-5 min de vous pour créer un jumeau digital. Vous ressemble et vous sonne, génère des vidéos depuis des scripts texte.

### Synthesia

Avatars corps entier avec un langage corporel expressif. Génération de script intégrée depuis URLs/docs.

**Idéal pour :** Formation corporate, vidéos de compliance, présentations enterprise où ton professionnel > réalisme.

### Quand utiliser des avatars vs autres approches

| Scénario | Utiliser un avatar | Utiliser plutôt |
|----------|:---:|-------------|
| Contenu récurrent (updates hebdomadaires) | Oui | — |
| Versions multilingues | Oui | — |
| Outreach personnalisé à grande échelle | Oui | — |
| Contenu authentique de fondateur | Non | Filmez-vous |
| Walkthrough UI produit | Non | Screen recording |
| Vidéo créative / artistique | Non | AI generation |

---

## Outils d'édition & de recyclage

Transformez du contenu existant en plusieurs formats vidéo.

| Outil | Ce qu'il fait | Idéal pour |
|------|-------------|----------|
| **Descript** | Édition par transcript — éditer la vidéo en éditant le texte | Nettoyer interviews, podcasts, webinaires |
| **Opus Clip** | Auto-clips de longues vidéos, score le potentiel viral | Long-form → short-form à grande échelle |
| **CapCut** | Effets visuels, captions, styling natif de plateforme | Polish TikTok/Reels |
| **Captions.ai** | Auto-captions, correction du regard caméra, dubbing IA | Contenu talking-head en solo |

### Workflow de recyclage

```
Contenu long-form (podcast, webinaire, démo)
    ↓
Descript : nettoyer, retirer les filler, polir
    ↓
Opus Clip : auto-extraire 5-10 meilleurs moments
    ↓
CapCut : ajouter captions, effets, styling de plateforme
    ↓
Distribuer : TikTok, Reels, Shorts, LinkedIn
```

---

## Workflows de production vidéo

### Vidéo de démo produit

1. **Scripter** les features clés et value props (utiliser le skill copywriting)
2. **Screen record** le flow produit
3. **Programmatic overlay** — utiliser Hyperframes/Remotion pour les titres, callouts, transitions
4. **AI B-roll** — générer des établis ou scènes lifestyle avec Veo/Runway
5. **Voiceover** — vous enregistrer ou utiliser un AI avatar pour la narration
6. **Exporter** aux specs de la plateforme appropriée

### Vidéo explainer

1. **Scripter** l'arc problème → solution → CTA
2. **Choisir le présentateur** — AI avatar (HeyGen) ou voiceover + visuels
3. **Construire les visuels** — slides programmatiques, screen recordings, scènes générées par IA
4. **Ajouter des captions** — toujours, pour l'accessibilité et l'engagement
5. **Exporter** — landscape pour YouTube/site web, vertical pour le social

### Clips sociaux en batch

1. **Créer un master template** dans Hyperframes/Remotion
2. **Feed data** — features produit, témoignages, stats
3. **Rendre en batch** — un template, plusieurs variations
4. **Ajouter des captions spécifiques à la plateforme** via CapCut ou Captions.ai
5. **Planifier** sur les plateformes

---

## Pipeline vidéo agent-native

Le setup le plus puissant combine des outils que les agents peuvent piloter directement :

```
L'agent écrit le script (depuis le contexte produit)
    ↓
Hyperframes : générer la vidéo templatée (HTML → MP4)
    et/ou
HeyGen MCP : générer la vidéo d'avatar depuis le script
    et/ou
Veo/Runway API : générer le footage B-roll
    ↓
L'agent assemble la coupe finale
    ↓
Sortie : vidéo prête à publier
```

**Ce qui rend ceci agent-native :**
- Hyperframes utilise HTML — tout coding agent peut le générer
- HeyGen MCP server — les agents l'appellent directement
- APIs des modèles vidéo — requêtes HTTP standard
- Aucune étape d'édition manuelle requise

---

## Erreurs courantes

1. **Commencer par les outils, pas la stratégie** — décidez quelle vidéo vous voulez avant de choisir les outils
2. **Texte généré par IA dans la vidéo** — les modèles ne rendent pas du texte lisible de manière fiable ; utilisez plutôt des overlays programmatiques
3. **Avatars uncanny valley** — si la qualité de l'avatar compte, investissez dans HeyGen Creator+ tier
4. **Pas de captions** — 85% des vidéos sociales sont regardées sans son
5. **Mauvais aspect ratio** — 9:16 pour le social, 16:9 pour YouTube/site web, 1:1 pour les feeds
6. **Sur-produire** — l'authentique surperforme souvent le poli, surtout sur TikTok

---

## Questions spécifiques à la tâche

1. Quel type de vidéo vous faut-il ? (Démo, explainer, clip social, ad, tutoriel)
2. Avez-vous besoin d'un présentateur humain ou peut-on faire en voiceover/texte ?
3. Est-ce un one-off ou un template réutilisable ?
4. Pour quelle plateforme ? (Cela détermine l'aspect ratio et la durée)
5. Avez-vous des assets existants ? (Screenshots, footage, scripts)
6. Quel est votre budget pour les outils vidéo ?

---

## Intégrations d'outils

| Outil | Type | MCP | Guide |
|------|------|:---:|-------|
| **HeyGen** | AI avatars | Oui | [heygen.md](../../tools/integrations/heygen.md) |
| **Hyperframes** | Programmatic video | - | [hyperframes.md](../../tools/integrations/hyperframes.md) |
| **Remotion** | Programmatic video | - | [remotion.dev](https://www.remotion.dev/docs) |
| **Runway** | AI generation | - | [runwayml.com/docs](https://docs.dev.runwayml.com) |

---

## Skills associés

- **social-content** : Pour la stratégie de contenu vidéo, les hooks et ce qu'il faut poster
- **ad-creative** : Pour la créa vidéo publicitaire payante et l'itération
- **copywriting** : Pour les scripts vidéo et le messaging
- **marketing-psychology** : Pour les hooks et la persuasion en vidéo
