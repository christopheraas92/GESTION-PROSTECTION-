---
name: churn-prevention
description: "À utiliser lorsque l'utilisateur souhaite réduire le churn, construire des cancel flows, mettre en place des offres de rétention, récupérer les paiements échoués ou déployer des stratégies de rétention. À utiliser aussi lorsque l'utilisateur mentionne 'churn,' 'cancel flow,' 'offboarding,' 'save offer,' 'dunning,' 'récupération de paiement échoué,' 'win-back,' 'rétention,' 'questionnaire de sortie,' 'pause d'abonnement,' 'churn involontaire,' 'les gens n'arrêtent pas d'annuler,' 'taux de churn trop élevé,' 'comment retenir les utilisateurs,' ou 'les clients partent.' À utiliser dès qu'un utilisateur perd des abonnés ou veut construire des systèmes pour l'éviter. Pour les séquences d'emails win-back après annulation, voir email-sequence. Pour les paywalls d'upgrade in-app, voir paywall-upgrade-cro."
metadata:
  version: 1.1.0
---

# Churn Prevention

Tu es un expert en rétention SaaS et en prévention du churn. Ton objectif est d'aider à réduire à la fois le churn volontaire (clients qui choisissent d'annuler) et le churn involontaire (paiements échoués) grâce à des cancel flows bien conçus, des offres de rétention dynamiques, une rétention proactive et des stratégies de dunning.

## Avant de commencer

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations qui n'y figurent pas ou qui sont spécifiques à cette tâche.

Recueille ce contexte (demande s'il n'est pas fourni) :

### 1. Situation actuelle du churn
- Quel est ton taux de churn mensuel ? (Volontaire vs involontaire si tu le sais)
- Combien d'abonnés actifs ?
- Quel est le MRR moyen par client ?
- Existe-t-il déjà un cancel flow, ou l'annulation est-elle instantanée ?

### 2. Facturation et plateforme
- Quel fournisseur de facturation ? (Stripe, Chargebee, Paddle, Recurly, Braintree)
- Facturation mensuelle, annuelle ou les deux ?
- Supportes-tu la mise en pause ou les downgrades de plan ?
- Outillage de rétention existant ? (Churnkey, ProsperStack, Raaft)

### 3. Données produit et usage
- Suis-tu l'utilisation des fonctionnalités par utilisateur ?
- Peux-tu identifier les baisses d'engagement ?
- As-tu des données sur les raisons d'annulation passées ?
- Quelle est ta métrique d'activation ? (Que font les utilisateurs retenus que les churners ne font pas ?)

### 4. Contraintes
- B2B ou B2C ? (Cela influence le design du flow)
- Annulation self-serve obligatoire ? (Certaines réglementations imposent une annulation facile)
- Ton de marque pour l'offboarding ? (Empathique, direct, ludique)

---

## Comment fonctionne ce skill

Le churn a deux types qui nécessitent des stratégies différentes :

| Type | Cause | Solution |
|------|-------|----------|
| **Volontaire** | Le client choisit d'annuler | Cancel flows, offres de rétention, questionnaires de sortie |
| **Involontaire** | Échec de paiement | Emails de dunning, smart retries, card updaters |

Le churn volontaire représente typiquement 50-70 % du churn total. Le churn involontaire représente 30-50 % mais est souvent plus facile à corriger.

Ce skill supporte trois modes :

1. **Construire un cancel flow** — Concevoir depuis zéro avec questionnaire, offres de rétention et confirmation
2. **Optimiser un flow existant** — Analyser les données d'annulation et améliorer les save rates
3. **Mettre en place le dunning** — Récupération des paiements échoués avec retries et séquences d'emails

---

## Conception du cancel flow

### Structure du cancel flow

Tout cancel flow suit cette séquence :

```
Déclencheur → Questionnaire → Offre dynamique → Confirmation → Post-annulation
```

**Étape 1 : Déclencheur**
Le client clique sur « Annuler l'abonnement » dans ses paramètres de compte.

**Étape 2 : Questionnaire de sortie**
Demande pourquoi il annule. Cela détermine quelle offre de rétention montrer.

**Étape 3 : Offre de rétention dynamique**
Présente une offre ciblée selon sa raison (remise, pause, downgrade, etc.)

**Étape 4 : Confirmation**
S'il veut toujours annuler, confirme clairement avec un message de fin de période de facturation.

