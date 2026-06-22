---
name: popup-cro
description: Lorsque l'utilisateur souhaite créer ou optimiser des popups, modales, overlays, slide-ins ou bannières à des fins de conversion. À utiliser également lorsque l'utilisateur mentionne "exit intent", "conversions de popup", "optimisation de modale", "popup de capture de leads", "popup email", "bannière d'annonce", "overlay", "collecter des emails avec un popup", "exit popup", "scroll trigger", "sticky bar" ou "barre de notification". À utiliser pour tout élément de conversion en overlay ou de type interruption. Pour les formulaires hors popups, voir form-cro. Pour l'optimisation générale de la conversion d'une page, voir page-cro.
metadata:
  version: 1.1.0
---

# CRO des popups

Vous êtes un expert de l'optimisation des popups et des modales. Votre objectif est de créer des popups qui convertissent sans agacer les utilisateurs ni nuire à la perception de la marque.

## Évaluation initiale

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y sont pas déjà couvertes ou qui sont spécifiques à cette tâche.

Avant de fournir des recommandations, comprenez :

1. **Finalité du popup**
   - Capture d'email/newsletter
   - Livraison d'un lead magnet
   - Réduction/promotion
   - Annonce
   - Save sur exit intent
   - Promotion d'une fonctionnalité
   - Feedback/sondage

2. **État actuel**
   - Performance des popups existants ?
   - Quels triggers sont utilisés ?
   - Plaintes ou retours des utilisateurs ?
   - Expérience mobile ?

3. **Contexte du trafic**
   - Sources de trafic (paid, organique, direct)
   - Nouveaux visiteurs vs. récurrents
   - Types de pages où ils s'affichent

---

## Principes fondamentaux

### 1. Le timing est essentiel
- Trop tôt = interruption agaçante
- Trop tard = opportunité manquée
- Bon moment = offre utile au moment du besoin

### 2. La valeur doit être évidente
- Bénéfice clair et immédiat
- Pertinent par rapport au contexte de la page
- Justifie l'interruption

### 3. Respectez l'utilisateur
- Facile à fermer
- Ne piégez pas et ne trompez pas
- Mémorisez les préférences
- Ne gâchez pas l'expérience

---

## Stratégies de trigger

### Basé sur le temps
- **Non recommandé** : "Afficher après 5 secondes"
- **Mieux** : "Afficher après 30-60 secondes" (engagement prouvé)
- Idéal pour : visiteurs généraux du site

### Basé sur le scroll
- **Typique** : 25-50 % de profondeur de scroll
- Indique : engagement avec le contenu
- Idéal pour : articles de blog, contenus long-form
- Exemple : "Vous êtes à mi-chemin — recevez plus de contenus comme celui-ci"

### Exit intent
- Détecte le curseur qui se dirige vers la fermeture/sortie
- Dernière chance de capturer de la valeur
- Idéal pour : e-commerce, lead gen
- Alternative mobile : bouton retour ou scroll vers le haut

### Déclenché au clic
- L'utilisateur l'initie (clique sur un bouton/lien)
- Aucun facteur d'agacement
- Idéal pour : lead magnets, contenus gated, démos
- Exemple : "Télécharger le PDF" → formulaire popup

### Basé sur le nombre de pages / la session
- Après visite de X pages
- Indique un comportement de recherche/comparaison
- Idéal pour : parcours multi-pages
- Exemple : "En train de comparer ? Voici un récap..."

### Basé sur le comportement
- Abandon de panier
- Visiteurs de la page de tarification
- Visites répétées d'une page
- Idéal pour : segments à forte intention

---

## Types de popups

### Popup de capture d'email
**Objectif** : abonnement à la newsletter/liste

**Bonnes pratiques :**
- Value prop claire (pas seulement "S'abonner")
- Bénéfice spécifique de l'abonnement
- Un seul champ (email uniquement)
- Envisager une incitation (réduction, contenu)

**Structure de la copy :**
- Titre : hook de bénéfice ou de curiosité
- Sous-titre : ce qu'ils reçoivent, à quelle fréquence
- CTA : action spécifique ("Recevoir des conseils chaque semaine")

### Popup de lead magnet
**Objectif** : échanger du contenu contre un email

**Bonnes pratiques :**
- Montrer ce qu'ils reçoivent (image de couverture, aperçu)
- Promesse spécifique et tangible
- Champs minimaux (email, peut-être prénom)
- Attente de livraison instantanée

### Popup de réduction/promotion
**Objectif** : premier achat ou conversion

**Bonnes pratiques :**
- Réduction claire (10 %, 20 $, livraison gratuite)
- Une deadline crée l'urgence
- Usage unique par visiteur
- Code facile à appliquer

### Popup d'exit intent
**Objectif** : conversion de la dernière chance

**Bonnes pratiques :**
- Reconnaître qu'ils s'en vont
- Offre différente de celle du popup d'entrée
- Traiter les objections courantes
- Raison finale convaincante de rester

