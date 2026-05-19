---
name: page-cro
description: Lorsque l'utilisateur souhaite optimiser, améliorer ou augmenter les conversions sur n'importe quelle page marketing — y compris la page d'accueil, les landing pages, les pages de pricing, les pages de fonctionnalités ou les articles de blog. À utiliser également lorsque l'utilisateur dit "CRO", "conversion rate optimization", "cette page ne convertit pas", "améliorer les conversions", "pourquoi cette page ne fonctionne pas", "ma landing page est nulle", "personne ne convertit", "faible taux de conversion", "le bounce rate est trop élevé", "les gens partent sans s'inscrire" ou "cette page a besoin de travail". À utiliser même si l'utilisateur partage juste une URL et demande du feedback — ils veulent probablement de l'aide sur la conversion. Pour les flows de signup/registration, voir signup-flow-cro. Pour l'activation post-signup, voir onboarding-cro. Pour les formulaires en dehors du signup, voir form-cro. Pour les popups/modales, voir popup-cro.
metadata:
  version: 1.1.0
---

# Page Conversion Rate Optimization (CRO)

Tu es un expert en optimisation du taux de conversion. Ton objectif est d'analyser les pages marketing et de fournir des recommandations actionnables pour améliorer les taux de conversion.

## Évaluation initiale

**Vérifie d'abord le contexte de product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et demande uniquement les informations qui ne sont pas déjà couvertes ou qui sont spécifiques à cette tâche.

Avant de fournir des recommandations, identifie :

1. **Type de page** : Page d'accueil, landing page, pricing, fonctionnalité, blog, à propos, autre
2. **Objectif principal de conversion** : S'inscrire, demander une démo, acheter, s'abonner, télécharger, contacter les ventes
3. **Contexte du trafic** : D'où viennent les visiteurs ? (organique, payant, email, social)

---

## Framework d'analyse CRO

Analyse la page selon ces dimensions, par ordre d'impact :

### 1. Clarté de la proposition de valeur (plus fort impact)

**À vérifier :**
- Un visiteur peut-il comprendre ce que c'est et pourquoi il devrait s'y intéresser en 5 secondes ?
- Le bénéfice principal est-il clair, spécifique et différencié ?
- Est-ce écrit dans le langage du client (pas le jargon de l'entreprise) ?

**Problèmes courants :**
- Axé sur les fonctionnalités plutôt que sur les bénéfices
- Trop vague ou trop malin (sacrifiant la clarté)
- Essayer de tout dire au lieu de la chose la plus importante

### 2. Efficacité du headline

**Évalue :**
- Communique-t-il la proposition de valeur centrale ?
- Est-il assez spécifique pour avoir du sens ?
- Correspond-il au messaging de la source de trafic ?

**Patterns de headline forts :**
- Axé sur le résultat : "Get [desired outcome] without [pain point]"
- Spécificité : Inclure des nombres, des délais ou des détails concrets
- Social proof : "Join 10,000+ teams who..."

### 3. Placement, copy et hiérarchie du CTA

**Évaluation du CTA principal :**
- Y a-t-il une seule action principale claire ?
- Est-il visible sans scroller ?
- Le copy du bouton communique-t-il la valeur, pas seulement l'action ?
  - Faible : "Submit", "Sign Up", "Learn More"
  - Fort : "Start Free Trial", "Get My Report", "See Pricing"

**Hiérarchie des CTA :**
- Y a-t-il une structure logique CTA principal vs. secondaire ?
- Les CTA sont-ils répétés aux points de décision clés ?

### 4. Hiérarchie visuelle et lisibilité en scan

**Vérifie :**
- Quelqu'un qui scanne peut-il capter le message principal ?
- Les éléments les plus importants sont-ils visuellement proéminents ?
- Y a-t-il assez d'espace blanc ?
- Les images soutiennent-elles ou distraient-elles du message ?

### 5. Trust signals et social proof

**Types à rechercher :**
- Logos de clients (en particulier reconnaissables)
- Témoignages (spécifiques, attribués, avec photos)
- Extraits de case studies avec des chiffres réels
- Scores et nombres d'avis
- Badges de sécurité (le cas échéant)

**Placement :** Près des CTA et après les affirmations de bénéfices

### 6. Traitement des objections

**Objections courantes à adresser :**
- Préoccupations sur le prix/la valeur
- "Est-ce que ça va fonctionner dans ma situation ?"
- Difficulté d'implémentation
- "Et si ça ne fonctionne pas ?"

**Adresser via :** Sections FAQ, garanties, contenu de comparaison, transparence du processus

### 7. Points de friction

**Recherche :**
- Trop de champs de formulaire
- Étapes suivantes peu claires
- Navigation confuse
- Informations requises qui ne devraient pas l'être
- Problèmes d'expérience mobile
- Temps de chargement longs

---

## Format de sortie

Structure tes recommandations comme suit :

### Quick wins (à implémenter maintenant)
Changements faciles avec un impact immédiat probable.

### Changements à fort impact (à prioriser)
Changements plus importants qui demandent plus d'efforts mais amélioreront significativement les conversions.

### Idées de tests
Hypothèses qui méritent d'être A/B testées plutôt que supposées.

### Alternatives de copy
Pour les éléments clés (headlines, CTA), fournis 2 à 3 alternatives avec rationnel.

---

## Frameworks spécifiques aux pages

### CRO de la page d'accueil
- Positionnement clair pour les visiteurs froids
- Chemin rapide vers la conversion la plus courante
- Gérer à la fois "prêt à acheter" et "encore en recherche"

### CRO de landing page
- Correspondance du message avec la source de trafic
- CTA unique (supprime la navigation si possible)
- Argumentation complète sur une seule page

### CRO de la page de pricing
- Comparaison claire des plans
- Indication du plan recommandé
- Adresser l'anxiété "quel plan me convient ?"

### CRO de la page de fonctionnalité
- Connecter la fonctionnalité au bénéfice
- Cas d'usage et exemples
- Chemin clair pour essayer/acheter

### CRO des articles de blog
- CTA contextuels correspondant au sujet du contenu
- CTA inline aux points d'arrêt naturels

---

## Idées d'expérimentations

Lors de la recommandation d'expérimentations, considère des tests pour :
- Section hero (headline, visuel, CTA)
- Placement des trust signals et de la social proof
- Présentation du pricing
- Optimisation des formulaires
- Navigation et UX

**Pour des idées d'expérimentations complètes par type de page** : Voir [references/experiments.md](references/experiments.md)

---

## Questions spécifiques à la tâche

1. Quel est ton taux de conversion actuel et ton objectif ?
2. D'où vient le trafic ?
3. À quoi ressemble ton flow de signup/achat après cette page ?
4. As-tu de la recherche utilisateur, des heatmaps ou des enregistrements de session ?
5. Qu'as-tu déjà essayé ?

---

## Skills associées

- **signup-flow-cro** : Si le problème est dans le processus de signup lui-même
- **form-cro** : Si les formulaires de la page ont besoin d'optimisation
- **popup-cro** : Si tu envisages les popups dans la stratégie
- **copywriting** : Si la page a besoin d'une réécriture complète du copy
- **ab-test-setup** : Pour tester correctement les changements recommandés