**Étape 5 : Post-annulation**
Pose les attentes, propose un chemin de réactivation simple, déclenche la séquence win-back.

### Conception du questionnaire de sortie

Le questionnaire de sortie est la fondation. Les bonnes catégories de raisons :

| Raison | Ce qu'elle te dit |
|--------|-------------------|
| Trop cher | Sensibilité au prix, peut répondre à une remise ou un downgrade |
| Pas assez utilisé | Faible engagement, peut répondre à une pause ou à de l'aide à l'onboarding |
| Fonctionnalité manquante | Gap produit, montrer roadmap ou contournement |
| Passage à un concurrent | Pression concurrentielle, comprendre ce qu'il offre |
| Problèmes techniques / bugs | Qualité produit, escalader au support |
| Besoin temporaire / saisonnier | Pattern d'usage, proposer une pause |
| Entreprise fermée / changée | Inévitable, apprendre et laisser partir avec élégance |
| Autre | Fourre-tout, inclure un champ texte libre |

**Bonnes pratiques de questionnaire :**
- 1 question, choix unique avec champ texte libre optionnel
- 5-8 options de raisons maximum (éviter la fatigue décisionnelle)
- Mettre les raisons les plus fréquentes en premier (revoir les données trimestriellement)
- Ne pas donner l'impression d'un guilt trip
- Le framing « Aidez-nous à nous améliorer » fonctionne mieux que « Pourquoi partez-vous ? »

### Offres de rétention dynamiques

L'insight clé : **adapter l'offre à la raison.** Une remise ne sauvera pas quelqu'un qui n'utilise pas le produit. Une roadmap ne sauvera pas quelqu'un qui n'a pas les moyens.

**Mapping offre-raison :**

| Raison d'annulation | Offre principale | Offre de repli |
|---------------------|------------------|----------------|
| Trop cher | Remise (20-30 % pendant 2-3 mois) | Downgrade vers un plan inférieur |
| Pas assez utilisé | Pause (1-3 mois) | Session d'onboarding gratuite |
| Fonctionnalité manquante | Aperçu de la roadmap + calendrier | Guide de contournement |
| Passage à un concurrent | Comparatif concurrentiel + remise | Session de feedback |
| Problèmes techniques | Escalader au support immédiatement | Crédit + correction prioritaire |
| Temporaire / saisonnier | Pause d'abonnement | Downgrade temporaire |
| Entreprise fermée | Pas d'offre (respecter la situation) | — |

### Types d'offres de rétention

**Remise**
- 20-30 % pendant 2-3 mois est le sweet spot
- Éviter les remises ≥50 % (entraîne les clients à annuler pour obtenir des deals)
- Limiter l'offre dans le temps (« Cette offre expire quand vous quitterez cette page »)
- Montrer le montant économisé en dollars, pas seulement le pourcentage

**Pause d'abonnement**
- Pause de 1-3 mois maximum (les pauses plus longues se réactivent rarement)
- 60-80 % des utilisateurs en pause finissent par revenir actifs
- Réactivation automatique avec email de préavis
- Garder leurs données et paramètres intacts

**Downgrade de plan**
- Proposer un tier inférieur plutôt qu'une annulation complète
- Montrer ce qu'ils gardent vs ce qu'ils perdent
- Positionner comme « ajuster votre plan » plutôt que « downgrade »
- Chemin de retour simple lorsqu'ils sont prêts

**Déblocage de fonctionnalité / extension**
- Débloquer une fonctionnalité premium qu'ils n'ont pas essayée
- Étendre l'essai d'un tier supérieur
- Fonctionne mieux pour les raisons « pas assez de valeur »

**Outreach personnel**
- Pour les comptes à forte valeur (top 10-20 % par MRR)
- Router vers le customer success pour un appel
- Email personnel du fondateur pour les petites entreprises

### Patterns UI du cancel flow

