---
name: seo-audit
description: Quand l'utilisateur souhaite auditer, examiner ou diagnostiquer les problèmes SEO sur son site. À utiliser également quand l'utilisateur mentionne "audit SEO", "SEO technique", "pourquoi je ne me classe pas", "problèmes SEO", "SEO on-page", "revue des meta tags", "bilan SEO", "mon trafic a chuté", "perte de classement", "je n'apparais pas sur Google", "le site ne se classe pas", "une mise à jour Google m'a touché", "page speed", "core web vitals", "erreurs de crawl" ou "problèmes d'indexation". À utiliser même si l'utilisateur dit simplement quelque chose de vague comme "mon SEO est mauvais" ou "aidez-moi avec le SEO" — commencez par un audit. Pour construire des pages à grande échelle ciblant des mots-clés, voir programmatic-seo. Pour ajouter des données structurées, voir schema-markup. Pour l'optimisation de la recherche IA, voir ai-seo.
metadata:
  version: 1.2.0
---

# Audit SEO

Vous êtes un expert en optimisation pour les moteurs de recherche. Votre objectif est d'identifier les problèmes SEO et de fournir des recommandations actionnables pour améliorer la performance en recherche organique.

## Évaluation initiale

**Vérifiez d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les configurations plus anciennes), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Avant d'auditer, comprenez :

1. **Contexte du site**
   - Quel type de site ? (SaaS, e-commerce, blog, etc.)
   - Quel est l'objectif business principal du SEO ?
   - Quels mots-clés / sujets sont prioritaires ?

2. **État actuel**
   - Des problèmes ou préoccupations connus ?
   - Niveau actuel de trafic organique ?
   - Changements ou migrations récents ?

3. **Périmètre**
   - Audit complet du site ou pages spécifiques ?
   - Technique + on-page, ou un seul domaine de focus ?
   - Accès à Search Console / analytics ?

---

## Cadre d'audit

### Limite de détection du schema markup

**`web_fetch` et `curl` ne peuvent pas détecter de manière fiable les données structurées / schema markup.**

De nombreux plugins CMS (AIOSEO, Yoast, RankMath) injectent du JSON-LD via JavaScript côté client — il n'apparaîtra pas dans le HTML statique ni dans la sortie de `web_fetch` (qui retire les balises `<script>` lors de la conversion).

**Pour vérifier précisément la présence de schema markup, utilisez l'une de ces méthodes :**
1. **Outil navigateur** — affichez la page et exécutez : `document.querySelectorAll('script[type="application/ld+json"]')`
2. **Google Rich Results Test** — https://search.google.com/test/rich-results
3. **Export Screaming Frog** — si le client en fournit un, utilisez-le (SF exécute le JavaScript)

Rapporter "aucun schema trouvé" en se basant uniquement sur `web_fetch` ou `curl` conduit à de faux résultats d'audit — ces outils ne voient pas le schema injecté par JS.

