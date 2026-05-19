---
name: referral-program
description: "Quand l'utilisateur souhaite créer, optimiser ou analyser un programme de parrainage, un programme d'affiliation ou une stratégie de bouche-à-oreille. À utiliser également quand l'utilisateur mentionne 'referral', 'affiliate', 'ambassador', 'word of mouth', 'viral loop', 'refer a friend', 'partner program', 'referral incentive', 'comment obtenir des parrainages', 'clients qui parrainent des clients' ou 'affiliate payout'. À utiliser dès que quelqu'un veut que ses clients existants ou ses partenaires lui amènent de nouveaux clients. Pour la viralité spécifique à un lancement, voir launch-strategy."
metadata:
  version: 1.1.0
---

# Programmes de parrainage et d'affiliation

Vous êtes expert en croissance virale et en marketing de parrainage. Votre objectif est d'aider à concevoir et à optimiser des programmes qui transforment les clients en moteurs de croissance.

## Avant de commencer

**Vérifier d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Recueillez ce contexte (demandez s'il n'est pas fourni) :

### 1. Type de programme
- Programme de parrainage client, programme d'affiliation, ou les deux ?
- B2B ou B2C ?
- Quelle est la LTV moyenne d'un client ?
- Quel est votre CAC actuel sur les autres canaux ?

### 2. État actuel
- Programme de parrainage/affiliation existant ?
- Taux de parrainage actuel (% qui parrainent) ?
- Quelles incitations avez-vous essayées ?

### 3. Fit produit
- Votre produit est-il partageable ?
- A-t-il des effets de réseau ?
- Les clients en parlent-ils naturellement ?

### 4. Ressources
- Quels outils/plateformes utilisez-vous ou envisagez-vous ?
- Quel budget pour les incitations de parrainage ?

---

## Parrainage vs affiliation

### Programmes de parrainage client

**Idéal pour :**
- Les clients existants qui recommandent à leur réseau
- Les produits avec un bouche-à-oreille naturel
- Les produits à plus faible ticket ou en self-serve

**Caractéristiques :**
- Le parrain est un client existant
- Récompenses uniques ou limitées
- Confiance élevée, volume plus faible

### Programmes d'affiliation

**Idéal pour :**
- Atteindre des audiences auxquelles vous n'avez pas accès
- Créateurs de contenu, influenceurs, blogueurs
- Produits à plus haut ticket justifiant des commissions

**Caractéristiques :**
- Les affiliés ne sont pas forcément clients
- Relation de commission continue
- Volume plus élevé, confiance variable

---

## Conception du programme de parrainage

### La boucle de parrainage

```
Moment déclencheur → Action de partage → Conversion du filleul → Récompense → (Boucle)
```

### Étape 1 : identifier les moments déclencheurs

**Moments à forte intention :**
- Juste après le premier moment "aha"
- Après l'atteinte d'un jalon
- Après un support exceptionnel
- Après un renouvellement ou un upgrade

### Étape 2 : concevoir le mécanisme de partage

**Classé par efficacité :**
1. Partage in-product (conversion la plus élevée)
2. Lien personnalisé
3. Invitation par email
4. Partage social
5. Code de parrainage (fonctionne hors ligne)

### Étape 3 : choisir la structure d'incitation

**Récompenses unilatérales** (parrain seulement) : plus simple, fonctionne pour les produits à forte valeur

**Récompenses bilatérales** (les deux parties) : conversion plus élevée, framing gagnant-gagnant

**Récompenses par paliers** : gamifie le processus de parrainage, augmente l'engagement

**Pour des exemples et le dimensionnement des incitations** : voir [references/program-examples.md](references/program-examples.md)

---

## Optimisation du programme

### Améliorer le taux de parrainage

**Si peu de clients parrainent :**
- Demandez à de meilleurs moments
- Simplifiez le processus de partage
- Testez différents types d'incitations
- Rendez le parrainage visible dans le produit

**Si les parrainages ne convertissent pas :**
- Améliorez l'expérience d'arrivée pour les filleuls
- Renforcez l'incitation pour les nouveaux utilisateurs
- Assurez-vous que la recommandation du parrain est visible

### A/B tests à mener

**Tests d'incitation :** montant, type, unilatéral vs bilatéral, timing

**Tests de message :** description du programme, copy du CTA, copy de la landing page

**Tests d'emplacement :** où et quand le prompt de parrainage apparaît

### Problèmes courants et solutions

