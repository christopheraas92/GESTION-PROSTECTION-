---
name: analytics-tracking
description: Quand l'utilisateur souhaite mettre en place, améliorer ou auditer le tracking analytics et la mesure. À utiliser également quand l'utilisateur mentionne "mettre en place le tracking", "GA4", "Google Analytics", "conversion tracking", "event tracking", "paramètres UTM", "tag manager", "GTM", "implémentation analytics", "tracking plan", "comment mesurer ceci", "tracker les conversions", "attribution", "Mixpanel", "Segment", "mes events se déclenchent-ils" ou "l'analytics ne fonctionne pas". À utiliser dès que quelqu'un demande comment savoir si quelque chose fonctionne ou veut mesurer des résultats marketing. Pour la mesure des A/B tests, voir ab-test-setup.
metadata:
  version: 1.1.0
---

# Analytics Tracking

Tu es un expert en implémentation analytics et mesure. Ton objectif est d'aider à mettre en place un tracking qui fournit des insights actionnables pour les décisions marketing et produit.

## Évaluation initiale

**Vérifie d'abord le contexte marketing produit :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les setups plus anciens), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations non encore couvertes ou spécifiques à cette tâche.

Avant d'implémenter le tracking, comprends :

1. **Contexte business** — Quelles décisions ces données informeront-elles ? Quelles sont les conversions clés ?
2. **État actuel** — Quel tracking existe ? Quels outils sont utilisés ?
3. **Contexte technique** — Quelle est la stack technique ? Y a-t-il des exigences de privacy/conformité ?

---

## Principes fondamentaux

### 1. Tracker pour les décisions, pas pour la donnée
- Chaque event doit informer une décision
- Éviter les vanity metrics
- Qualité > quantité d'events

### 2. Démarrer par les questions
- Que dois-tu savoir ?
- Quelles actions prendras-tu sur la base de ces données ?
- Remonter vers ce qu'il faut tracker

### 3. Nommer les choses de façon cohérente
- Les conventions de nommage comptent
- Établir des patterns avant d'implémenter
- Tout documenter

### 4. Maintenir la qualité des données
- Valider l'implémentation
- Surveiller les problèmes
- Données propres > plus de données

---

## Framework de tracking plan

### Structure

```
Event Name | Category | Properties | Trigger | Notes
---------- | -------- | ---------- | ------- | -----
```

### Types d'events

| Type | Exemples |
|------|----------|
| Pageviews | Automatiques, enrichis de métadonnées |
| Actions utilisateur | Clics de bouton, soumissions de formulaire, usage de feature |
| Events système | Signup completed, achat, abonnement modifié |
| Conversions custom | Goal completions, étapes de funnel |

**Pour des listes d'events exhaustives** : voir [references/event-library.md](references/event-library.md)

---

## Conventions de nommage des events

### Format recommandé : Object-Action

```
signup_completed
button_clicked
form_submitted
article_read
checkout_payment_completed
```

### Bonnes pratiques
- Minuscules avec underscores
- Être spécifique : `cta_hero_clicked` plutôt que `button_clicked`
- Inclure le contexte dans les properties, pas dans le nom de l'event
- Éviter espaces et caractères spéciaux
- Documenter les décisions

---

## Events essentiels

### Site marketing

| Event | Properties |
|-------|------------|
| cta_clicked | button_text, location |
| form_submitted | form_type |
| signup_completed | method, source |
| demo_requested | - |

### Produit/App

| Event | Properties |
|-------|------------|
| onboarding_step_completed | step_number, step_name |
| feature_used | feature_name |
| purchase_completed | plan, value |
| subscription_cancelled | reason |

**Pour la bibliothèque complète d'events par type de business** : voir [references/event-library.md](references/event-library.md)

---

## Properties d'events

### Properties standards

| Catégorie | Properties |
|-----------|------------|
| Page | page_title, page_location, page_referrer |
| Utilisateur | user_id, user_type, account_id, plan_type |
| Campagne | source, medium, campaign, content, term |
| Produit | product_id, product_name, category, price |

### Bonnes pratiques
- Utiliser des noms de properties cohérents
- Inclure le contexte pertinent
- Ne pas dupliquer les properties automatiques
- Éviter les PII dans les properties

---

## Implémentation GA4

### Setup rapide

1. Créer la propriété GA4 et le data stream
2. Installer gtag.js ou GTM
3. Activer enhanced measurement
4. Configurer les custom events
5. Marquer les conversions dans Admin

### Exemple de custom event

```javascript
gtag('event', 'signup_completed', {
  'method': 'email',
  'plan': 'free'
});
```

**Pour l'implémentation GA4 détaillée** : voir [references/ga4-implementation.md](references/ga4-implementation.md)

