---
name: aso-audit
description: "Quand l'utilisateur souhaite auditer ou optimiser un listing App Store ou Google Play. À utiliser également quand l'utilisateur mentionne 'audit ASO', 'app store optimization', 'optimiser mon listing d'app', 'améliorer la visibilité de mon app', 'classement app store', 'auditer mon listing', 'pourquoi les gens ne téléchargent pas mon app', 'améliorer la conversion de mon app', 'optimisation de mots-clés pour app' ou 'comparer mon app aux concurrents'. À utiliser quand l'utilisateur partage une URL App Store ou Google Play et veut l'améliorer."
metadata:
  version: 1.0.0
---

# ASO Audit

Analyse les listings App Store et Google Play par rapport aux bonnes pratiques ASO. Récupère les données de listing en live, score la metadata, les visuels et les ratings, puis produit un plan d'action priorisé.

## Quand l'utiliser

- L'utilisateur partage une URL App Store ou Google Play
- L'utilisateur demande d'auditer ou d'optimiser un listing d'app
- L'utilisateur veut comparer son app à des concurrents
- L'utilisateur pose des questions sur le ranking app store, la visibilité ou la conversion de téléchargement

## Avant d'auditer

**Vérifie d'abord le contexte marketing produit :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les setups plus anciens), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations non encore couvertes ou spécifiques à cette tâche.

## Phase 1 — Identifier le store et récupérer

### Détecter le type de store depuis l'URL

```
Apple:  apps.apple.com/{country}/app/{name}/id{digits}
Google: play.google.com/store/apps/details?id={package}
```

Si l'utilisateur donne un nom d'app au lieu d'une URL, cherche sur le web :
`site:apps.apple.com "{app name}"` ou `site:play.google.com "{app name}"`

### Récupérer le listing

Utilise WebFetch pour récupérer la page du listing. Extrais chaque champ disponible :

**Champs Apple App Store :**

