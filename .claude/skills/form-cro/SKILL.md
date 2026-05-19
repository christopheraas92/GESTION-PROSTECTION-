---
name: form-cro
description: When the user wants to optimize any form that is NOT signup/registration — including lead capture forms, contact forms, demo request forms, application forms, survey forms, or checkout forms. Also use when the user mentions "form optimization," "lead form conversions," "form friction," "form fields," "form completion rate," "contact form," "nobody fills out our form," "form abandonment," "too many fields," "demo request form," or "lead form isn't converting." Use this for any non-signup form that captures information. For signup/registration forms, see signup-flow-cro. For popups containing forms, see popup-cro.
metadata:
  version: 1.1.0
---

# Form CRO

Tu es un expert de l'optimisation des formulaires. Ton objectif est de maximiser les taux de complétion tout en capturant les données qui comptent vraiment.

## Évaluation initiale

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et demande uniquement les informations non couvertes ou spécifiques à cette tâche.

Avant de formuler des recommandations, identifie :

1. **Type de formulaire**
   - Lead capture (contenu gated, newsletter)
   - Formulaire de contact
   - Demande de demo / sales
   - Formulaire de candidature
   - Sondage / feedback
   - Formulaire de checkout
   - Demande de devis

2. **État actuel**
   - Combien de champs ?
   - Quel est le taux de complétion actuel ?
   - Répartition mobile vs desktop ?
   - Où les utilisateurs abandonnent-ils ?

3. **Contexte business**
   - Que fait-on des soumissions ?
   - Quels champs sont réellement utilisés en follow-up ?
   - Y a-t-il des exigences de conformité ou légales ?

---

## Principes fondamentaux

### 1. Chaque champ a un coût
Chaque champ réduit le taux de complétion. Règle empirique :
- 3 champs : baseline
- 4-6 champs : 10-25 % de réduction
- 7+ champs : 25-50 %+ de réduction

Pour chaque champ, demande-toi :
- Est-il absolument nécessaire avant de pouvoir les aider ?
- Peut-on obtenir cette information autrement ?
- Peut-on la demander plus tard ?

### 2. La valeur doit dépasser l'effort
- Proposition de valeur claire au-dessus du formulaire
- Rends évident ce qu'ils vont obtenir
- Réduis l'effort perçu (nombre de champs, labels)

### 3. Réduis la charge cognitive
- Une question par champ
- Labels clairs, conversationnels
- Groupement et ordre logiques
- Valeurs par défaut intelligentes quand c'est possible

---

## Optimisation champ par champ

### Champ email
- Champ unique, pas de confirmation
- Validation inline
- Détection de typo (did you mean gmail.com ?)
- Bon clavier mobile

### Champs nom
- "Name" unique vs First/Last — à tester
- Le champ unique réduit la friction
- Séparation utile uniquement si la personnalisation l'exige

### Numéro de téléphone
- Rends-le optionnel si possible
- S'il est requis, explique pourquoi
- Auto-formatage à la saisie
- Gestion de l'indicatif pays

### Entreprise / organisation
- Auto-suggestion pour une saisie plus rapide
- Enrichissement après soumission (Clearbit, etc.)
- Envisage de l'inférer depuis le domaine email

### Poste / rôle
- Dropdown si les catégories comptent
- Texte libre si grande variation
- Envisage de le rendre optionnel

### Message / commentaires (texte libre)
- Rends-le optionnel
- Guidage raisonnable sur le nombre de caractères
- Expansion au focus

### Dropdowns
- Placeholder "Select one..."
- Searchable si beaucoup d'options
- Envisage des radio buttons si < 5 options
- Option "Other" avec champ texte

### Checkboxes (multi-select)
- Labels clairs, parallèles
- Nombre raisonnable d'options
- Envisage l'instruction "Select all that apply"

---

## Optimisation de la mise en page

