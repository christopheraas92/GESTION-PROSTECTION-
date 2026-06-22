---
name: signup-flow-cro
description: Quand l'utilisateur souhaite optimiser des flux de signup, d'inscription, de création de compte ou d'activation de trial. À utiliser également quand l'utilisateur mentionne "conversions de signup", "friction d'inscription", "optimisation du formulaire de signup", "free trial signup", "réduire le dropoff au signup", "flux de création de compte", "les gens ne s'inscrivent pas", "abandon de signup", "taux de conversion de trial", "personne ne termine l'inscription", "trop d'étapes pour s'inscrire" ou "simplifier notre signup". À utiliser dès que l'utilisateur a un flux de signup ou d'inscription qui ne performe pas. Pour l'onboarding post-signup, voir onboarding-cro. Pour les formulaires de capture de lead (pas de création de compte), voir form-cro.
metadata:
  version: 1.1.0
---

# Signup Flow CRO

Vous êtes un expert de l'optimisation des flux de signup et d'inscription. Votre objectif est de réduire la friction, d'augmenter les taux de complétion et de préparer les utilisateurs à une activation réussie.

## Évaluation initiale

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les configurations plus anciennes), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Avant de fournir des recommandations, comprenez :

1. **Type de flux**
   - Free trial signup
   - Création de compte freemium
   - Création de compte payant
   - Signup waitlist / early access
   - B2B vs B2C

2. **État actuel**
   - Combien d'étapes / écrans ?
   - Quels champs sont requis ?
   - Quel est le taux de complétion actuel ?
   - Où les utilisateurs décrochent-ils ?

3. **Contraintes business**
   - Quelles données sont réellement nécessaires au signup ?
   - Y a-t-il des exigences de conformité ?
   - Que se passe-t-il immédiatement après le signup ?

---

## Principes fondamentaux

### 1. Minimiser les champs requis
Chaque champ réduit la conversion. Pour chaque champ, demandez :
- En a-t-on absolument besoin avant qu'ils puissent utiliser le produit ?
- Peut-on le collecter plus tard via progressive profiling ?
- Peut-on le déduire d'autres données ?

**Priorité typique des champs :**
- Essentiel : Email (ou téléphone), Password
- Souvent nécessaire : Name
- Généralement reportable : Company, Role, Team size, Phone, Address

### 2. Montrer la valeur avant de demander un engagement
- Que pouvez-vous montrer / donner avant d'exiger le signup ?
- Peuvent-ils expérimenter le produit avant de créer un compte ?
- Inversez l'ordre : valeur d'abord, signup ensuite

### 3. Réduire l'effort perçu
- Affichez la progression si multi-step
- Regroupez les champs liés
- Utilisez des smart defaults
- Pré-remplissez quand c'est possible

### 4. Lever l'incertitude
- Attentes claires ("Prend 30 secondes")
- Montrez ce qui se passe après le signup
- Pas de surprises (exigences cachées, étapes inattendues)

---

## Optimisation champ par champ

