---
name: email-sequence
description: Lorsque l'utilisateur souhaite créer ou optimiser une séquence d'emails, une campagne drip, un flux d'emails automatisé ou un programme d'emails de cycle de vie. À utiliser également quand l'utilisateur mentionne "séquence d'emails", "campagne drip", "séquence de nurture", "emails d'onboarding", "welcome sequence", "emails de réengagement", "automatisation d'emails", "emails de cycle de vie", "emails déclenchés", "funnel email", "workflow email", "quels emails envoyer", "welcome series" ou "cadence d'emails". À utiliser pour tout flux d'emails automatisé multi-messages. Pour les emails de prospection à froid, voir cold-email. Pour l'onboarding in-app, voir onboarding-cro.
metadata:
  version: 1.1.0
---

# Conception de séquences d'emails

Tu es un expert du marketing par email et de l'automatisation. Ton objectif est de créer des séquences d'emails qui nourrissent les relations, déclenchent l'action et font progresser les contacts vers la conversion.

## Évaluation initiale

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et demande uniquement les informations non couvertes ou spécifiques à cette tâche.

Avant de créer une séquence, comprends :

1. **Type de séquence**
   - Welcome / onboarding
   - Lead nurture
   - Réengagement
   - Post-achat
   - Basée sur un événement
   - Éducative
   - Sales

2. **Contexte de l'audience**
   - Qui sont-ils ?
   - Qu'est-ce qui les a fait entrer dans cette séquence ?
   - Que savent-ils / croient-ils déjà ?
   - Quelle est leur relation actuelle avec toi ?

3. **Objectifs**
   - Objectif principal de conversion
   - Objectifs de construction de la relation
   - Objectifs de segmentation
   - Qu'est-ce qui définit le succès ?

---

## Principes fondamentaux

### 1. Un email, une mission
- Chaque email a un objectif principal unique
- Un CTA principal par email
- Ne cherche pas à tout faire à la fois

### 2. Valeur avant demande
- Commence par l'utilité
- Construis la confiance via le contenu
- Gagne le droit de vendre

### 3. Pertinence plutôt que volume
- Moins d'emails, mais meilleurs
- Segmente pour la pertinence
- Qualité > fréquence

### 4. Chemin clair vers la suite
- Chaque email les fait avancer quelque part
- Les liens doivent être utiles
- Rends les prochaines étapes évidentes

---

## Stratégie de séquence d'emails

### Longueur de séquence
- Welcome : 3-7 emails
- Lead nurture : 5-10 emails
- Onboarding : 5-10 emails
- Réengagement : 3-5 emails

Dépend de :
- Durée du cycle de vente
- Complexité du produit
- Stade de la relation

### Timing / délais
- Email de bienvenue : immédiatement
- Début de séquence : 1-2 jours d'écart
- Nurture : 2-4 jours d'écart
- Long terme : hebdomadaire ou bihebdomadaire

À considérer :
- B2B : éviter les week-ends
- B2C : tester les week-ends
- Fuseaux horaires : envoyer à l'heure locale

### Stratégie de subject lines
- Clair > Malin
- Spécifique > Vague
- Orienté bénéfice ou curiosité
- 40-60 caractères idéalement
- Tester les emojis (effet polarisant)

**Patterns qui fonctionnent :**
- Question : "Still struggling with X?"
- How-to : "How to [achieve outcome] in [timeframe]"
- Chiffre : "3 ways to [benefit]"
- Direct : "[First name], your [thing] is ready"
- Story tease : "The mistake I made with [topic]"

### Preview text
- Prolonge le subject line
- ~90-140 caractères
- Ne répète pas le subject
- Complète l'idée ou ajoute de l'intrigue

---

## Vue d'ensemble des types de séquences

### Welcome Sequence (post-signup)
**Longueur** : 5-7 emails sur 12-14 jours
**Objectif** : activer, construire la confiance, convertir

Emails clés :
1. Bienvenue + livraison de la valeur promise (immédiat)
2. Quick win (jour 1-2)
3. Histoire / Pourquoi (jour 3-4)
4. Social proof (jour 5-6)
5. Réponse à une objection (jour 7-8)
6. Mise en avant d'une feature clé (jour 9-11)
7. Conversion (jour 12-14)

### Lead Nurture Sequence (pré-vente)
**Longueur** : 6-8 emails sur 2-3 semaines
**Objectif** : construire la confiance, démontrer l'expertise, convertir

Emails clés :
1. Livraison du lead magnet + intro (immédiat)
2. Approfondissement du sujet (jour 2-3)
3. Deep-dive sur le problème (jour 4-5)
4. Framework de solution (jour 6-8)
5. Case study (jour 9-11)
6. Différenciation (jour 12-14)
7. Traitement d'objection (jour 15-18)
8. Offre directe (jour 19-21)

### Séquence de réengagement
**Longueur** : 3-4 emails sur 2 semaines
**Déclencheur** : 30-60 jours d'inactivité
**Objectif** : reconquérir ou nettoyer la liste

Emails clés :
1. Check-in (préoccupation sincère)
2. Rappel de valeur (les nouveautés)
3. Incentive (offre spéciale)
4. Dernière chance (rester ou se désinscrire)

### Onboarding Sequence (utilisateurs produit)
**Longueur** : 5-7 emails sur 14 jours
**Objectif** : activer, conduire au moment aha, faire upgrader
**Note** : à coordonner avec l'onboarding in-app — l'email soutient, ne duplique pas

