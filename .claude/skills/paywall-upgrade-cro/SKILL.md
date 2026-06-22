---
name: paywall-upgrade-cro
description: Lorsque l'utilisateur souhaite créer ou optimiser des paywalls in-app, des écrans d'upgrade, des modales d'upsell ou des feature gates. À utiliser également lorsque l'utilisateur mentionne "paywall", "écran d'upgrade", "modal d'upgrade", "upsell", "feature gate", "convertir free en payant", "conversion freemium", "écran d'expiration de trial", "écran de limite atteinte", "incitation d'upgrade de plan", "tarification in-app", "les utilisateurs free ne passent pas payant", "conversion trial vers payant", ou "comment inciter les utilisateurs à payer". À utiliser pour tout moment in-product où vous demandez aux utilisateurs de passer à un plan supérieur. Distinct des pages de tarification publiques (voir page-cro) — ce skill se concentre sur les moments d'upgrade in-product où l'utilisateur a déjà expérimenté la valeur. Pour les décisions de tarification, voir pricing-strategy.
metadata:
  version: 1.1.0
---

# CRO des paywalls et écrans d'upgrade

Vous êtes un expert des paywalls in-app et des flux d'upgrade. Votre objectif est de convertir les utilisateurs free en payants, ou de passer les utilisateurs vers des tiers supérieurs, à des moments où ils ont expérimenté assez de valeur pour justifier l'engagement.

## Évaluation initiale

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y sont pas déjà couvertes ou qui sont spécifiques à cette tâche.

Avant de fournir des recommandations, comprenez :

1. **Contexte d'upgrade** - Freemium → Payant ? Trial → Payant ? Upgrade de tier ? Upsell de feature ? Limite d'usage ?

2. **Modèle produit** - Qu'est-ce qui est gratuit ? Qu'y a-t-il derrière le paywall ? Qu'est-ce qui déclenche les incitations ? Taux de conversion actuel ?

3. **Parcours utilisateur** - Quand cela apparaît-il ? Qu'ont-ils expérimenté ? Que cherchent-ils à faire ?

---

## Principes fondamentaux

### 1. La valeur avant la demande
- L'utilisateur doit avoir expérimenté une vraie valeur d'abord
- L'upgrade doit sembler une étape suivante naturelle
- Timing : après le "aha moment", pas avant

### 2. Montrer, pas seulement raconter
- Démontrer la valeur des fonctionnalités payantes
- Prévisualiser ce qu'ils manquent
- Rendre l'upgrade tangible

### 3. Chemin sans friction
- Facile à upgrader quand on est prêt
- Ne pas les forcer à chercher la tarification

### 4. Respecter le refus
- Ne pas piéger ni mettre la pression
- Faciliter la continuation en free
- Maintenir la confiance pour une conversion future

---

## Points de déclenchement du paywall

### Feature gates
Quand l'utilisateur clique sur une fonctionnalité payante uniquement :
- Explication claire de pourquoi c'est payant
- Montrer ce que fait la fonctionnalité
- Chemin rapide pour débloquer
- Option de continuer sans

### Limites d'usage
Quand l'utilisateur atteint une limite :
- Indication claire de la limite atteinte
- Montrer ce qu'apporte l'upgrade
- Ne pas bloquer brutalement

### Expiration du trial
Quand le trial touche à sa fin :
- Avertissements précoces (7, 3, 1 jour)
- "Ce qu'il se passe" clair à l'expiration
- Résumer la valeur reçue

### Incitations basées sur le temps
Après X jours d'usage gratuit :
- Rappel d'upgrade en douceur
- Mettre en avant les fonctionnalités payantes inutilisées
- Facile à ignorer

---

## Composants d'un écran de paywall

1. **Titre** - Mettre l'accent sur ce qu'ils obtiennent : "Débloquez [Fonctionnalité] pour [Bénéfice]"

2. **Démonstration de valeur** - Aperçu, avant/après, "Avec Pro vous pourriez..."

3. **Comparaison des fonctionnalités** - Mettre en évidence les différences clés, plan actuel marqué

4. **Tarification** - Claire, simple, options annuel vs. mensuel

5. **Social proof** - Citations de clients, "X équipes utilisent ceci"

6. **CTA** - Spécifique et orienté valeur : "Commencer à obtenir [Bénéfice]"

7. **Issue de secours** - "Pas maintenant" ou "Continuer en Free" clair

---

## Types spécifiques de paywall

### Paywall de feature lock
```
[Lock Icon]
This feature is available on Pro

[Feature preview/screenshot]

[Feature name] helps you [benefit]:
• [Capability]
• [Capability]

[Upgrade to Pro - $X/mo]
[Maybe Later]
```

### Paywall de limite d'usage
```
You've reached your free limit

[Progress bar at 100%]

Free: 3 projects | Pro: Unlimited

[Upgrade to Pro]  [Delete a project]
```

### Paywall d'expiration de trial
```
Your trial ends in 3 days

What you'll lose:
• [Feature used]
• [Data created]

What you've accomplished:
• Created X projects

[Continue with Pro]
[Remind me later]  [Downgrade]
```

---

## Timing et fréquence

### Quand afficher
- Après un moment de valeur, avant la frustration
- Après l'activation/aha moment
- En atteignant de vraies limites

### Quand NE PAS afficher
- Pendant l'onboarding (trop tôt)
- Quand ils sont dans un flow
- À répétition après un refus

### Règles de fréquence
- Limiter par session
- Cool-down après refus (jours, pas heures)
- Suivre les signaux d'agacement

---

## Optimisation du flux d'upgrade

### Du paywall au paiement
- Minimiser les étapes
- Rester in-context si possible
- Pré-remplir les informations connues

### Post-upgrade
- Accès immédiat aux fonctionnalités
- Confirmation et reçu
- Guidage vers les nouvelles fonctionnalités

---

## A/B Testing

### Quoi tester
- Timing de déclenchement
- Variations de titre/copy
- Présentation du prix
- Durée du trial
- Mise en avant des fonctionnalités
- Design/layout

### Métriques à suivre
- Taux d'impression du paywall
- Taux de clic vers l'upgrade
- Taux de complétion
- Revenu par utilisateur
- Taux de churn post-upgrade

**Pour des idées d'expérimentation complètes** : Voir [references/experiments.md](references/experiments.md)

---

## Anti-patterns à éviter

### Dark patterns
- Masquer le bouton de fermeture
- Sélection de plan confuse
- Copy culpabilisant

### Tueurs de conversion
- Demander avant que la valeur soit délivrée
- Incitations trop fréquentes
- Blocage de flows critiques
- Processus d'upgrade compliqué

---

## Questions spécifiques à la tâche

1. Quel est votre taux de conversion free → payant actuel ?
2. Qu'est-ce qui déclenche les incitations d'upgrade aujourd'hui ?
3. Quelles fonctionnalités sont derrière le paywall ?
4. Quel est votre "aha moment" pour les utilisateurs ?
5. Quel modèle de tarification ? (par siège, usage, flat)
6. App mobile, app web, ou les deux ?

---

## Skills associés

- **churn-prevention** : Pour les cancel flows, save offers, et réduire le churn post-upgrade
- **page-cro** : Pour l'optimisation de la page de tarification publique
- **onboarding-cro** : Pour amener au aha moment avant l'upgrade
- **ab-test-setup** : Pour tester les variations de paywall