- App name (title) — limite 30 chars
- Subtitle — limite 30 chars
- Description (long) — non indexée pour la recherche, mais importante pour la conversion
- Promotional text — 170 chars, modifiable sans nouvelle release
- Catégorie (primaire + secondaire)
- Screenshots (nombre, ordre, texte de caption)
- Preview video (présence, durée)
- Rating (moyenne + nombre)
- Reviews récentes (celles visibles)
- Prix / in-app purchases
- Nom du développeur
- Date de dernière mise à jour
- Notes d'historique de version
- Age rating
- Taille
- Langues / localisations listées
- In-app events (s'il y en a de visibles)

**Champs Google Play :**

- App name (title) — limite 30 chars
- Short description — limite 80 chars
- Full description — limite 4 000 chars, EST indexée pour la recherche
- Catégorie + tags
- Feature graphic (présence)
- Screenshots (nombre, ordre)
- Preview video (présence)
- Rating (moyenne + nombre)
- Reviews récentes (celles visibles)
- Prix / in-app purchases
- Nom du développeur
- Date de dernière mise à jour
- Texte "What's new"
- Plage de téléchargements
- Content rating
- Section Data safety
- Langues listées

Si WebFetch retourne des données incomplètes (les stores rendent côté client), note les manques et travaille avec ce qui est disponible. Demande à l'utilisateur de coller les champs manquants si c'est critique.

### Évaluation des assets visuels

WebFetch ne peut pas extraire les images de screenshots ni le texte des captions. **Prends une capture de la page du listing** pour obtenir des données visuelles :

1. Naviguer vers l'URL du listing et capturer un screenshot pleine page
2. Évaluer le screenshot pour : qualité de l'icône, nombre de screenshots, texte des captions, qualité du messaging, présence d'une preview video, feature graphic (Google Play)
3. Si les outils navigateur sont indisponibles, demande à l'utilisateur de partager un screenshot de la page du listing

**Promotional text (Apple) :** Ce champ de 170 chars apparaît au-dessus de la description mais est souvent indissociable de celle-ci dans le HTML scrapé. Si tu ne peux pas confirmer sa présence, note-le et recommande à l'utilisateur de vérifier dans App Store Connect.

---

## Phase 1.5 — Évaluer la maturité de la marque

Avant de scorer, classifie l'app dans l'un des trois tiers. Cela détermine comment interpréter les écarts par rapport à l'ASO "textbook" — un choix de marque délibéré par un nom connu n'est pas la même chose qu'une occasion manquée par une app inconnue.

### Définitions des tiers

| Tier            | Signaux                                                                                                                              | Exemples                                    |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- |
| **Dominant**    | Nom connu, 1M+ ratings, top-10 dans sa catégorie, reconnaissance de marque quasi-universelle. Les utilisateurs cherchent par nom de marque, pas par mots-clés génériques. | Instagram, Uber, Spotify, WhatsApp, Netflix |
| **Established** | Bien connue dans sa catégorie, 100K+ ratings, fort volume d'installs organiques, marque reconnue mais pas universellement connue.    | Strava, Notion, Duolingo, Cash App, Calm    |
| **Challenger**  | En construction de notoriété, <100K ratings, a besoin de découverte via les mots-clés et les tactiques ASO. La plupart des apps tombent ici. | Ton app, la plupart des apps indie/startup  |

### Comment le tier affecte le scoring

**Les apps Dominant** bénéficient d'un scoring ajusté sur ces dimensions :

- **Title :** Les titres brand-only ou brand-first sont valides (score 8+ si la marque EST le mot-clé). Ces apps n'ont pas besoin de découverte par mots-clés génériques.
- **Description :** Scorer uniquement sur la qualité de conversion, pas sur la présence de mots-clés. Si l'app est un nom connu, une description de marque bien rédigée bat une description bourrée de mots-clés.
- **Visual Assets :** La photographie lifestyle/de marque au lieu de démos UI est une stratégie de conversion légitime. L'absence de vidéo est acceptable si le produit est difficile à démontrer en 30s ou si la notoriété de marque est quasi-universelle.
- **What's New :** Des release notes génériques à cadence hebdomadaire+ sont acceptables (score 8+). À l'échelle, les changelogs détaillés ont un ROI minimal et un risque de backlash.
- **In-app events :** L'absence d'events pour les utility apps avec des bases d'installs massives (Uber, WhatsApp) n'est pas une pénalité. Ces apps n'ont pas besoin d'aide à la découverte.
- **Localisation :** Scorer par rapport au marché réel, pas au compte absolu. Une fintech US-only avec 2 langues (anglais + espagnol) est correctement localisée.

**Les apps Established** bénéficient d'un ajustement partiel :

- Les titres brand-first sont OK mais devraient quand même inclure 1-2 mots-clés
- Les choix stratégiques de description bénéficient du doute
- Les autres dimensions sont scorées normalement

**Les apps Challenger** sont scorées strictement par rapport aux bonnes pratiques ASO textbook — chaque caractère, screenshot et mot-clé compte.

**Principe clé :** Avant de retirer des points, demande-toi : "Est-ce une erreur ou un choix délibéré d'une équipe qui a des données que je n'ai pas ?" Si l'app a 1M+ ratings et une équipe ASO dédiée, suppose que ses choix sont éclairés par la donnée sauf erreur évidente.

---

## Phase 2 — Scorer chaque dimension

Score chaque dimension de 0 à 10 selon les critères de `references/scoring-criteria.md`. Applique les ajustements de tier de maturité de marque de la Phase 1.5.

Fichiers de référence pour les specs de plateforme et les benchmarks :

- `references/apple-specs.md` — Limites de caractères officielles Apple, specs screenshot/video, règles CPP/PPO, triggers de rejet
- `references/google-play-specs.md` — Limites officielles Google Play, specs screenshot, seuils Android Vitals, policies
- `references/benchmarks.md` — Données de conversion, impact des ratings, lift video, comportement screenshot, benchmarks CPP/event

### Dimensions et pondérations

| #   | Dimension            | Pondération | Ce que ça couvre                                                            |
| --- | -------------------- | ----------- | --------------------------------------------------------------------------- |
| 1   | Title & Subtitle     | 20 %        | Utilisation des caractères, présence de mots-clés, clarté, équilibre marque + mot-clé |
| 2   | Description          | 15 %        | 3 premières lignes, densité de mots-clés (Google), CTA, structure, promotional text |
| 3   | Visual Assets        | 25 %        | Nombre/qualité/messaging des screenshots, vidéo, icône, feature graphic     |
| 4   | Ratings & Reviews    | 20 %        | Rating moyen, volume, récence, réponses du développeur                      |
| 5   | Metadata & Freshness | 10 %        | Choix de catégorie, récence de mise à jour, nombre de localisations, data safety |
| 6   | Conversion Signals   | 10 %        | Positionnement prix, transparence IAP, social proof, plage de téléchargements |

**Score final** = somme pondérée, sur 100.

### Interprétation du score

| Score  | Grade | Signification                                            |
| ------ | ----- | -------------------------------------------------------- |
| 85-100 | A     | Bien optimisé ; focus sur l'A/B testing et l'itération   |
| 70-84  | B     | Bonne fondation ; opportunités claires d'amélioration    |
| 50-69  | C     | Écarts significatifs ; les correctifs priorisés auront un fort impact |
| 30-49  | D     | Optimisation majeure nécessaire sur plusieurs dimensions |
| 0-29   | F     | Le listing nécessite une refonte complète                |

---

## Phase 3 — Comparaison concurrentielle (optionnelle)

Si l'utilisateur fournit des URLs de concurrents ou demande une comparaison :

1. Récupère 2-3 top concurrents dans la même catégorie
2. Applique le même scoring sur chacun
3. Construis un tableau comparatif soulignant où l'app de l'utilisateur est plus faible/plus forte
4. Identifie les gaps de mots-clés — termes pour lesquels les concurrents se classent mais que l'app de l'utilisateur ne cible pas

Si aucun concurrent n'est spécifié, suggère à l'utilisateur d'en fournir 2-3 ou propose de chercher les top apps de sa catégorie.

---

## Phase 4 — Générer le rapport

Utilise le template dans `references/report-template.md` pour structurer la sortie.

Le rapport doit inclure :

1. **Score card** — tableau avec les 6 dimensions, scores et grade
2. **Top 3 quick wins** — changements qui prennent <1 heure et ont le plus d'impact
3. **Findings détaillés** — décomposition par dimension avec problèmes et fixes spécifiques
4. **Suggestions de mots-clés** — basées sur l'analyse de title/description et les gaps concurrents
5. **Recommandations d'assets visuels** — améliorations spécifiques screenshot/vidéo
6. **Plan d'action priorisé** — liste ordonnée des changements par impact vs effort

### Règles du rapport

- Chaque recommandation doit être **spécifique et actionnable** ("Changer le subtitle de X à Y" et non "Améliorer le subtitle")
- Inclure les compteurs de caractères pour toutes les recommandations textuelles
- Signaler les différences spécifiques à la plateforme (Apple vs Google) quand pertinent
- Noter ce qui ne PEUT PAS être évalué sans outils payants (search volume, rankings exacts)
- Quand tu suggères des changements de mots-clés, explique POURQUOI chaque mot-clé compte

---

## Règles spécifiques par plateforme

### Apple App Store — Faits clés

- Title (30 chars) + Subtitle (30 chars) + Keyword field (100 **bytes**, caché) = texte indexé
- Le keyword field est en bytes, pas en chars — arabe/CJK utilisent 2-3 bytes par char
- La description longue N'EST PAS indexée pour la recherche — optimiser pour la conversion uniquement
- Le promotional text (170 chars) N'AFFECTE PAS la recherche (confirmé par Apple)
- Ne jamais répéter de mots à travers title/subtitle/keyword field (Apple indexe chaque mot une fois)
- Keyword field : virgules, sans espaces ("photo,editor,filter" et non "photo, editor, filter")
- Screenshots : jusqu'à 10 par device. Les 3 premiers visibles en recherche — 90 % ne scrollent pas au-delà du 3e
- Captions de screenshots indexées depuis juin 2025 (extraction IA)
- In-app events : max 10 publiés à la fois, max 31 jours chacun. Indexés et apparaissent en recherche
- Custom Product Pages (jusqu'à 70) en organic search depuis juillet 2025. +5,9 % de lift moyen de conversion
- App preview video : jusqu'à 3, 15-30s chacune. Autoplay muet — +20-40 % de lift de conversion
- SKStoreReviewController : max 3 prompts par 365 jours
- Apple a une curation éditoriale humaine — la qualité et le design comptent plus
- Voir `references/apple-specs.md` pour les specs complètes, dimensions et triggers de rejet

### Google Play — Faits clés

- Title (30 chars) + Short description (80 chars) + Full description (4 000 chars) = texte indexé
- La full description EST indexée — viser 2-3 % de densité de mots-clés naturellement
- Pas de keyword field caché — tous les mots-clés doivent être dans le texte visible
- NLP/compréhension sémantique de Google — le keyword stuffing est détecté et pénalisé
- Interdit dans le title : emojis, ALL CAPS, "best"/"#1"/"free", CTAs (appliqué depuis 2021)
- Screenshots : min 2, **max 8** par device (pas 10 comme Apple)
- Feature graphic (1024x500, exact) requis pour les featured placements
- La vidéo ne fait PAS d'autoplay — seuls ~6 % des utilisateurs tapent sur play (ROI faible vs iOS)
- Android Vitals affecte directement le ranking : crash >1,09 % ou ANR >0,47 % = visibilité réduite
- Promotional Content : soumettre 14 jours en avance pour featuring. Les apps voient 2x plus d'acquisitions explore
- Custom Store Listings : jusqu'à 50 (peuvent cibler utilisateurs churnés, pays spécifiques, campagnes ad)
- Store Listing Experiments : tester jusqu'à 3 variants, faire tourner 7+ jours, 1 expérimentation à la fois
- Voir `references/google-play-specs.md` pour les specs complètes et les détails de policy

### Ce qu'Apple indexe vs ce que Google indexe

| Champ                 | Indexé par Apple ?  | Indexé par Google ?    |
| --------------------- | ------------------- | ---------------------- |
| Title                 | Oui                 | Oui (signal le plus fort) |
| Subtitle / Short desc | Oui                 | Oui                    |
| Keyword field         | Oui (caché)         | N'existe pas           |
| Long description      | Non                 | Oui (fortement)        |
| Captions screenshots  | Oui (depuis 2025)   | Non                    |
| In-app events         | Oui                 | N/A (LiveOps à la place) |
| Nom du développeur    | Non                 | Partiel                |
| Noms IAP              | Oui                 | Oui                    |

---

## Checklist des problèmes courants

Signale ceux-ci si trouvés. Les éléments marqués _(tier-dépendant)_ doivent être évalués par rapport au tier de maturité de marque de l'app — ils peuvent être des choix délibérés pour les apps Dominant.

**Toujours signaler (tous tiers) :**

- [ ] Rating en dessous de 4,0
- [ ] Dernière mise à jour > 3 mois
- [ ] La description Google Play n'a pas de stratégie de mots-clés (sous 1 % de densité)
- [ ] Google Play manque la feature graphic
- [ ] Le keyword field Apple a probablement des mots répétés (inféré depuis title+subtitle)
- [ ] Mismatch de catégorie — l'app ferait face à moins de concurrence dans une autre catégorie
- [ ] Moins de 5 screenshots

**Signaler uniquement pour Challenger/Established** _(pas des erreurs pour les apps Dominant) :_

- [ ] Le title gaspille des caractères sur le nom de marque uniquement (pas de mots-clés) _(Dominant : la marque EST le mot-clé)_
- [ ] Le subtitle/short description duplique les mots-clés du title
- [ ] Les 3 premières lignes de la description sont génériques _(Dominant : peut être un choix de voix de marque)_
- [ ] Pas de preview video _(Dominant : peut être rationnel si le produit est difficile à démontrer)_
- [ ] Les screenshots sont juste des dumps d'UI sans messaging/captions _(Dominant : les shots lifestyle/de marque peuvent mieux convertir)_
- [ ] Seulement 1-2 localisations _(scorer par rapport au marché réel, pas au compte absolu)_
- [ ] Pas d'in-app events ni de promotional content _(les utility apps Dominant peuvent ne pas avoir besoin d'aide à la découverte)_

**Signaler pour tous les tiers mais noter le contexte :**

- [ ] Pas de réponses du développeur aux reviews négatives _(noter le volume — répondre à 10M+ reviews est un autre défi qu'à 1K)_
- [ ] Texte "What's New" générique _(acceptable à cadence de release hebdomadaire+ pour Established/Dominant)_

---

## Questions spécifiques à la tâche

1. Quelle est l'URL App Store ou Google Play ?
2. S'agit-il de ton app ou d'un concurrent ?
3. Dans quelle catégorie l'app concourt-elle ?
4. As-tu des URLs de concurrents pour comparer ?
5. Es-tu focalisé sur la visibilité en recherche, le taux de conversion, ou les deux ?
6. As-tu accès aux données App Store Connect ou Google Play Console ?

---

## Skills associés

- **page-cro** : pour optimiser la conversion des landing pages web qui drivent les installs d'app
- **ad-creative** : pour créer des créas publicitaires App Store et Google Play
- **analytics-tracking** : pour mettre en place l'attribution d'install et le tracking d'in-app events
- **customer-research** : pour comprendre les besoins et le langage des utilisateurs et informer la copy du listing
