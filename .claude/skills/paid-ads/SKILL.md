---
name: paid-ads
description: "Lorsque l'utilisateur souhaite de l'aide pour des campagnes publicitaires payantes sur Google Ads, Meta (Facebook/Instagram), LinkedIn, Twitter/X, ou d'autres plateformes publicitaires. À utiliser également lorsque l'utilisateur mentionne 'PPC', 'paid media', 'ROAS', 'CPA', 'campagne publicitaire', 'retargeting', 'ciblage d'audience', 'Google Ads', 'Facebook ads', 'LinkedIn ads', 'budget publicitaire', 'coût par clic', 'budget pub', ou 'devrais-je lancer des annonces'. À utiliser pour la stratégie de campagne, le ciblage d'audience, les enchères et l'optimisation. Pour la génération et l'itération de créatifs publicitaires en masse, voir ad-creative. Pour l'optimisation des landing pages, voir page-cro."
metadata:
  version: 1.2.0
---

# Paid Ads

Vous êtes un expert en marketing à la performance avec un accès direct aux comptes des plateformes publicitaires. Votre objectif est d'aider à créer, optimiser et scaler des campagnes payantes qui génèrent une acquisition client efficace.

## Avant de commencer

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y sont pas déjà couvertes ou qui sont spécifiques à cette tâche.

Rassemblez ce contexte (demandez si non fourni) :

### 1. Objectifs de campagne
- Quel est l'objectif principal ? (Notoriété, trafic, leads, ventes, installations d'app)
- Quel est le CPA ou ROAS cible ?
- Quel est le budget mensuel/hebdomadaire ?
- Y a-t-il des contraintes ? (Charte de marque, conformité, géographie)

### 2. Produit et offre
- Que faites-vous la promotion ? (Produit, free trial, lead magnet, démo)
- Quelle est l'URL de la landing page ?
- Qu'est-ce qui rend cette offre convaincante ?

### 3. Audience
- Qui est le client idéal ?
- Quel problème votre produit résout-il pour lui ?
- Que recherchent-ils ou par quoi sont-ils intéressés ?
- Disposez-vous de données clients existantes pour les lookalikes ?

### 4. État actuel
- Avez-vous déjà lancé des annonces ? Qu'est-ce qui a fonctionné/échoué ?
- Disposez-vous de données pixel/conversion existantes ?
- Quel est votre taux de conversion actuel dans le funnel ?

---

## Guide de sélection de plateforme

| Plateforme | Idéal pour | À utiliser quand |
|----------|----------|----------|
| **Google Ads** | Trafic de recherche à forte intention | Les gens recherchent activement votre solution |
| **Meta** | Génération de demande, produits visuels | Création de demande, forts assets créatifs |
| **LinkedIn** | B2B, décideurs | Le ciblage par poste/entreprise compte, prix élevés |
| **Twitter/X** | Audiences tech, leadership d'opinion | L'audience est active sur X, contenu d'actualité |
| **TikTok** | Démographies plus jeunes, créatifs viraux | Audience 18-34 ans, capacité vidéo |

---

## Bonnes pratiques de structure de campagne

### Organisation du compte

```
Account
├── Campaign 1: [Objective] - [Audience/Product]
│   ├── Ad Set 1: [Targeting variation]
│   │   ├── Ad 1: [Creative variation A]
│   │   ├── Ad 2: [Creative variation B]
│   │   └── Ad 3: [Creative variation C]
│   └── Ad Set 2: [Targeting variation]
└── Campaign 2...
```

### Conventions de nommage

```
[Platform]_[Objective]_[Audience]_[Offer]_[Date]

Examples:
META_Conv_Lookalike-Customers_FreeTrial_2024Q1
GOOG_Search_Brand_Demo_Ongoing
LI_LeadGen_CMOs-SaaS_Whitepaper_Mar24
```

### Allocation du budget

**Phase de test (2-4 premières semaines) :**
- 70 % sur les campagnes éprouvées/sûres
- 30 % sur le test de nouvelles audiences/créatifs

**Phase de scaling :**
- Consolider le budget dans les combinaisons gagnantes
- Augmenter les budgets de 20-30 % à la fois
- Attendre 3-5 jours entre les augmentations pour l'apprentissage de l'algorithme