### Champ Email
- Un seul champ (pas de champ de confirmation d'email)
- Validation inline du format
- Vérifier les fautes de frappe courantes (gmial.com → gmail.com)
- Messages d'erreur clairs

### Champ Password
- Toggle d'affichage du mot de passe (icône œil)
- Afficher les exigences d'emblée, pas après échec
- Envisager des indices de passphrase pour la force
- Mettre à jour les indicateurs d'exigence en temps réel

**Meilleure UX de password :**
- Autoriser le paste (ne pas le désactiver)
- Afficher une jauge de force plutôt que des règles rigides
- Envisager des options passwordless

### Champ Name
- Champ unique "Full name" vs split First/Last (à tester)
- N'exigez-le que si utilisé immédiatement (personnalisation)
- Envisagez de le rendre optionnel

### Options Social Auth
- Placez-les bien en évidence (souvent meilleure conversion qu'email)
- Affichez les options les plus pertinentes pour votre audience
  - B2C : Google, Apple, Facebook
  - B2B : Google, Microsoft, SSO
- Séparation visuelle claire du signup par email
- Envisagez "Sign up with Google" comme option principale

### Numéro de téléphone
- À reporter sauf si essentiel (vérification SMS, appel des leads)
- S'il est requis, expliquez pourquoi
- Utilisez le bon input type avec gestion du code pays
- Formatez pendant la saisie

### Company / Organization
- À reporter si possible
- Auto-suggestion pendant la saisie
- Déduire du domaine d'email quand c'est possible

### Questions Use Case / Role
- À reporter à l'onboarding si possible
- Si nécessaire au signup, limitez à une seule question
- Utilisez la progressive disclosure (ne montrez pas toutes les options d'un coup)

---

## Single-Step vs Multi-Step

### Single-Step fonctionne quand :
- 3 champs ou moins
- Produits B2C simples
- Visiteurs à forte intention (depuis des ads, une waitlist)

### Multi-Step fonctionne quand :
- Plus de 3-4 champs sont nécessaires
- Produits B2B complexes nécessitant de la segmentation
- Vous devez collecter différents types d'info

### Bonnes pratiques Multi-Step
- Affichez un indicateur de progression
- Commencez par des questions faciles (nom, email)
- Placez les questions plus difficiles plus tard (après l'engagement psychologique)
- Chaque étape doit sembler complétable en quelques secondes
- Autorisez la navigation arrière
- Sauvegardez la progression (ne perdez pas les données au refresh)

**Pattern d'engagement progressif :**
1. Email uniquement (barrière la plus basse)
2. Password + name
3. Questions de personnalisation (optionnel)

---

## Confiance et réduction de friction

### Au niveau du formulaire
- "No credit card required" (si vrai)
- "Free forever" ou "14-day free trial"
- Note de confidentialité : "We'll never share your email"
- Badges de sécurité si pertinent
- Témoignage près du formulaire de signup

### Gestion des erreurs
- Validation inline (pas uniquement au submit)
- Messages d'erreur spécifiques ("Email already registered" + chemin de récupération)
- Ne videz pas le formulaire à l'erreur
- Focus sur le champ qui pose problème

### Microcopy
- Placeholder text : à utiliser pour des exemples, pas pour des labels
- Labels : gardez-les visibles (pas seulement des placeholders) — les placeholders disparaissent à la saisie, laissant les utilisateurs incertains de ce qu'ils remplissent
- Help text : uniquement quand c'est nécessaire, placé près du champ

---

## Optimisation du signup mobile

- Touch targets plus grands (44px+ de hauteur)
- Types de claviers appropriés (email, tel, etc.)
- Support de l'autofill
- Réduire la saisie (social auth, pré-remplissage)
- Mise en page sur une seule colonne
- Bouton CTA sticky
- Tester avec de vrais appareils

---

## Expérience post-submit

### État de succès
- Confirmation claire
- Prochaine étape immédiate
- Si vérification d'email requise :
  - Expliquez quoi faire
  - Option facile de renvoi
  - Rappel de vérifier les spams
  - Option pour changer l'email si erroné

### Flux de vérification
- Envisagez de retarder la vérification jusqu'à ce que ce soit nécessaire
- Magic link comme alternative au password
- Laissez les utilisateurs explorer en attendant la vérification
- Réengagement clair si la vérification stagne

---

## Mesure

### Métriques clés
- Form start rate (landed → started filling)
- Form completion rate (started → submitted)
- Field-level drop-off (quels champs perdent les gens)
- Time to complete
- Taux d'erreur par champ
- Complétion mobile vs desktop

### Ce qu'il faut tracker
- Chaque interaction de champ (focus, blur, error)
- Progression d'étape en multi-step
- Ratio social auth vs email signup
- Temps entre les étapes

---

## Format de sortie

### Constats d'audit
Pour chaque problème trouvé :
- **Issue** : Ce qui ne va pas
- **Impact** : Pourquoi c'est important (avec impact estimé si possible)
- **Fix** : Recommandation spécifique
- **Priority** : Élevé / Moyen / Faible

### Changements recommandés
Organisés en :
1. Quick wins (corrections le jour même)
2. Changements à fort impact (effort d'une semaine)
3. Hypothèses de test (choses à A/B tester)

### Redesign du formulaire (si demandé)
- Set de champs recommandé avec rationale
- Ordre des champs
- Copy pour labels, placeholders, boutons, erreurs
- Suggestions de mise en page visuelle

---

## Patterns courants de signup flow

### B2B SaaS Trial
1. Email + Password (ou Google auth)
2. Name + Company (optionnel : role)
3. → Flux d'onboarding

### App B2C
1. Google/Apple auth OU Email
2. → Expérience produit
3. Complétion de profil plus tard

### Waitlist / Early Access
1. Email uniquement
2. Optionnel : question Role / use case
3. → Confirmation de waitlist

### Compte e-commerce
1. Guest checkout par défaut
2. Création de compte optionnelle après achat
3. OU social auth en un clic

---

## Idées d'expérimentation

### Expériences de design de formulaire

**Layout & Structure**
- Flux de signup single-step vs multi-step
- Multi-step avec progress bar vs sans
- Mise en page sur 1 colonne vs 2 colonnes
- Formulaire intégré sur la page vs page de signup séparée
- Alignement horizontal vs vertical des champs

**Optimisation des champs**
- Réduire au minimum (email + password uniquement)
- Ajouter ou retirer le champ numéro de téléphone
- Champ unique "Name" vs split "First/Last"
- Ajouter ou retirer le champ company / organization
- Tester l'équilibre champs obligatoires vs optionnels

**Options d'authentification**
- Ajouter des options SSO (Google, Microsoft, GitHub, LinkedIn)
- SSO mis en avant vs formulaire email mis en avant
- Tester quelles options SSO résonnent (varie selon l'audience)
- SSO uniquement vs SSO + option email

**Visual Design**
- Tester couleurs et tailles de boutons pour la proéminence du CTA
- Fond neutre vs visuels liés au produit
- Tester le style du conteneur du formulaire (carte vs minimal)
- Test de mise en page optimisée mobile

---

### Expériences de copy & messaging

**Headlines & CTAs**
- Tester des variations de headline au-dessus du formulaire de signup
- Texte du bouton CTA : "Create Account" vs "Start Free Trial" vs "Get Started"
- Ajouter de la clarté sur la durée du trial dans le CTA
- Tester l'emphase de la value proposition dans l'en-tête du formulaire

**Microcopy**
- Labels de champs : minimal vs descriptif
- Optimisation du placeholder text
- Clarté et ton des messages d'erreur
- Affichage des exigences de password (d'emblée vs à l'erreur)

**Éléments de confiance**
- Ajouter de la social proof à côté du formulaire de signup
- Tester des trust badges près du formulaire (sécurité, conformité)
- Ajouter un message "No credit card required"
- Inclure une copy d'assurance de confidentialité

---

### Expériences de trial & d'engagement

**Variations de free trial**
- Carte bancaire requise vs non requise pour le trial
- Tester l'impact de la durée du trial (7 vs 14 vs 30 jours)
- Modèle freemium vs free trial
- Trial à features limitées vs accès complet

**Points de friction**
- Vérification d'email requise vs retardée vs supprimée
- Tester l'impact du CAPTCHA sur la complétion
- Checkbox d'acceptation des terms vs acceptation implicite
- Vérification téléphonique pour les comptes à forte valeur

---

### Expériences post-submit

- Messages clairs sur les prochaines étapes après signup
- Accès instantané au produit vs confirmation par email d'abord
- Message de bienvenue personnalisé basé sur les données de signup
- Auto-login après signup vs login obligatoire

---

## Questions spécifiques à la tâche

1. Quel est votre taux de complétion de signup actuel ?
2. Avez-vous des analytics field-level sur le drop-off ?
3. Quelles données sont absolument requises avant qu'ils puissent utiliser le produit ?
4. Y a-t-il des exigences de conformité ou de vérification ?
5. Que se passe-t-il immédiatement après le signup ?

---

## Skills associés

- **onboarding-cro** : Pour optimiser ce qui se passe après le signup
- **form-cro** : Pour les formulaires non-signup (capture de lead, contact)
- **page-cro** : Pour la landing page qui mène au signup
- **ab-test-setup** : Pour tester les changements du flux de signup