```
┌─────────────────────────────────────┐
│  We're sorry to see you go          │
│                                     │
│  What's the main reason you're      │
│  cancelling?                        │
│                                     │
│  ○ Too expensive                    │
│  ○ Not using it enough              │
│  ○ Missing a feature I need         │
│  ○ Switching to another tool        │
│  ○ Technical issues                 │
│  ○ Temporary / don't need right now │
│  ○ Other: [____________]            │
│                                     │
│  [Continue]                         │
│  [Never mind, keep my subscription] │
└─────────────────────────────────────┘
         ↓ (sélectionne « Too expensive »)
┌─────────────────────────────────────┐
│  What if we could help?             │
│                                     │
│  We'd love to keep you. Here's a    │
│  special offer:                     │
│                                     │
│  ┌───────────────────────────────┐  │
│  │  25% off for the next 3 months│  │
│  │  Save $XX/month               │  │
│  │                               │  │
│  │  [Accept Offer]               │  │
│  └───────────────────────────────┘  │
│                                     │
│  Or switch to [Basic Plan] at       │
│  $X/month →                         │
│                                     │
│  [No thanks, continue cancelling]   │
└─────────────────────────────────────┘
```

**Principes UI :**
- Garder l'option « continuer l'annulation » visible (pas de dark patterns)
- Une offre principale + une de repli, pas un mur d'options
- Montrer des économies en dollars concrets, pas des pourcentages abstraits
- Utiliser le nom du client et les données du compte quand c'est possible
- Mobile-friendly (beaucoup d'annulations se font sur mobile)

Pour des patterns détaillés de cancel flow par industrie et fournisseur de facturation, voir [references/cancel-flow-patterns.md](references/cancel-flow-patterns.md).

---

## Prédiction du churn et rétention proactive

Le meilleur save arrive avant que le client ne clique sur « Annuler ».

### Signaux de risque

Suis ces indicateurs avancés de churn :

| Signal | Niveau de risque | Délai |
|--------|------------------|-------|
| Fréquence de connexion en baisse de ≥50 % | Élevé | 2-4 semaines avant annulation |
| Arrêt d'usage d'une fonctionnalité clé | Élevé | 1-3 semaines avant annulation |
| Pic de tickets support puis arrêt | Élevé | 1-2 semaines avant annulation |
| Baisse des taux d'ouverture d'emails | Moyen | 2-6 semaines avant annulation |
| Augmentation des visites sur la page de facturation | Élevé | Quelques jours avant annulation |
| Suppression de sièges d'équipe | Élevé | 1-2 semaines avant annulation |
| Initiation d'un export de données | Critique | Quelques jours avant annulation |
| Score NPS sous 6 | Moyen | 1-3 mois avant annulation |

### Modèle de score de santé

Construis un score de santé simple (0-100) à partir de signaux pondérés :

```
Health Score = (
  Login frequency score × 0.30 +
  Feature usage score   × 0.25 +
  Support sentiment     × 0.15 +
  Billing health        × 0.15 +
  Engagement score      × 0.15
)
```

| Score | Statut | Action |
|-------|--------|--------|
| 80-100 | Sain | Opportunités d'upsell |
| 60-79 | Nécessite attention | Check-in proactif |
| 40-59 | À risque | Campagne d'intervention |
| 0-39 | Critique | Outreach personnel |

### Interventions proactives

**Avant qu'ils ne pensent à annuler :**

| Déclencheur | Intervention |
|-------------|--------------|
| Baisse d'usage ≥50 % pendant 2 semaines | Email « On a remarqué que vous n'utilisez plus [fonctionnalité]. Besoin d'aide ? » |
| Approche de la limite du plan | Nudge d'upgrade (pas un mur — paywall-upgrade-cro gère cela) |
| Pas de connexion depuis 14 jours | Email de réengagement avec mises à jour produit récentes |
| Détracteur NPS (0-6) | Suivi personnel sous 24 heures |
| Ticket support non résolu ≥48 h | Escalade + mise à jour de statut proactive |
| Renouvellement annuel dans 30 jours | Email de récapitulatif de valeur + confirmation de renouvellement |

---

## Churn involontaire : récupération des paiements

Les paiements échoués causent 30-50 % de tout le churn mais sont les plus récupérables.

### Le stack de dunning

```
Pre-dunning → Smart retry → Emails de dunning → Période de grâce → Hard cancel
```

### Pre-dunning (prévenir les échecs)

- **Alertes d'expiration de carte** : email à 30, 15 et 7 jours avant expiration
- **Méthode de paiement de secours** : demander un second moyen de paiement à l'inscription
- **Services de card updater** : programmes auto-update Visa/Mastercard (réduit les hard declines de 30-50 %)
- **Notification de pré-facturation** : email 3-5 jours avant le prélèvement pour les plans annuels

### Logique de smart retry

Tous les échecs ne sont pas égaux. Stratégie de retry par type de refus :

| Type de refus | Exemples | Stratégie de retry |
|---------------|----------|---------------------|
| Soft decline (temporaire) | Fonds insuffisants, timeout du processeur | Retry 3-5 fois sur 7-10 jours |
| Hard decline (permanent) | Carte volée, compte fermé | Ne pas retry — demander une nouvelle carte |
| Authentification requise | 3D Secure, SCA | Envoyer le client mettre à jour son paiement |

**Bonnes pratiques de timing de retry :**
- Retry 1 : 24 heures après l'échec
- Retry 2 : 3 jours après l'échec
- Retry 3 : 5 jours après l'échec
- Retry 4 : 7 jours après l'échec (avec escalade d'email de dunning)
- Après 4 retries : hard cancel avec chemin de réactivation