---

## Frameworks de copy publicitaire

### Formules clés

**Problem-Agitate-Solve (PAS) :**
> [Problème] → [Agiter la douleur] → [Introduire la solution] → [CTA]

**Before-After-Bridge (BAB) :**
> [État douloureux actuel] → [État futur souhaité] → [Votre produit comme pont]

**Social Proof Lead :**
> [Statistique impressionnante ou témoignage] → [Ce que vous faites] → [CTA]

**Pour des templates détaillés et des formules de titres** : Voir [references/ad-copy-templates.md](references/ad-copy-templates.md)

---

## Vue d'ensemble du ciblage d'audience

### Forces des plateformes

| Plateforme | Ciblage clé | Meilleurs signaux |
|----------|---------------|--------------|
| Google | Mots-clés, intention de recherche | Ce qu'ils recherchent |
| Meta | Intérêts, comportements, lookalikes | Schémas d'engagement |
| LinkedIn | Postes, entreprises, secteurs | Identité professionnelle |

### Concepts clés

- **Lookalikes** : Baser sur les meilleurs clients (par LTV), pas tous les clients
- **Retargeting** : Segmenter par étape du funnel (visiteurs vs. cart abandoners)
- **Exclusions** : Exclure les clients existants et les récents convertis — afficher des annonces à des gens qui ont déjà acheté gaspille le budget

**Pour des stratégies de ciblage détaillées par plateforme** : Voir [references/audience-targeting.md](references/audience-targeting.md)

---

## Bonnes pratiques créatives

### Annonces images
- Captures d'écran produit claires montrant l'UI
- Comparaisons avant/après
- Stats et chiffres comme point focal
- Visages humains (réels, pas du stock)
- Overlay texte gras et lisible (rester sous 20 %)

### Structure des vidéos publicitaires (15-30 sec)
1. Hook (0-3 sec) : Pattern interrupt, question ou affirmation forte
2. Problème (3-8 sec) : Pain point relatable
3. Solution (8-20 sec) : Montrer le produit/bénéfice
4. CTA (20-30 sec) : Étape suivante claire

**Conseils de production :**
- Sous-titres toujours (85 % regardent sans son)
- Vertical pour Stories/Reels, carré pour le feed
- Le rendu natif surpasse le poli
- Les 3 premières secondes déterminent s'ils regardent

### Hiérarchie de test créatif
1. Concept/angle (impact le plus important)
2. Hook/titre
3. Style visuel
4. Corps de texte
5. CTA

---

## Optimisation de campagne

### Métriques clés par objectif

| Objectif | Métriques principales |
|-----------|-----------------|
| Notoriété | CPM, Reach, Taux de vue vidéo |
| Considération | CTR, CPC, Temps sur site |
| Conversion | CPA, ROAS, Taux de conversion |

### Leviers d'optimisation

**Si le CPA est trop élevé :**
1. Vérifier la landing page (le problème est-il post-clic ?)
2. Resserrer le ciblage d'audience
3. Tester de nouveaux angles créatifs
4. Améliorer la pertinence/quality score de l'annonce
5. Ajuster la stratégie d'enchère

**Si le CTR est faible :**
- Le créatif ne résonne pas → tester de nouveaux hooks/angles
- Mauvais fit d'audience → affiner le ciblage
- Ad fatigue → rafraîchir le créatif

**Si le CPM est élevé :**
- Audience trop étroite → élargir le ciblage
- Forte concurrence → essayer d'autres placements
- Score de pertinence faible → améliorer l'adéquation créative

### Progression de la stratégie d'enchères
1. Commencer par manual ou cost caps
2. Recueillir des données de conversion (50+ conversions)
3. Passer à l'automatisé avec des cibles basées sur l'historique
4. Surveiller et ajuster les cibles en fonction des résultats

---

## Stratégies de retargeting

### Approche basée sur le funnel

| Étape du funnel | Audience | Message | Objectif |
|--------------|----------|---------|------|
| Top | Lecteurs de blog, viewers de vidéo | Éducatif, social proof | Passer à la considération |
| Middle | Visiteurs des pages tarifs/features | Études de cas, démos | Passer à la décision |
| Bottom | Cart abandoners, utilisateurs trial | Urgence, gestion des objections | Convertir |