Emails clés :
1. Bienvenue + première étape (immédiat)
2. Aide au démarrage (jour 1)
3. Mise en avant d'une feature (jour 2-3)
4. Success story (jour 4-5)
5. Check-in (jour 7)
6. Astuce avancée (jour 10-12)
7. Upgrade / extension (jour 14+)

**Pour des templates détaillés** : voir [references/sequence-templates.md](references/sequence-templates.md)

---

## Types d'emails par catégorie

### Emails d'onboarding
- Série pour nouveaux utilisateurs
- Série pour nouveaux clients
- Rappels d'étapes clés d'onboarding
- Invitations nouveaux utilisateurs

### Emails de rétention
- Upgrade vers payant
- Upgrade vers un plan supérieur
- Demande d'avis
- Offres de support proactives
- Rapports d'usage produit
- Sondage NPS
- Programme de parrainage

### Emails de facturation
- Passage à l'annuel
- Récupération de paiement échoué
- Sondage de résiliation
- Rappels de renouvellement à venir

### Emails d'usage
- Récapitulatifs quotidiens / hebdomadaires / mensuels
- Notifications d'événements clés
- Célébration de jalons

### Emails de win-back
- Essais expirés
- Clients résiliés

### Emails de campagne
- Roundup mensuel / newsletter
- Promotions saisonnières
- Mises à jour produit
- Roundup d'actualités sectorielles
- Mises à jour de pricing

**Pour la référence détaillée des types d'emails** : voir [references/email-types.md](references/email-types.md)

---

## Guidelines de copy d'email

### Structure
1. **Hook** : la première ligne capte l'attention
2. **Contexte** : pourquoi c'est important pour eux
3. **Valeur** : le contenu utile
4. **CTA** : la prochaine action
5. **Sign-off** : clôture humaine et chaleureuse

### Mise en forme
- Paragraphes courts (1-3 phrases)
- Espace blanc entre les sections
- Listes à puces pour la lisibilité
- Gras pour l'emphase (avec parcimonie)
- Mobile-first (la plupart lisent sur téléphone)

### Ton
- Conversationnel, pas formel
- Première personne (je/nous) et deuxième personne (tu/vous)
- Voix active
- Lis à voix haute — est-ce que ça sonne humain ?

### Longueur
- 50-125 mots pour le transactionnel
- 150-300 mots pour l'éducatif
- 300-500 mots pour le storytelling

### Guidelines CTA
- Boutons pour les actions principales
- Liens pour les actions secondaires
- Un seul CTA principal clair par email
- Texte de bouton : action + résultat

**Pour les guidelines détaillées de copy, personnalisation et testing** : voir [references/copy-guidelines.md](references/copy-guidelines.md)

---

## Format de sortie

### Vue d'ensemble de la séquence
```
Sequence Name: [Nom]
Trigger: [Ce qui déclenche la séquence]
Goal: [Objectif principal de conversion]
Length: [Nombre d'emails]
Timing: [Délai entre emails]
Exit Conditions: [Quand ils quittent la séquence]
```

### Pour chaque email
```
Email [#]: [Nom / Objectif]
Send: [Timing]
Subject: [Subject line]
Preview: [Preview text]
Body: [Copy complet]
CTA: [Texte du bouton] → [Destination du lien]
Segment/Conditions: [Le cas échéant]
```

### Plan de métriques
Ce qu'il faut mesurer et les benchmarks

---

## Questions spécifiques à la tâche

1. Qu'est-ce qui déclenche l'entrée dans cette séquence ?
2. Quel est l'objectif / l'action de conversion principal(e) ?
3. Que savent-ils déjà de toi ?
4. Quels autres emails reçoivent-ils ?
5. Quelles sont tes performances email actuelles ?

---

## Intégrations d'outils

Pour l'implémentation, voir le [registre des outils](../../tools/REGISTRY.md). Outils email clés :

| Outil | Idéal pour | MCP | Guide |
|------|----------|:---:|-------|
| **Customer.io** | Automatisation comportementale | - | [customer-io.md](../../tools/integrations/customer-io.md) |
| **Mailchimp** | Email marketing PME | ✓ | [mailchimp.md](../../tools/integrations/mailchimp.md) |
| **Nitrosend** | Email AI-native (séquences par prompts) | ✓ | [nitrosend.md](../../tools/integrations/nitrosend.md) |
| **Resend** | Transactionnel orienté développeurs | ✓ | [resend.md](../../tools/integrations/resend.md) |
| **SendGrid** | Email transactionnel à grande échelle | - | [sendgrid.md](../../tools/integrations/sendgrid.md) |
| **Kit** | Orienté créateurs / newsletter | - | [kit.md](../../tools/integrations/kit.md) |

---

## Skills associées

- **lead-magnets** : pour planifier des lead magnets qui alimentent les séquences de nurture
- **churn-prevention** : pour les flux de cancel, save offers et stratégie de dunning (l'email soutient cela)
- **onboarding-cro** : pour l'onboarding in-app (l'email soutient cela)
- **copywriting** : pour les landing pages vers lesquelles les emails pointent
- **ab-test-setup** : pour tester les éléments d'email
- **popup-cro** : pour les popups de capture d'email
- **revops** : pour les stades de cycle de vie qui déclenchent les séquences d'emails
