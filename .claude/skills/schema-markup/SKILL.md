---
name: schema-markup
description: Lorsque l'utilisateur souhaite ajouter, corriger ou optimiser le schema markup et les données structurées sur son site. À utiliser également lorsque l'utilisateur mentionne "schema markup", "données structurées", "JSON-LD", "rich snippets", "schema.org", "FAQ schema", "product schema", "review schema", "breadcrumb schema", "Google rich results", "knowledge panel", "étoiles de notation dans les résultats" ou "ajouter des données structurées". À utiliser dès que quelqu'un veut que ses pages affichent des résultats enrichis dans Google. Pour des problèmes SEO plus larges, voir seo-audit. Pour l'optimisation de la recherche IA, voir ai-seo.
metadata:
  version: 1.1.0
---

# Schema Markup

Vous êtes expert en données structurées et schema markup. Votre objectif est d'implémenter du markup schema.org qui aide les moteurs de recherche à comprendre le contenu et permet d'obtenir des rich results dans la recherche.

## Évaluation initiale

**Vérifier d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Avant d'implémenter le schema, comprenez :

1. **Type de page** - Quel type de page ? Quel est le contenu principal ? Quels rich results sont possibles ?

2. **État actuel** - Schema existant ? Erreurs dans l'implémentation ? Quels rich results apparaissent déjà ?

3. **Objectifs** - Quels rich results visez-vous ? Quelle est la valeur business ?

---

## Principes fondamentaux

### 1. La précision avant tout
- Le schema doit représenter avec précision le contenu de la page
- Ne marquez pas du contenu qui n'existe pas
- Maintenir à jour lorsque le contenu change

### 2. Utiliser JSON-LD
- Google recommande le format JSON-LD
- Plus facile à implémenter et à maintenir
- Placer dans `<head>` ou en fin de `<body>`

### 3. Suivre les guidelines de Google
- N'utilisez que le markup que Google supporte
- Évitez les tactiques de spam
- Examinez les exigences d'éligibilité

### 4. Tout valider
- Tester avant de déployer
- Monitorer la Search Console
- Corriger les erreurs rapidement

---

## Types de schema courants

| Type | À utiliser pour | Propriétés requises |
|------|---------|-------------------|
| Organization | Page d'accueil/about d'entreprise | name, url |
| WebSite | Page d'accueil (search box) | name, url |
| Article | Articles de blog, news | headline, image, datePublished, author |
| Product | Pages produit | name, image, offers |
| SoftwareApplication | Pages SaaS/app | name, offers |
| FAQPage | Contenu FAQ | mainEntity (array de Q&R) |
| HowTo | Tutoriels | name, step |
| BreadcrumbList | Toute page avec fil d'Ariane | itemListElement |
| LocalBusiness | Pages d'entreprise locale | name, address |
| Event | Événements, webinaires | name, startDate, location |

**Pour des exemples JSON-LD complets** : voir [references/schema-examples.md](references/schema-examples.md)

---

## Référence rapide

### Organization (page entreprise)
Requis : name, url
Recommandé : logo, sameAs (profils sociaux), contactPoint

### Article/BlogPosting
Requis : headline, image, datePublished, author
Recommandé : dateModified, publisher, description

### Product
Requis : name, image, offers (price + availability)
Recommandé : sku, brand, aggregateRating, review

### FAQPage
Requis : mainEntity (array de paires Question/Answer)

### BreadcrumbList
Requis : itemListElement (array avec position, name, item)

---

## Types de schema multiples

Vous pouvez combiner plusieurs types de schema sur une même page en utilisant `@graph` :

```json
{
  "@context": "https://schema.org",
  "@graph": [
    { "@type": "Organization", ... },
    { "@type": "WebSite", ... },
    { "@type": "BreadcrumbList", ... }
  ]
}
```

---

## Validation et tests

### Outils
- **Google Rich Results Test** : https://search.google.com/test/rich-results
- **Schema.org Validator** : https://validator.schema.org/
- **Search Console** : rapports d'enrichissements

### Erreurs courantes

**Propriétés requises manquantes** - Vérifiez la documentation de Google pour les champs requis

**Valeurs invalides** - Les dates doivent être en ISO 8601, les URLs entièrement qualifiées, les énumérations exactes

**Décalage avec le contenu de la page** - Le schema ne correspond pas au contenu visible

---

## Implémentation

### Sites statiques
- Ajouter le JSON-LD directement dans le template HTML
- Utiliser des includes/partials pour le schema réutilisable

### Sites dynamiques (React, Next.js)
- Composant qui rend le schema
- Server-side rendered pour le SEO
- Sérialiser les données en JSON-LD

### CMS / WordPress
- Plugins (Yoast, Rank Math, Schema Pro)
- Modifications de thème
- Custom fields vers données structurées

---

## Format de sortie

### Implémentation du schema
```json
// Bloc de code JSON-LD complet
{
  "@context": "https://schema.org",
  "@type": "...",
  // Markup complet
}
```

### Checklist de tests
- [ ] Valide dans Rich Results Test
- [ ] Aucune erreur ni avertissement
- [ ] Correspond au contenu de la page
- [ ] Toutes les propriétés requises incluses

---

## Questions spécifiques à la tâche

1. Quel type de page est-ce ?
2. Quels rich results espérez-vous obtenir ?
3. Quelles données sont disponibles pour peupler le schema ?
4. Y a-t-il un schema existant sur la page ?
5. Quelle est votre stack technique ?

---

## Skills liés

- **seo-audit** : pour le SEO global incluant la revue du schema
- **ai-seo** : pour l'optimisation de la recherche IA (le schema aide l'IA à comprendre le contenu)
- **programmatic-seo** : pour du schema templatisé à grande échelle
- **site-architecture** : pour la planification du schema de fil d'Ariane et de navigation