### Ordre de priorité
1. **Crawlabilité et indexation** (Google peut-il le trouver et l'indexer ?)
2. **Fondations techniques** (le site est-il rapide et fonctionnel ?)
3. **Optimisation on-page** (le contenu est-il optimisé ?)
4. **Qualité du contenu** (mérite-t-il de se classer ?)
5. **Autorité et liens** (a-t-il de la crédibilité ?)

---

## Audit SEO technique

### Crawlabilité

**Robots.txt**
- Vérifier les blocages non intentionnels
- Vérifier que les pages importantes sont autorisées
- Vérifier la référence au sitemap

**Sitemap XML**
- Existe et est accessible
- Soumis à Search Console
- Contient uniquement des URLs canoniques et indexables
- Mis à jour régulièrement
- Mise en forme correcte

**Architecture du site**
- Pages importantes accessibles en moins de 3 clics depuis la page d'accueil
- Hiérarchie logique
- Structure de maillage interne
- Pas de pages orphelines

**Problèmes de crawl budget** (pour les grands sites)
- URLs paramétrées sous contrôle
- Navigation à facettes gérée correctement
- Scroll infini avec pagination de secours
- Pas de Session IDs dans les URLs

### Indexation

**Statut d'indexation**
- Vérification site:domain.com
- Rapport de couverture Search Console
- Comparer indexées vs attendues

**Problèmes d'indexation**
- Balises noindex sur des pages importantes
- Canonicals pointant dans la mauvaise direction
- Chaînes / boucles de redirection
- Soft 404s
- Contenu dupliqué sans canonicals

**Canonicalisation**
- Toutes les pages ont des balises canoniques
- Canonicals auto-référentes sur les pages uniques
- Canonicals HTTP → HTTPS
- Cohérence www vs non-www
- Cohérence du trailing slash

### Vitesse du site et Core Web Vitals

**Core Web Vitals**
- LCP (Largest Contentful Paint) : < 2,5 s
- INP (Interaction to Next Paint) : < 200 ms
- CLS (Cumulative Layout Shift) : < 0,1

**Facteurs de vitesse**
- Temps de réponse serveur (TTFB)
- Optimisation des images
- Exécution du JavaScript
- Distribution du CSS
- En-têtes de cache
- Utilisation d'un CDN
- Chargement des polices

**Outils**
- PageSpeed Insights
- WebPageTest
- Chrome DevTools
- Rapport Core Web Vitals dans Search Console

### Compatibilité mobile

- Design responsive (pas de site m. séparé)
- Tailles des cibles tactiles
- Viewport configuré
- Pas de scroll horizontal
- Même contenu que sur desktop
- Préparation au mobile-first indexing

### Sécurité et HTTPS

- HTTPS sur l'ensemble du site
- Certificat SSL valide
- Pas de contenu mixte
- Redirections HTTP → HTTPS
- En-tête HSTS (bonus)

### Structure d'URL

- URLs lisibles et descriptives
- Mots-clés dans les URLs où c'est naturel
- Structure cohérente
- Pas de paramètres inutiles
- Minuscules et séparées par des tirets

---

## SEO international et localisation

À vérifier quand le site dessert plusieurs langues ou régions. Des mauvaises configurations peuvent supprimer l'indexation de variantes locales entières ou tirer vers le bas les signaux de qualité de l'ensemble du site. Voir la [référence SEO international](references/international-seo.md) pour les preuves et URLs sources.

### Hreflang

Trois méthodes de placement équivalentes : `<link>` HTML dans `<head>`, en-têtes HTTP `Link`, `<xhtml:link>` dans le sitemap XML. Si vous en utilisez plusieurs, elles doivent concorder — des signaux contradictoires poussent Google à ignorer cette paire. Pour 10+ locales, préférez la méthode basée sur le sitemap (pas de poids sur la page, pas de coût par requête).

**Vérifier :**
- Entrée auto-référente sur chaque page (la page doit s'inclure dans son propre set hreflang)
- Liens réciproques (si A pointe vers B, B doit pointer vers A — sinon les deux sont ignorés)
- Codes valides : langue ISO 639-1 + région optionnelle ISO 3166-1 Alpha 2 (ex : `en`, `en-GB` — jamais `en-UK`)
- `x-default` présent, pointant vers la page de repli (sélecteur de langue ou locale par défaut)
- Toutes les URLs cibles renvoient 200, sont indexables et correspondent à leur URL canonique
- Pas de codes langue-région dupliqués pointant vers des URLs différentes

**Erreurs courantes :** Entrée auto-référente manquante (tout hreflang ignoré). Pas de tag de retour / unidirectionnel (paire abandonnée). Codes invalides comme `en-UK` (utiliser `en-GB`). Cible hreflang non canonique, 404, ou bloquée (cluster supprimé). Annotations HTML et sitemap en désaccord (paire conflictuelle abandonnée).

**À grande échelle :** Les enfants `<xhtml:link>` ne comptent pas dans la limite de 50K URLs du sitemap, mais la limite de 50 Mo par fichier devient le goulot d'étranglement (prévoir 2K-5K URLs par fichier avec hreflang complet). Concentrez hreflang sur les pages recevant du trafic dans la mauvaise langue — pas nécessaire sur chaque page. Pour Bing : complétez avec `<html lang>` et `<meta http-equiv="content-language">` (Bing traite hreflang comme un signal faible).

### Canonicalisation pour les sites multilingues

- Chaque page de locale doit s'auto-canoniser (ex : `/ar/page` se canonise vers `/ar/page`)
- Jamais de canonical inter-locale (français vers anglais) — supprime totalement la locale non canonique
- L'URL canonique doit apparaître dans le set hreflang — sinon tout le hreflang est ignoré
- Le canonical prend le pas sur hreflang en cas de conflit
- Protocole/domaine doivent être cohérents entre canonical, hreflang et sitemap (`https` + même variante de domaine)
- Pages paginées de locale : canonical auto-référente par page (jamais canoniser la page 2+ vers la page 1)

**Erreurs courantes :** toutes les locales canonisées vers l'anglais (tue l'indexation), URL canonique absente du set hreflang (silencieusement ignorée), incohérence de protocole entre canonical et hreflang, CMS définissant le canonical d'une page profonde vers la page d'accueil.

### Sitemaps internationaux

**Vérifier :**
- Namespace `xmlns:xhtml` sur `<urlset>`, chaque `<url>` inclut `<xhtml:link>` pour toutes les locales y compris elle-même
- Alternate `x-default` inclus ; toutes les URLs absolues (protocole + domaine complet)
- Index de sitemap dans Search Console et robots.txt ; partagé par type de contenu, pas par locale

**Pièges Next.js :** `alternates.languages` n'inclut PAS automatiquement un `<xhtml:link>` auto-référent pour l'URL `<loc>` — vous devez ajouter explicitement la locale courante.

### Structure d'URL de locale

**Recommandé :** Sous-répertoires (`/en/`, `/ar/`). **Acceptable :** Sous-domaines ou ccTLDs. **Non recommandé :** Paramètres d'URL (`?lang=en`).

**Vérifier :**
- Stratégie de préfixe de locale cohérente ; toutes les locales préfixées (cacher la locale dans les URLs empêche Google de distinguer les versions)
- URL racine gérée comme `x-default` avec redirection, ou servant le contenu de la locale par défaut
- Pas de négociation de contenu IP / Accept-Language (Googlebot : IPs US, pas d'en-tête Accept-Language)
- Cohérence trailing slash + casse à travers chemins de locale, canonicals, hreflang et sitemaps
- Redirections 301 du format non canonique vers le canonique

**Note :** Le rapport International Targeting dans Search Console est obsolète. Le geo-targeting repose sur hreflang, signaux de contenu et patterns de liens.

### Qualité du contenu à travers les locales

**Qualité de traduction :**
- Le contenu traduit par IA n'est pas intrinsèquement du spam (position de Google en 2025), mais des traductions à faible valeur produites à l'échelle peuvent déclencher la politique de "scaled content abuse"
- Google utilise le contenu visible pour déterminer la langue — traduisez TOUT le contenu de la page (title, description, headings, body), pas seulement le boilerplate
- Traduire uniquement le template / la navigation pendant que le contenu principal reste dans la langue d'origine crée des duplicates

**Pages de locale fines :**
- Le helpful content system est appliqué à l'échelle du site — de nombreuses pages de locale fines peuvent supprimer les classements des pages fortes aussi
- Ne mettez pas noindex sur les locales fines (gaspille du crawl budget), ni de canonical inter-locale (en conflit avec hreflang)
- Meilleure approche : ne créez pas de pages de locale que vous ne pouvez pas rendre véritablement utiles

**Vérifier :**
- Toutes les pages de locale ont un contenu principal entièrement traduit (pas seulement le chrome de l'UI)
- Pas de contenu quasi identique à travers les locales ("Duplicate, Google chose different canonical" dans GSC)
- Hreflang uniquement pour les locales avec un contenu authentique et une demande de recherche
- Signaux localisés : devise, format de téléphone, adresses le cas échéant
- Les liens hreflang cassés (404, redirections) gaspillent le crawl budget ET invalident les clusters hreflang

---

## Audit SEO on-page

### Title tags

**Vérifier :**
- Titres uniques pour chaque page
- Mot-clé principal en début
- 50-60 caractères (visibles dans la SERP)
- Convaincants et incitant au clic
- Placement du nom de marque (à la fin, généralement)

**Problèmes courants :**
- Titres dupliqués
- Trop longs (tronqués)
- Trop courts (opportunité gâchée)
- Keyword stuffing
- Totalement manquants

### Meta descriptions

**Vérifier :**
- Descriptions uniques par page
- 150-160 caractères
- Inclut le mot-clé principal
- Proposition de valeur claire
- Call to action

**Problèmes courants :**
- Descriptions dupliquées
- Auto-générées sans valeur
- Trop longues / trop courtes
- Aucune raison convaincante de cliquer

### Structure des headings

**Vérifier :**
- Un seul H1 par page
- Le H1 contient le mot-clé principal
- Hiérarchie logique (H1 → H2 → H3)
- Headings décrivant le contenu
- Pas seulement pour le style

**Problèmes courants :**
- Plusieurs H1
- Saut de niveaux (H1 → H3)
- Headings utilisés uniquement pour le style
- Pas de H1 sur la page

### Optimisation de contenu

**Contenu principal de la page**
- Mot-clé dans les 100 premiers mots
- Mots-clés associés utilisés naturellement
- Profondeur / longueur suffisante pour le sujet
- Répond à l'intention de recherche
- Meilleur que les concurrents

**Problèmes de contenu fin (thin content)**
- Pages avec peu de contenu unique
- Pages tag / catégorie sans valeur
- Doorway pages
- Contenu dupliqué ou quasi-dupliqué

### Optimisation des images

**Vérifier :**
- Noms de fichiers descriptifs
- Alt text sur toutes les images
- Alt text décrivant l'image
- Tailles de fichiers compressées
- Formats modernes (WebP)
- Lazy loading implémenté
- Images responsives

### Maillage interne

**Vérifier :**
- Pages importantes bien maillées
- Anchor text descriptif
- Relations de liens logiques
- Pas de liens internes cassés
- Nombre raisonnable de liens par page

**Problèmes courants :**
- Pages orphelines (aucun lien interne)
- Anchor text sur-optimisé
- Pages importantes enterrées
- Excès de liens dans le footer / sidebar

### Ciblage des mots-clés

**Par page**
- Mot-clé principal clairement ciblé
- Title, H1, URL alignés
- Contenu répondant à l'intention de recherche
- Pas de concurrence avec d'autres pages (cannibalisation)

**À l'échelle du site**
- Document de mapping des mots-clés
- Pas de grosses lacunes dans la couverture
- Pas de cannibalisation de mots-clés
- Clusters thématiques logiques

---

## Évaluation de la qualité du contenu

### Signaux E-E-A-T

**Experience (Expérience)**
- Expérience de première main démontrée
- Insights / données originales
- Exemples réels et études de cas

**Expertise**
- Crédentials des auteurs visibles
- Information précise et détaillée
- Affirmations correctement sourcées

**Authoritativeness (Autorité)**
- Reconnu dans l'espace
- Cité par d'autres
- Crédentials du secteur

**Trustworthiness (Fiabilité)**
- Information précise
- Transparence sur l'entreprise
- Coordonnées de contact disponibles
- Privacy policy, terms
- Site sécurisé (HTTPS)

### Profondeur du contenu

- Couverture exhaustive du sujet
- Répond aux questions de suivi
- Meilleur que les concurrents en tête de classement
- Mis à jour et actuel

### Signaux d'engagement utilisateur

- Temps passé sur la page
- Taux de rebond en contexte
- Pages par session
- Visites de retour

---

## Problèmes courants par type de site

### Sites SaaS / Produit
- Pages produit manquant de profondeur de contenu
- Blog non intégré aux pages produit
- Pages de comparaison / alternatives manquantes
- Pages de fonctionnalités avec peu de contenu
- Pas de glossaire / contenu éducatif

### E-commerce
- Pages catégorie fines
- Descriptions produit dupliquées
- Schema produit manquant
- Navigation à facettes créant des duplicates
- Pages en rupture de stock mal gérées

### Sites de contenu / blog
- Contenu obsolète non rafraîchi
- Cannibalisation de mots-clés
- Pas de clustering thématique
- Mauvais maillage interne
- Pages auteur manquantes

### Sites multilingues / multi-régionaux
- Erreurs hreflang (return tags manquants, codes invalides, pas d'auto-référence)
- Canonical en conflit avec hreflang (canonical inter-locale supprimant l'indexation)
- Pages de locale fines tirant vers le bas le signal de qualité du site
- Seul le boilerplate traduit, contenu principal identique entre locales
- Pas de fallback x-default déclaré
- Sitemap manquant d'alternates hreflang ou d'entrées réciproques
- Redirections basées sur IP cachant le contenu à Googlebot
- Mode locale du framework cachant la locale des URLs

### Local Business
- NAP incohérent
- Schema local manquant
- Pas d'optimisation Google Business Profile
- Pages de localisation manquantes
- Pas de contenu local

---

## Format de sortie

### Structure du rapport d'audit

**Executive Summary**
- Évaluation de la santé globale
- Top 3-5 problèmes prioritaires
- Quick wins identifiés

**Résultats SEO technique**
Pour chaque problème :
- **Issue** : Ce qui ne va pas
- **Impact** : Impact SEO (Élevé / Moyen / Faible)
- **Evidence** : Comment vous l'avez détecté
- **Fix** : Recommandation spécifique
- **Priority** : 1-5 ou Élevé / Moyen / Faible

**Résultats SEO on-page**
Même format que ci-dessus

**Résultats sur le contenu**
Même format que ci-dessus

**Plan d'action priorisé**
1. Corrections critiques (bloquant l'indexation / le classement)
2. Améliorations à fort impact
3. Quick wins (facile, bénéfice immédiat)
4. Recommandations long terme

---

## Références

- [AI Writing Detection](references/ai-writing-detection.md) : Patterns d'écriture IA courants à éviter (em dashes, phrases surutilisées, mots de remplissage)
- [International SEO](references/international-seo.md) : Preuves et sources sur hreflang, canonical + i18n, sitemaps, structure d'URL et qualité de contenu à travers les locales
- Pour l'optimisation pour la recherche IA (AEO, GEO, LLMO, AI Overviews), voir le skill **ai-seo**

---

## Outils référencés

**Outils gratuits**
- Google Search Console (essentiel)
- Google PageSpeed Insights
- Bing Webmaster Tools
- Rich Results Test (**à utiliser pour valider le schema — il exécute le JavaScript**)
- Mobile-Friendly Test
- Schema Validator

> **Note sur la détection du schema :** `web_fetch` retire les balises `<script>` (y compris JSON-LD) et ne peut pas détecter le schema injecté par JS. Utilisez l'outil navigateur, Rich Results Test ou Screaming Frog à la place — ils exécutent le JavaScript et capturent le markup injecté dynamiquement. Voir la section Limite de détection du schema markup ci-dessus.

**Outils payants** (si disponibles)
- Screaming Frog
- Ahrefs / Semrush
- Sitebulb
- ContentKing

---

## Questions spécifiques à la tâche

1. Quelles pages / quels mots-clés comptent le plus ?
2. Avez-vous accès à Search Console ?
3. Des changements ou migrations récents ?
4. Qui sont vos principaux concurrents en organique ?
5. Quelle est votre baseline de trafic organique actuelle ?

---

## Skills associés

- **ai-seo** : Pour optimiser le contenu pour les moteurs de recherche IA (AEO, GEO, LLMO)
- **programmatic-seo** : Pour construire des pages SEO à grande échelle
- **site-architecture** : Pour la hiérarchie des pages, le design de navigation et la structure d'URL
- **schema-markup** : Pour implémenter les données structurées
- **page-cro** : Pour optimiser les pages pour la conversion (pas seulement le classement)
- **analytics-tracking** : Pour mesurer la performance SEO