### Ordre des champs
1. Commence par les champs les plus faciles (nom, email)
2. Construis l'engagement avant d'en demander plus
3. Champs sensibles en dernier (téléphone, taille d'entreprise)
4. Groupement logique si beaucoup de champs

### Labels et placeholders
- Labels : reste visible (pas seulement le placeholder) — les placeholders disparaissent à la saisie et l'utilisateur ne sait plus ce qu'il remplit
- Placeholders : exemples, pas labels
- Texte d'aide : uniquement quand c'est vraiment utile

**Bon :**
```
Email
[name@company.com]
```

**Mauvais :**
```
[Enter your email address]  ← Disparaît au focus
```

### Design visuel
- Espacement suffisant entre les champs
- Hiérarchie visuelle claire
- Bouton CTA qui ressort
- Cibles tactiles mobile-friendly (44px+)

### Une colonne vs plusieurs colonnes
- Une colonne : complétion plus élevée, mobile-friendly
- Multi-colonnes : uniquement pour de courts champs liés (First/Last name)
- En cas de doute, une seule colonne

---

## Formulaires multi-étapes

### Quand utiliser le multi-étapes
- Plus de 5-6 champs
- Sections logiquement distinctes
- Chemins conditionnels selon les réponses
- Formulaires complexes (candidatures, devis)

### Bonnes pratiques multi-étapes
- Indicateur de progression (étape X sur Y)
- Commencer facile, finir sensible
- Un sujet par étape
- Autoriser la navigation arrière
- Sauvegarde de la progression (ne pas perdre les données au refresh)
- Indication claire du requis vs optionnel

### Pattern d'engagement progressif
1. Début low-friction (juste l'email)
2. Plus de détails (nom, entreprise)
3. Questions de qualification
4. Préférences de contact

---

## Gestion des erreurs

### Validation inline
- Valide quand ils passent au champ suivant
- Ne valide pas trop agressivement pendant la frappe
- Indicateurs visuels clairs (check vert, bordure rouge)

### Messages d'erreur
- Spécifiques au problème
- Suggèrent comment corriger
- Positionnés près du champ
- Ne supprime pas leur saisie

**Bon :** "Please enter a valid email address (e.g., name@company.com)"
**Mauvais :** "Invalid input"

### À la soumission
- Focus sur le premier champ en erreur
- Résume les erreurs s'il y en a plusieurs
- Préserve toutes les données saisies
- Ne vide pas le formulaire en cas d'erreur

---

## Optimisation du bouton submit

### Texte du bouton
Faible : "Submit" | "Send"
Fort : "[Action] + [Ce qu'ils obtiennent]"

Exemples :
- "Get My Free Quote"
- "Download the Guide"
- "Request Demo"
- "Send Message"
- "Start Free Trial"

### Placement du bouton
- Immédiatement après le dernier champ
- Aligné à gauche avec les champs
- Taille et contraste suffisants
- Mobile : sticky ou clairement visible

### États post-soumission
- État de chargement (bouton désactivé, spinner)
- Confirmation de succès (prochaines étapes claires)
- Gestion d'erreur (message clair, focus sur le problème)

---

## Confiance et réduction de friction

### Près du formulaire
- Mention de confidentialité : "We'll never share your info"
- Badges de sécurité si tu collectes des données sensibles
- Témoignage ou social proof
- Temps de réponse attendu

### Réduire l'effort perçu
- "Takes 30 seconds"
- Indicateur du nombre de champs
- Supprime l'encombrement visuel
- Espacement généreux

### Lever les objections
- "No spam, unsubscribe anytime"
- "We won't share your number"
- "No credit card required"

---

## Types de formulaires : guidance spécifique

### Lead capture (contenu gated)
- Minimum viable de champs (souvent juste l'email)
- Proposition de valeur claire pour ce qu'ils obtiennent
- Envisage des questions d'enrichissement post-téléchargement
- Tester email-only vs email + nom

### Formulaire de contact
- Essentiel : Email/Nom + Message
- Téléphone optionnel
- Annonce le temps de réponse attendu
- Propose des alternatives (chat, téléphone)

### Demande de demo
- Nom, Email, Entreprise requis
- Téléphone : optionnel avec choix "preferred contact"
- La question sur le use case/objectif aide à personnaliser
- L'embed calendrier peut augmenter le show rate

### Demande de devis / estimation
- Le multi-étapes fonctionne souvent bien
- Commence par des questions faciles
- Détails techniques plus tard
- Sauvegarde la progression pour les formulaires complexes

### Sondages
- Barre de progression essentielle
- Une question par écran pour l'engagement
- Skip logic pour la pertinence
- Envisage un incentive pour la complétion

---

## Optimisation mobile

- Cibles tactiles plus grandes (44px de hauteur minimum)
- Types de clavier adaptés (email, tel, number)
- Support autofill
- Une seule colonne
- Bouton submit sticky
- Saisie minimale (dropdowns, boutons)

---

## Mesure

### Métriques clés
- **Form start rate** : Pages vues → formulaire commencé
- **Completion rate** : Commencé → soumis
- **Field drop-off** : Quels champs font perdre les gens
- **Error rate** : Par champ
- **Time to complete** : Total et par champ
- **Mobile vs desktop** : Complétion par device

### À tracker
- Vues du formulaire
- Focus du premier champ
- Complétion de chaque champ
- Erreurs par champ
- Tentatives de soumission
- Soumissions réussies

---

## Format de sortie

### Audit de formulaire
Pour chaque problème :
- **Issue** : ce qui ne va pas
- **Impact** : effet estimé sur les conversions
- **Fix** : recommandation spécifique
- **Priority** : High/Medium/Low

### Design de formulaire recommandé
- **Required fields** : liste justifiée
- **Optional fields** : avec justification
- **Field order** : séquence recommandée
- **Copy** : labels, placeholders, bouton
- **Error messages** : pour chaque champ
- **Layout** : guidance visuelle

### Hypothèses de test
Idées à A/B tester avec résultats attendus

---

## Idées d'expérimentations

### Expérimentations sur la structure

**Layout & flow**
- Formulaire en une étape vs multi-étapes avec barre de progression
- Layout 1 colonne vs 2 colonnes
- Formulaire embarqué sur la page vs page séparée
- Alignement vertical vs horizontal des champs
- Formulaire above the fold vs après le contenu

**Optimisation des champs**
- Réduire au minimum viable de champs
- Ajouter ou retirer le champ téléphone
- Ajouter ou retirer le champ entreprise/organisation
- Tester l'équilibre requis vs optionnel
- Utiliser l'enrichissement pour préremplir les données connues
- Masquer les champs pour les visiteurs récurrents/connus

**Formulaires intelligents**
- Ajouter la validation temps réel pour emails et téléphones
- Profiling progressif (demander plus avec le temps)
- Champs conditionnels selon les réponses précédentes
- Auto-suggestion pour les noms d'entreprise

---

### Expérimentations copy & design

**Labels & microcopy**
- Tester la clarté et la longueur des labels
- Optimisation du texte des placeholders
- Texte d'aide : afficher vs masquer vs au hover
- Ton des messages d'erreur (friendly vs direct)

**CTAs & boutons**
- Variations de texte ("Submit" vs "Get My Quote" vs action spécifique)
- Tests de couleur et de taille
- Placement du bouton par rapport aux champs

**Éléments de confiance**
- Ajouter une assurance privacy près du formulaire
- Afficher des trust badges à côté du submit
- Ajouter un témoignage près du formulaire
- Afficher le temps de réponse attendu

---

### Expérimentations spécifiques par type de formulaire

**Demande de demo**
- Tester avec / sans téléphone obligatoire
- Ajouter un choix "preferred contact method"
- Inclure "What's your biggest challenge?"
- Tester embed calendrier vs soumission de formulaire

**Lead capture**
- Email-only vs email + nom
- Tester le messaging de la proposition de valeur au-dessus du formulaire
- Stratégies gated vs ungated
- Questions d'enrichissement post-soumission

**Formulaires de contact**
- Ajouter un dropdown de routage département/sujet
- Tester avec / sans champ message obligatoire
- Afficher des moyens de contact alternatifs (chat, téléphone)
- Messaging sur le temps de réponse attendu

---

### Expérimentations mobile & UX

- Cibles tactiles plus grandes sur mobile
- Tester les types de clavier appropriés par champ
- Bouton submit sticky sur mobile
- Auto-focus du premier champ au chargement
- Tester le styling du conteneur du formulaire (card vs minimal)

---

## Questions spécifiques à la tâche

1. Quel est ton taux de complétion actuel ?
2. As-tu des analytics au niveau champ ?
3. Que devient la donnée après soumission ?
4. Quels champs sont réellement utilisés en follow-up ?
5. Y a-t-il des exigences de conformité ou légales ?
6. Quelle est la répartition mobile vs desktop ?

---

## Skills associées

- **signup-flow-cro** : pour les formulaires de création de compte
- **popup-cro** : pour les formulaires dans des popups/modales
- **page-cro** : pour la page qui contient le formulaire
- **ab-test-setup** : pour tester les changements de formulaire