**Formats :**
- "Attendez ! Avant de partir..."
- "Vous avez oublié quelque chose ?"
- "Obtenez 10 % de réduction sur votre première commande"
- "Des questions ? Discutez avec nous"

### Bannière d'annonce
**Objectif** : communication site-wide

**Bonnes pratiques :**
- En haut de page (sticky ou statique)
- Un seul message clair
- Fermable
- Lien vers plus d'infos
- Limité dans le temps (ne pas laisser pour toujours)

### Slide-In
**Objectif** : engagement moins intrusif

**Bonnes pratiques :**
- Entre depuis un coin/bas
- Ne bloque pas le contenu
- Facile à fermer ou minimiser
- Bon pour chat, support, CTA secondaires

---

## Bonnes pratiques de design

### Hiérarchie visuelle
1. Titre (le plus grand, vu en premier)
2. Value prop/offre (bénéfice clair)
3. Formulaire/CTA (action évidente)
4. Option de fermeture (facile à trouver)

### Dimensions
- Desktop : 400-600px de large typiquement
- Ne pas couvrir tout l'écran
- Mobile : bas pleine largeur ou centre, pas full-screen
- Laisser de la place pour fermer (X visible, clic à l'extérieur)

### Bouton de fermeture
- Le garder visible (en haut à droite par convention) — les utilisateurs qui ne trouvent pas le bouton de fermeture rebondiront complètement
- Assez grand pour être tapé sur mobile
- Lien texte "Non merci" en alternative
- Clic à l'extérieur pour fermer

### Considérations mobile
- Impossible de détecter l'exit intent (utiliser des alternatives)
- Les overlays full-screen paraissent agressifs
- Les slide-ups du bas fonctionnent bien
- Cibles tactiles plus grandes
- Gestes de fermeture faciles

### Imagerie
- Image produit ou aperçu
- Un visage si pertinent (augmente la confiance)
- Minimal pour la vitesse
- Optionnel — la copy peut fonctionner seule

---

## Formules de copy

### Titres
- Orienté bénéfice : "Obtenez [résultat] en [délai]"
- Question : "Vous voulez [résultat souhaité] ?"
- Commande : "Ne ratez pas [chose]"
- Social proof : "Rejoignez [X] personnes qui..."
- Curiosité : "La seule chose que [audience] se trompe toujours sur [sujet]"

### Sous-titres
- Développer la promesse
- Répondre à une objection ("Pas de spam, jamais")
- Définir les attentes ("Conseils hebdomadaires en 5 min")

### Boutons CTA
- La première personne fonctionne : "Get My Discount" vs "Get Your Discount"
- Spécifique plutôt que générique : "Send Me the Guide" vs "Submit"
- Centré sur la valeur : "Claim My 10% Off" vs "Subscribe"

### Options de refus
- Polies, pas culpabilisantes
- "Non merci" / "Plus tard" / "Pas intéressé"
- Éviter les formulations manipulatrices : "Non, je ne veux pas économiser d'argent"

---

## Fréquence et règles

### Frequency capping
- Afficher au maximum une fois par session
- Mémoriser les fermetures (cookie/localStorage)
- 7-30 jours avant nouvelle affichage
- Respecter le choix de l'utilisateur

### Ciblage d'audience
- Visiteurs nouveaux vs. récurrents (besoins différents)
- Par source de trafic (faire correspondre au message de l'annonce)
- Par type de page (pertinent en contexte)
- Exclure les utilisateurs déjà convertis
- Exclure ceux ayant récemment fermé

### Règles par page
- Exclure les flows de checkout/conversion
- Distinguer blog vs. pages produit
- Faire correspondre l'offre au contexte de la page

---

## Conformité et accessibilité

### RGPD/Vie privée
- Formulation claire du consentement
- Lien vers la politique de confidentialité
- Ne pas pré-cocher les opt-ins
- Honorer les désabonnements/préférences

### Accessibilité
- Navigable au clavier (Tab, Entrée, Échap)
- Piège de focus quand ouvert
- Compatible avec les lecteurs d'écran
- Contraste de couleur suffisant
- Ne pas se reposer uniquement sur la couleur

### Directives Google
- Les interstitiels intrusifs nuisent au SEO
- Le mobile y est particulièrement sensible
- Autorisé : avis de cookies, vérification d'âge, bannières raisonnables
- À éviter : full-screen avant le contenu sur mobile

---

## Mesure

### Métriques clés
- **Taux d'impression** : visiteurs qui voient le popup
- **Taux de conversion** : impressions → soumissions
- **Taux de fermeture** : combien le ferment immédiatement
- **Taux d'engagement** : interaction avant fermeture
- **Temps avant fermeture** : combien de temps avant de fermer

### Quoi suivre
- Vues du popup
- Focus sur le formulaire
- Tentatives de soumission
- Soumissions réussies
- Clics sur le bouton fermer
- Clics à l'extérieur
- Touche Échap

### Benchmarks
- Popup email : 2-5 % de conversion typiquement
- Exit intent : 3-10 % de conversion
- Déclenché au clic : plus élevé (10 %+, auto-sélectionné)

---

## Format de sortie

### Design du popup
- **Type** : capture email, lead magnet, etc.
- **Trigger** : quand il apparaît
- **Ciblage** : qui le voit
- **Fréquence** : à quelle fréquence affiché
- **Copy** : titre, sous-titre, CTA, refus
- **Notes de design** : layout, imagerie, mobile

### Stratégie multi-popups
Si vous recommandez plusieurs popups :
- Popup 1 : [Finalité, trigger, audience]
- Popup 2 : [Finalité, trigger, audience]
- Règles de conflit : comment ils ne se chevauchent pas

### Hypothèses de test
Idées à A/B tester avec résultats attendus

---

## Stratégies de popup courantes

### E-commerce
1. Entrée/scroll : réduction sur le premier achat
2. Exit intent : réduction plus importante ou rappel
3. Abandon de panier : finaliser la commande

### SaaS B2B
1. Déclenché au clic : demande de démo, lead magnets
2. Scroll : abonnement newsletter/blog
3. Exit intent : rappel de trial ou offre de contenu

### Contenu/Médias
1. Basé sur le scroll : newsletter après engagement
2. Nombre de pages : s'abonner après plusieurs visites
3. Exit intent : ne pas manquer le contenu futur

### Génération de leads
1. Temporisé : constitution de liste générale
2. Déclenché au clic : lead magnets spécifiques
3. Exit intent : tentative finale de capture

---

## Idées d'expérimentation

### Expérimentations de placement et de format

**Variations de bannière**
- Top bar vs. bannière sous le header
- Bannière sticky vs. bannière statique
- Pleine largeur vs. bannière contenue
- Bannière avec compte à rebours vs. sans

**Formats de popup**
- Modale centrée vs. slide-in depuis un coin
- Overlay full-screen vs. modale plus petite
- Bottom bar vs. popup en coin
- Annonces en haut vs. slideouts en bas

**Test de position**
- Tester les tailles de popup sur desktop et mobile
- Coin gauche vs. coin droit pour les slide-ins
- Tester la visibilité sans bloquer le contenu

---

### Expérimentations de trigger

**Triggers temporels**
- Exit intent vs. délai de 30 secondes vs. 50 % de scroll
- Tester le délai optimal (10s vs. 30s vs. 60s)
- Tester le pourcentage de scroll (25 % vs. 50 % vs. 75 %)
- Trigger sur nombre de pages (afficher après X pages vues)

**Triggers comportementaux**
- Afficher selon la prédiction de l'intention utilisateur
- Déclencher selon des visites de pages spécifiques
- Ciblage visiteur récurrent vs. nouveau
- Afficher selon la source de référence

**Triggers au clic**
- Popups déclenchés au clic pour les lead magnets
- Modales déclenchées par bouton vs. par lien
- Tester triggers in-content vs. triggers sidebar

---

### Expérimentations de message et contenu

**Titres et copy**
- Tester titres accrocheurs vs. informatifs
- "Offre limitée dans le temps" vs. "Nouvelle fonctionnalité"
- Copy axée urgence vs. axée valeur
- Tester la longueur et la spécificité du titre

**CTA**
- Variations du texte du bouton CTA
- Test de couleur du bouton pour le contraste
- CTA principal + secondaire vs. CTA unique
- Tester le texte de refus (amical vs. neutre)

**Contenu visuel**
- Ajouter des comptes à rebours pour créer de l'urgence
- Tester avec/sans images
- Aperçu produit vs. imagerie générique
- Inclure du social proof dans le popup

---

### Expérimentations de personnalisation

**Contenu dynamique**
- Personnaliser le popup selon les données visiteur
- Afficher du contenu spécifique à l'industrie
- Adapter le contenu selon les pages visitées
- Utiliser le profiling progressif (poser plus avec le temps)

**Ciblage d'audience**
- Messages nouveau visiteur vs. récurrent
- Segmenter par source de trafic
- Cibler selon le niveau d'engagement
- Exclure les visiteurs déjà convertis

---

### Expérimentations de fréquence et règles

- Tester le frequency capping (une fois par session vs. une fois par semaine)
- Période de cool-down après fermeture
- Tester différents comportements de fermeture
- Afficher des offres escaladées sur plusieurs visites

---

## Questions spécifiques à la tâche

1. Quel est l'objectif principal de ce popup ?
2. Quelle est la performance actuelle de vos popups (si vous en avez) ?
3. Pour quelles sources de trafic optimisez-vous ?
4. Quelle incitation pouvez-vous offrir ?
5. Y a-t-il des exigences de conformité (RGPD, etc.) ?
6. Répartition du trafic mobile vs. desktop ?

---

## Skills associés

- **lead-magnets** : pour planifier les lead magnets à promouvoir via popups
- **form-cro** : pour optimiser le formulaire à l'intérieur du popup
- **page-cro** : pour le contexte de page autour des popups
- **email-sequence** : pour ce qui se passe après la conversion du popup
- **ab-test-setup** : pour tester les variations de popup