| Problème | Solution |
|---------|-----|
| Faible notoriété | Ajouter des prompts in-app proéminents |
| Faible taux de partage | Simplifier à un clic |
| Faible conversion | Optimiser l'expérience du filleul |
| Fraude/abus | Ajouter vérification, limites |
| Parrains uniques | Ajouter des récompenses par paliers/gamifiées |

---

## Mesurer le succès

### Métriques clés

**Santé du programme :**
- Parrains actifs (ont parrainé quelqu'un dans les 30 derniers jours)
- Taux de conversion du parrainage
- Récompenses gagnées/versées

**Impact business :**
- % de nouveaux clients issus de parrainages
- CAC via parrainage vs autres canaux
- LTV des clients parrainés
- ROI du programme de parrainage

### Constats typiques

- Les clients parrainés ont une LTV 16-25% plus élevée
- Les clients parrainés ont un churn 18-37% plus faible
- Les clients parrainés parrainent à un rythme 2-3x plus élevé

---

## Checklist de lancement

### Avant le lancement
- [ ] Définir les objectifs et métriques de succès du programme
- [ ] Concevoir la structure d'incitation
- [ ] Construire ou configurer l'outil de parrainage
- [ ] Créer la landing page de parrainage
- [ ] Mettre en place le tracking et l'attribution
- [ ] Définir les règles de prévention de fraude
- [ ] Créer les conditions générales
- [ ] Tester le flux complet de parrainage

### Lancement
- [ ] Annoncer aux clients existants
- [ ] Ajouter des prompts de parrainage in-app
- [ ] Mettre à jour le site avec les détails du programme
- [ ] Briefer l'équipe support

### Post-lancement (premiers 30 jours)
- [ ] Examiner le funnel de conversion
- [ ] Identifier les meilleurs parrains
- [ ] Recueillir les retours
- [ ] Corriger les points de friction
- [ ] Envoyer des emails de rappel aux non-parrains

---

## Séquences email

### Lancement du programme de parrainage

```
Subject: You can now earn [reward] for sharing [Product]

We just launched our referral program!

Share [Product] with friends and earn [reward] for each signup.
They get [their reward] too.

[Unique referral link]

1. Share your link
2. Friend signs up
3. You both get [reward]
```

### Séquence de nurture parrainage

- Jour 7 : rappel sur le programme de parrainage
- Jour 30 : "Connaissez-vous quelqu'un qui en profiterait ?"
- Jour 60 : success story + prompt de parrainage
- Après un jalon : "Vous avez accompli [X] — connaissez-vous d'autres personnes qui voudraient ça ?"

---

## Programmes d'affiliation

**Pour la conception détaillée d'un programme d'affiliation, les structures de commissions, le recrutement et les outils** : voir [references/affiliate-programs.md](references/affiliate-programs.md)

---

## Questions spécifiques à la tâche

1. Quel type de programme (parrainage, affiliation ou les deux) ?
2. Quels sont votre LTV client et votre CAC actuel ?
3. Programme existant ou démarrage de zéro ?
4. Quels outils/plateformes envisagez-vous ?
5. Quel est votre budget pour les récompenses/commissions ?
6. Votre produit est-il naturellement partageable ?

---

## Intégrations d'outils

Pour l'implémentation, voir le [registry des outils](../../tools/REGISTRY.md). Outils clés pour les programmes de parrainage :

| Outil | Idéal pour | Guide |
|------|----------|-------|
| **Rewardful** | Programmes d'affiliation natifs Stripe | [rewardful.md](../../tools/integrations/rewardful.md) |
| **Tolt** | Programmes d'affiliation SaaS | [tolt.md](../../tools/integrations/tolt.md) |
| **Mention Me** | Programmes de parrainage enterprise | [mention-me.md](../../tools/integrations/mention-me.md) |
| **Dub.co** | Tracking de liens et attribution | [dub-co.md](../../tools/integrations/dub-co.md) |
| **Stripe** | Traitement des paiements (pour le suivi des commissions) | [stripe.md](../../tools/integrations/stripe.md) |
| **Introw** | Programmes partenaires de canal avec paliers, deal registration, QBR | [introw.md](../../tools/integrations/introw.md) |
| **PartnerStack** | Programmes partenaires et d'affiliation enterprise | [partnerstack.md](../../tools/integrations/partnerstack.md) |

---

## Skills liés

- **launch-strategy** : pour lancer efficacement un programme de parrainage
- **email-sequence** : pour les campagnes de nurture de parrainage
- **marketing-psychology** : pour comprendre la motivation au parrainage
- **analytics-tracking** : pour le suivi de l'attribution des parrainages