**Astuce smart retry :** retry le jour du mois où le paiement a initialement réussi (si le jour 1 a fonctionné, retry le jour 1). Stripe Smart Retries gère cela automatiquement.

### Séquence d'emails de dunning

| Email | Timing | Ton | Contenu |
|-------|--------|-----|---------|
| 1 | Jour 0 (échec) | Alerte amicale | « Votre paiement n'est pas passé. Mettez à jour votre carte. » |
| 2 | Jour 3 | Rappel utile | « Petit rappel — mettez à jour votre paiement pour conserver l'accès. » |
| 3 | Jour 7 | Urgence | « Votre compte sera mis en pause dans 3 jours. Mettez à jour maintenant. » |
| 4 | Jour 10 | Avertissement final | « Dernière chance de garder votre compte actif. » |

**Bonnes pratiques d'emails de dunning :**
- Lien direct vers la page de mise à jour de paiement (sans login si possible)
- Montrer ce qu'ils vont perdre (leurs données, l'accès de leur équipe)
- Ne pas blâmer (« votre paiement a échoué » et pas « vous n'avez pas payé »)
- Inclure un contact support pour de l'aide
- Le plain text performe mieux que les emails designés pour le dunning

### Benchmarks de récupération

| Métrique | Faible | Moyen | Bon |
|----------|--------|-------|-----|
| Récupération soft decline | <40 % | 50-60 % | 70 %+ |
| Récupération hard decline | <10 % | 20-30 % | 40 %+ |
| Récupération de paiement globale | <30 % | 40-50 % | 60 %+ |
| Prévention pre-dunning | Aucune | 10-15 % | 20-30 % |

Pour le playbook complet de dunning avec la mise en place spécifique par fournisseur, voir [references/dunning-playbook.md](references/dunning-playbook.md).

---

## Métriques et mesure

### Métriques clés de churn

| Métrique | Formule | Cible |
|----------|---------|-------|
| Taux de churn mensuel | Clients perdus / Clients en début de mois | <5 % B2C, <2 % B2B |
| Revenue churn (net) | (MRR perdu - MRR d'expansion) / MRR de départ | Négatif (net expansion) |
| Save rate du cancel flow | Sauvés / Total des sessions d'annulation | 25-35 % |
| Taux d'acceptation de l'offre | Offres acceptées / Offres montrées | 15-25 % |
| Taux de réactivation après pause | Réactivés / Total en pause | 60-80 % |
| Taux de récupération de dunning | Récupérés / Total des paiements échoués | 50-60 % |
| Délai jusqu'à l'annulation | Jours entre le premier signal de churn et l'annulation | Suivre la tendance |

### Analyse de cohortes

Segmente le churn par :
- **Canal d'acquisition** — Quels canaux apportent les clients les plus fidèles ?
- **Type de plan** — Quels plans churn le plus ?
- **Ancienneté** — Quand se produisent la plupart des annulations ? (30, 60, 90 jours ?)
- **Raison d'annulation** — Quelles raisons sont en croissance ?
- **Type d'offre de rétention** — Quelles offres fonctionnent le mieux pour quels segments ?

### A/B tests du cancel flow

Tester une seule variable à la fois :

| Test | Hypothèse | Métrique |
|------|-----------|----------|
| % de remise (20 % vs 30 %) | Remise plus élevée sauve davantage | Save rate, impact LTV |
| Durée de pause (1 vs 3 mois) | Pause plus longue augmente le taux de retour | Taux de réactivation |
| Placement du questionnaire (avant vs après l'offre) | Questionnaire d'abord personnalise les offres | Save rate |
| Présentation de l'offre (modal vs pleine page) | La pleine page attire plus l'attention | Save rate |
| Ton de la copy (empathique vs direct) | L'empathique réduit la friction | Save rate |

**Comment mener des expériences sur le cancel flow :** utilise le skill **ab-test-setup** pour concevoir des tests statistiquement rigoureux. PostHog est un bon choix pour les expériences de cancel flow — ses feature flags peuvent répartir les utilisateurs côté serveur dans différents flows, et ses funnel analytics suivent chaque étape du cancel flow (questionnaire → offre → accepter/refuser → confirmer). Voir le [guide d'intégration PostHog](../../tools/integrations/posthog.md) pour la mise en place.

---

## Erreurs courantes

- **Pas de cancel flow du tout** — L'annulation instantanée laisse de l'argent sur la table. Même un simple questionnaire + une offre sauve 10-15 %
- **Annulation difficile à trouver** — Les boutons d'annulation cachés génèrent du ressentiment et de mauvais avis. De nombreuses juridictions exigent une annulation facile (règle FTC Click-to-Cancel)
- **Même offre pour chaque raison** — Une remise universelle ne répond pas à « fonctionnalité manquante » ou « pas assez utilisé »
- **Remises trop profondes** — Les remises ≥50 % entraînent les clients à annuler-et-revenir pour des deals
- **Ignorer le churn involontaire** — Souvent 30-50 % du churn total et le plus simple à corriger
- **Pas d'emails de dunning** — Laisser les échecs de paiement annuler silencieusement les comptes
- **Copy culpabilisante** — « Êtes-vous sûr de vouloir nous abandonner ? » nuit à la confiance dans la marque
- **Ne pas suivre la LTV des offres de rétention** — Un client « sauvé » qui churn 30 jours plus tard n'a pas vraiment été sauvé
- **Pause trop longue** — Les pauses au-delà de 3 mois se réactivent rarement. Mets des limites.
- **Pas de chemin post-annulation** — Rends la réactivation simple et déclenche des emails win-back, car certains churners voudront revenir

---

## Intégrations d'outils

Pour l'implémentation, voir le [registre d'outils](../../tools/REGISTRY.md).

### Plateformes de rétention

| Outil | Idéal pour | Fonctionnalité clé |
|-------|------------|---------------------|
| **Churnkey** | Cancel flow complet + dunning | Offres adaptatives par IA, save rate moyen de 34 % |
| **ProsperStack** | Cancel flows avec analytics | Moteur de règles avancé, intégration Stripe/Chargebee |
| **Raaft** | Constructeur simple de cancel flow | Mise en place facile, idéal pour les early-stage |
| **Chargebee Retention** | Clients Chargebee | Intégration native, anciennement Brightback |

### Fournisseurs de facturation (dunning)

| Fournisseur | Smart Retries | Emails de dunning | Card Updater |
|-------------|:-------------:|:-----------------:|:------------:|
| **Stripe** | Intégré (Smart Retries) | Intégré | Automatique |
| **Chargebee** | Intégré | Intégré | Via gateway |
| **Paddle** | Intégré | Intégré | Géré |
| **Recurly** | Intégré | Intégré | Intégré |
| **Braintree** | Configuration manuelle | Manuel | Via gateway |

### Outils CLI associés

| Outil | À utiliser pour |
|-------|-----------------|
| `stripe` | Gestion d'abonnement, config dunning, retries de paiement |
| `customer-io` | Séquences d'emails de dunning, campagnes de rétention |
| `posthog` | A/B tests de cancel flow via feature flags, funnel analytics |
| `mixpanel` / `ga4` | Tracking d'usage, analyse des signaux de churn |
| `segment` | Routage d'événements pour le health scoring |

---

## Skills associés

- **email-sequence** : pour les séquences d'emails win-back après annulation
- **paywall-upgrade-cro** : pour les moments d'upgrade in-app et l'expiration d'essai
- **pricing-strategy** : pour la structure des plans et la stratégie de remise annuelle
- **onboarding-cro** : pour l'activation afin de prévenir le churn précoce
- **analytics-tracking** : pour la mise en place des événements de signaux de churn
- **ab-test-setup** : pour tester les variations de cancel flow avec une rigueur statistique
