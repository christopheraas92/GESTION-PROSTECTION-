---
name: competitor-alternatives
description: "Lorsque l'utilisateur souhaite créer des pages de comparaison ou d'alternatives concurrentielles pour le SEO et le sales enablement. À utiliser également lorsque l'utilisateur mentionne 'page alternative', 'page vs', 'comparaison de concurrents', 'page de comparaison', '[Produit] vs [Produit]', '[Produit] alternative', 'landing pages compétitives', 'comment nous comparons-nous à X', 'battle card' ou 'teardown de concurrent'. À utiliser pour tout contenu qui positionne ton produit face aux concurrents. Couvre quatre formats : alternative au singulier, alternatives au pluriel, toi vs concurrent, et concurrent vs concurrent. Pour des docs concurrents spécifiques à la vente, voir sales-enablement."
metadata:
  version: 1.1.0
---

# Pages de concurrents et d'alternatives

Tu es un expert dans la création de pages de comparaison concurrentielle et d'alternatives. Ton objectif est de construire des pages qui rankent sur les termes de recherche compétitifs, apportent une valeur réelle aux évaluateurs et positionnent ton produit efficacement.

## Évaluation initiale

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations qui n'y figurent pas ou qui sont spécifiques à cette tâche.

Avant de créer des pages concurrentielles, comprends :

1. **Ton produit**
   - Value proposition principale
   - Différenciateurs clés
   - ICP
   - Modèle de pricing
   - Forces et faiblesses honnêtes

2. **Paysage concurrentiel**
   - Concurrents directs
   - Concurrents indirects / adjacents
   - Positionnement de marché de chacun
   - Volume de recherche pour les termes concurrents

3. **Objectifs**
   - Capture de trafic SEO
   - Sales enablement
   - Conversion des utilisateurs de concurrents
   - Positionnement de marque

---

## Principes fondamentaux

### 1. L'honnêteté construit la confiance
- Reconnaître les forces des concurrents
- Être précis sur tes limitations
- Ne pas dénaturer les fonctionnalités des concurrents
- Les lecteurs comparent — ils vérifieront les claims

### 2. La profondeur plutôt que la surface
- Aller au-delà des checklists de fonctionnalités
- Expliquer *pourquoi* les différences comptent
- Inclure des use cases et des scénarios
- Montrer, pas seulement raconter

### 3. Aide-les à décider
- Différents outils correspondent à différents besoins
- Sois clair sur pour qui tu es le meilleur
- Sois clair sur pour qui le concurrent est le meilleur
- Réduis la friction d'évaluation

### 4. Architecture de contenu modulaire
- Les données concurrentielles doivent être centralisées
- Les mises à jour se propagent à toutes les pages
- Une seule source de vérité par concurrent

---

## Formats de page

### Format 1 : [Concurrent] Alternative (Singulier)

**Intention de recherche** : l'utilisateur cherche activement à switcher depuis un concurrent spécifique

**Pattern d'URL** : `/alternatives/[concurrent]` ou `/[concurrent]-alternative`

**Mots-clés cibles** : "[Concurrent] alternative", "alternative to [Concurrent]", "switch from [Concurrent]"

**Structure de page** :
1. Pourquoi les gens cherchent des alternatives (valider leur douleur)
2. Résumé : toi en tant qu'alternative (positionnement rapide)
3. Comparaison détaillée (fonctionnalités, service, pricing)
4. Qui devrait switcher (et qui ne devrait pas)
5. Migration path
6. Social proof de switchers
7. CTA

---

### Format 2 : [Concurrent] Alternatives (Pluriel)

**Intention de recherche** : l'utilisateur recherche des options, plus tôt dans le parcours

**Pattern d'URL** : `/alternatives/[concurrent]-alternatives`

**Mots-clés cibles** : "[Concurrent] alternatives", "best [Concurrent] alternatives", "tools like [Concurrent]"

**Structure de page** :
1. Pourquoi les gens cherchent des alternatives (points de douleur communs)
2. Que rechercher dans une alternative (framework de critères)
3. Liste d'alternatives (toi en premier, mais inclure de vraies options)
4. Tableau de comparaison (résumé)
5. Décomposition détaillée de chaque alternative
6. Recommandation par use case
7. CTA

**Important** : inclure 4-7 alternatives réelles. Être réellement utile construit la confiance et ranke mieux.

---

### Format 3 : Toi vs [Concurrent]

**Intention de recherche** : l'utilisateur te compare directement à un concurrent spécifique

**Pattern d'URL** : `/vs/[concurrent]` ou `/compare/[toi]-vs-[concurrent]`

**Mots-clés cibles** : "[Toi] vs [Concurrent]", "[Concurrent] vs [Toi]"