### Fenêtres de retargeting

| Étape | Fenêtre | Frequency Cap |
|-------|--------|---------------|
| Hot (cart/trial) | 1-7 jours | Élevée OK |
| Warm (pages clés) | 7-30 jours | 3-5x/semaine |
| Cold (toute visite) | 30-90 jours | 1-2x/semaine |

### Exclusions à mettre en place
- Clients existants (sauf upsell)
- Récents convertis (fenêtre 7-14 jours)
- Visiteurs ayant rebondi (<10 sec)
- Pages non pertinentes (carrières, support)

---

## Reporting et analyse

### Revue hebdomadaire
- Cadencement budget vs. dépenses
- CPA/ROAS vs. cibles
- Top et bottom des annonces
- Répartition de la performance par audience
- Vérification de fréquence (risque de fatigue)
- Taux de conversion de la landing page

### Considérations d'attribution
- L'attribution des plateformes est gonflée
- Utiliser les paramètres UTM de manière cohérente
- Comparer les données des plateformes à GA4
- Regarder le CAC blended, pas uniquement le CPA de la plateforme

---

## Mise en place de plateforme

Avant de lancer des campagnes, assurez-vous d'un tracking et d'une configuration du compte adéquats.

**Pour des checklists complètes de setup par plateforme** : Voir [references/platform-setup-checklists.md](references/platform-setup-checklists.md)

**Pour l'installation du pixel de conversion et la configuration des événements** : Voir [references/conversion-tracking.md](references/conversion-tracking.md)

### Checklist universelle pré-lancement
- [ ] Tracking de conversion testé avec une vraie conversion
- [ ] La landing page se charge rapidement (<3 sec)
- [ ] Landing page mobile-friendly
- [ ] Paramètres UTM fonctionnels
- [ ] Budget correctement défini
- [ ] Ciblage correspondant à l'audience visée

---

## Erreurs courantes à éviter

### Stratégie
- Lancer sans tracking de conversion
- Trop de campagnes (fragmentation du budget)
- Ne pas laisser assez de temps d'apprentissage aux algorithmes
- Optimiser sur la mauvaise métrique

### Ciblage
- Audiences trop étroites ou trop larges
- Ne pas exclure les clients existants
- Audiences qui se chevauchent et se concurrencent

### Créatif
- Une seule annonce par ad set
- Pas de rafraîchissement créatif (fatigue)
- Décalage entre l'annonce et la landing page

### Budget
- Étaler trop fin sur de nombreuses campagnes
- Faire de gros changements de budget (perturbe l'apprentissage)
- Arrêter les campagnes pendant la phase d'apprentissage

---

## Questions spécifiques à la tâche

1. Sur quelle(s) plateforme(s) tournez-vous actuellement ou souhaitez-vous démarrer ?
2. Quel est votre budget publicitaire mensuel ?
3. À quoi ressemble une conversion réussie (et quelle est sa valeur) ?
4. Disposez-vous d'assets créatifs existants ou faut-il les créer ?
5. Vers quelle landing page les annonces pointeront-elles ?
6. Avez-vous mis en place le tracking pixel/conversion ?

---

## Intégrations d'outils

Pour l'implémentation, voir le [tools registry](../../tools/REGISTRY.md). Principales plateformes publicitaires :

| Plateforme | Idéal pour | MCP | Guide |
|----------|----------|:---:|-------|
| **Google Ads** | Intention de recherche, trafic à forte intention | ✓ | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | Demand gen, produits visuels, B2C | - | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | B2B, ciblage par poste | - | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | Démographies plus jeunes, vidéo | - | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

Pour la configuration du tracking, voir [references/conversion-tracking.md](references/conversion-tracking.md), [ga4.md](../../tools/integrations/ga4.md), [segment.md](../../tools/integrations/segment.md)

---

## Skills associés

- **ad-creative** : Pour générer et itérer des titres, descriptions et créatifs publicitaires à grande échelle
- **copywriting** : Pour des landing pages qui convertissent le trafic publicitaire
- **analytics-tracking** : Pour une bonne configuration du tracking de conversion
- **ab-test-setup** : Pour tester les landing pages afin d'améliorer le ROAS
- **page-cro** : Pour optimiser les taux de conversion post-clic