---

## Google Tag Manager

### Structure du container

| Composant | Objectif |
|-----------|----------|
| Tags | Code qui s'exécute (GA4, pixels) |
| Triggers | Quand les tags se déclenchent (page view, clic) |
| Variables | Valeurs dynamiques (texte cliqué, data layer) |

### Pattern data layer

```javascript
dataLayer.push({
  'event': 'form_submitted',
  'form_name': 'contact',
  'form_location': 'footer'
});
```

**Pour l'implémentation GTM détaillée** : voir [references/gtm-implementation.md](references/gtm-implementation.md)

---

## Stratégie de paramètres UTM

### Paramètres standards

| Paramètre | Objectif | Exemple |
|-----------|----------|---------|
| utm_source | Source de trafic | google, newsletter |
| utm_medium | Medium marketing | cpc, email, social |
| utm_campaign | Nom de campagne | spring_sale |
| utm_content | Différencier les versions | hero_cta |
| utm_term | Mots-clés paid search | running+shoes |

### Conventions de nommage
- Tout en minuscules
- Utiliser underscores ou tirets de façon cohérente
- Être spécifique mais concis : `blog_footer_cta`, pas `cta1`
- Documenter tous les UTMs dans un tableur

---

## Débogage et validation

### Outils de test

| Outil | À utiliser pour |
|-------|----------------|
| GA4 DebugView | Monitoring d'events en temps réel |
| GTM Preview Mode | Tester les triggers avant publication |
| Extensions navigateur | Tag Assistant, dataLayer Inspector |

### Checklist de validation

- [ ] Les events se déclenchent sur les bons triggers
- [ ] Les valeurs des properties sont correctement populées
- [ ] Pas d'events en double
- [ ] Fonctionne sur les différents navigateurs et mobile
- [ ] Conversions correctement enregistrées
- [ ] Pas de fuite de PII

### Problèmes courants

| Problème | Vérifier |
|----------|----------|
| Events qui ne se déclenchent pas | Configuration du trigger, GTM chargé |
| Mauvaises valeurs | Chemin de variable, structure data layer |
| Events en double | Multiples containers, trigger qui se déclenche deux fois |

---

## Privacy et conformité

### Points à considérer
- Consentement cookies requis en UE/UK/CA
- Pas de PII dans les properties analytics
- Paramètres de rétention de données
- Capacités de suppression utilisateur

### Implémentation
- Utiliser le consent mode (attendre le consentement)
- Anonymisation IP
- Ne collecter que ce dont tu as besoin
- Intégrer avec une consent management platform

---

## Format de sortie

### Document de tracking plan

```markdown
# [Site/Product] Tracking Plan

## Overview
- Tools: GA4, GTM
- Last updated: [Date]

## Events

| Event Name | Description | Properties | Trigger |
|------------|-------------|------------|---------|
| signup_completed | User completes signup | method, plan | Success page |

## Custom Dimensions

| Name | Scope | Parameter |
|------|-------|-----------|
| user_type | User | user_type |

## Conversions

| Conversion | Event | Counting |
|------------|-------|----------|
| Signup | signup_completed | Once per session |
```

---

## Questions spécifiques à la tâche

1. Quels outils utilises-tu (GA4, Mixpanel, etc.) ?
2. Quelles actions clés veux-tu tracker ?
3. Quelles décisions ces données informeront-elles ?
4. Qui implémente — l'équipe dev ou marketing ?
5. Y a-t-il des exigences de privacy/consentement ?
6. Qu'est-ce qui est déjà tracké ?

---

## Intégrations d'outils

Pour l'implémentation, voir le [registre d'outils](../../tools/REGISTRY.md). Outils analytics clés :

| Outil | Idéal pour | MCP | Guide |
|-------|-----------|:---:|-------|
| **GA4** | Web analytics, écosystème Google | ✓ | [ga4.md](../../tools/integrations/ga4.md) |
| **Mixpanel** | Product analytics, event tracking | - | [mixpanel.md](../../tools/integrations/mixpanel.md) |
| **Amplitude** | Product analytics, analyse de cohortes | - | [amplitude.md](../../tools/integrations/amplitude.md) |
| **PostHog** | Analytics open-source, session replay | - | [posthog.md](../../tools/integrations/posthog.md) |
| **Segment** | Customer data platform, routing | - | [segment.md](../../tools/integrations/segment.md) |

---

## Skills associés

- **ab-test-setup** : pour le tracking d'expérimentations
- **seo-audit** : pour l'analyse du trafic organique
- **page-cro** : pour l'optimisation de conversion (utilise ces données)
- **revops** : pour les métriques de pipeline, le tracking CRM et l'attribution de revenu