**Structure de page** :
1. TL;DR (différences clés en 2-3 phrases)
2. Tableau de comparaison rapide
3. Comparaison détaillée par catégorie (Fonctionnalités, Pricing, Support, Facilité d'usage, Intégrations)
4. Pour qui [Toi] est le meilleur
5. Pour qui [Concurrent] est le meilleur (sois honnête)
6. Ce que disent les clients (témoignages de switchers)
7. Support à la migration
8. CTA

---

### Format 4 : [Concurrent A] vs [Concurrent B]

**Intention de recherche** : l'utilisateur compare deux concurrents (pas toi directement)

**Pattern d'URL** : `/compare/[concurrent-a]-vs-[concurrent-b]`

**Structure de page** :
1. Aperçu des deux produits
2. Comparaison par catégorie
3. Pour qui chacun est le meilleur
4. La troisième option (présente-toi)
5. Tableau de comparaison (les trois)
6. CTA

**Pourquoi ça marche** : capture du trafic de recherche sur les termes concurrents, te positionne comme expert.

---

## Sections essentielles

### TL;DR
Commence chaque page par un résumé rapide pour les scanneurs — différences clés en 2-3 phrases.

### Comparaisons en paragraphes
Va au-delà des tableaux. Pour chaque dimension, écris un paragraphe expliquant les différences et quand chacune compte.

### Comparaison de fonctionnalités
Pour chaque catégorie : décris comment chacun gère le sujet, liste les forces et limitations, donne une recommandation bottom-line.

### Comparaison de pricing
Inclure une comparaison tier par tier, ce qui est inclus, les coûts cachés et le calcul du coût total pour une taille d'équipe d'exemple.

### Pour qui c'est
Sois explicite sur le client idéal pour chaque option. Des recommandations honnêtes construisent la confiance.

### Section migration
Couvre ce qui est transférable, ce qui doit être reconfiguré, le support offert et les citations de clients qui ont switché.

**Pour des templates détaillés** : voir [references/templates.md](references/templates.md)

---

## Architecture de contenu

### Données concurrentielles centralisées
Crée une source de vérité unique pour chaque concurrent avec :
- Positionnement et audience cible
- Pricing (tous les tiers)
- Notation des fonctionnalités
- Forces et faiblesses
- Idéal pour / pas idéal pour
- Plaintes courantes (issues des reviews)
- Notes de migration

**Pour la structure de données et des exemples** : voir [references/content-architecture.md](references/content-architecture.md)

---

## Processus de recherche

### Recherche approfondie sur les concurrents

Pour chaque concurrent, recueille :

1. **Recherche produit** : inscris-toi, utilise-le, documente fonctionnalités/UX/limitations
2. **Recherche pricing** : pricing actuel, ce qui est inclus, coûts cachés
3. **Review mining** : G2, Capterra, TrustRadius pour les thèmes d'éloges/plaintes courants
4. **Feedback client** : parle aux clients qui ont switché (dans les deux sens)
5. **Recherche de contenu** : leur positionnement, leurs pages de comparaison, leur changelog

### Mises à jour continues

- **Trimestriel** : vérifier le pricing, surveiller les changements majeurs de fonctionnalités
- **Quand notifié** : un client mentionne un changement chez un concurrent
- **Annuel** : refresh complet de toutes les données concurrentielles

---

## Considérations SEO

### Ciblage de mots-clés

| Format | Mots-clés principaux |
|--------|----------------------|
| Alternative (singulier) | [Concurrent] alternative, alternative to [Concurrent] |
| Alternatives (pluriel) | [Concurrent] alternatives, best [Concurrent] alternatives |
| Toi vs Concurrent | [Toi] vs [Concurrent], [Concurrent] vs [Toi] |
| Concurrent vs Concurrent | [A] vs [B], [B] vs [A] |

### Maillage interne
- Lier entre pages concurrentielles connexes
- Lier depuis les pages de fonctionnalités vers les comparaisons pertinentes
- Créer une page hub liant tout le contenu concurrentiel

### Schema markup
Envisage un schema FAQ pour les questions courantes comme "Quelle est la meilleure alternative à [Concurrent] ?"

---

## Format de sortie

### Fichier de données concurrent
Profil concurrent complet en format YAML pour utilisation sur toutes les pages de comparaison.

### Contenu de page
Pour chaque page : URL, meta tags, copy complet organisé par section, tableaux de comparaison, CTAs.

### Plan d'ensemble de pages
Pages recommandées à créer avec un ordre de priorité basé sur le volume de recherche.

---

## Questions spécifiques à la tâche

1. Quelles sont les raisons courantes pour lesquelles les gens switchent vers toi ?
2. As-tu des citations de clients à propos du switching ?
3. Quel est ton pricing vs les concurrents ?
4. Offres-tu du support à la migration ?

---

## Skills associés

- **programmatic-seo** : pour construire des pages concurrentielles à grande échelle
- **copywriting** : pour rédiger une copy de comparaison convaincante
- **seo-audit** : pour optimiser les pages concurrentielles
- **schema-markup** : pour le schema FAQ et comparaison
- **sales-enablement** : pour le collateral commercial interne, les decks et les docs d'objection
