---
name: product-marketing-context
description: "Lorsque l'utilisateur souhaite créer ou mettre à jour son document de contexte product marketing. À utiliser également lorsque l'utilisateur mentionne 'contexte produit', 'contexte marketing', 'mettre en place le contexte', 'positionnement', 'qui est mon audience cible', 'décrire mon produit', 'ICP', 'ideal customer profile', ou souhaite éviter de répéter des informations de base entre les tâches marketing. À utiliser au début de tout nouveau projet avant d'utiliser d'autres skills marketing — cela crée `.agents/product-marketing-context.md` que tous les autres skills consultent pour le contexte produit, audience et positionnement."
metadata:
  version: 1.1.0
---

# Contexte Product Marketing

Vous aidez les utilisateurs à créer et maintenir un document de contexte product marketing. Il capture les informations fondamentales de positionnement et de messaging que les autres skills marketing consultent, afin que les utilisateurs n'aient pas à se répéter.

Le document est stocké dans `.agents/product-marketing-context.md`.

## Workflow

### Étape 1 : Vérifier l'existence d'un contexte

D'abord, vérifiez si `.agents/product-marketing-context.md` existe déjà. Vérifiez aussi `.claude/product-marketing-context.md` pour les anciennes configurations — si trouvé là mais pas dans `.agents/`, proposez de le déplacer.

**S'il existe :**
- Le lire et résumer ce qui est capturé
- Demander quelles sections ils veulent mettre à jour
- Ne rassembler les infos que pour ces sections

**S'il n'existe pas, proposez deux options :**

1. **Auto-draft depuis le codebase** (recommandé) : vous étudiez le repo — README, landing pages, copy marketing, package.json, etc. — et vous rédigez une V1 du document de contexte. L'utilisateur révise ensuite, corrige et comble les manques. C'est plus rapide que de partir de zéro.

2. **Partir de zéro** : parcourir chaque section de manière conversationnelle, en rassemblant les infos section par section.

La plupart des utilisateurs préfèrent l'option 1. Après avoir présenté le draft, demandez : "Qu'est-ce qui doit être corrigé ? Qu'est-ce qui manque ?"

### Étape 2 : Rassembler les informations

**Si auto-drafting :**
1. Lisez le codebase : README, landing pages, copy marketing, pages "about", meta descriptions, package.json, toute doc existante
2. Rédigez toutes les sections à partir de ce que vous trouvez
3. Présentez le draft et demandez ce qui doit être corrigé ou ajouté
4. Itérez jusqu'à satisfaction de l'utilisateur

**Si vous partez de zéro :**
Parcourez chaque section ci-dessous de manière conversationnelle, une à la fois. Ne déversez pas toutes les questions d'un coup.

Pour chaque section :
1. Expliquez brièvement ce que vous capturez
2. Posez des questions pertinentes
3. Confirmez l'exactitude
4. Passez à la suivante

Insistez pour obtenir le langage verbatim des clients — les phrases exactes sont plus précieuses que les descriptions polies parce qu'elles reflètent comment les clients pensent et parlent réellement, ce qui rend la copy plus résonante.

---

## Sections à capturer

### 1. Vue d'ensemble du produit
- Description en une ligne
- Ce qu'il fait (2-3 phrases)
- Catégorie du produit (sur quelle "étagère" vous êtes — comment les clients vous cherchent)
- Type de produit (SaaS, marketplace, e-commerce, service, etc.)
- Modèle économique et tarification

### 2. Audience cible
- Type d'entreprise ciblée (secteur, taille, stade)
- Décisionnaires ciblés (rôles, départements)
- Cas d'usage principal (le problème central que vous résolvez)
- Jobs to be done (2-3 choses pour lesquelles les clients vous "embauchent")
- Cas d'usage ou scénarios spécifiques

### 3. Personas (B2B uniquement)
Si plusieurs parties prenantes sont impliquées dans l'achat, capturez pour chacune :
- User, Champion, Decision Maker, Financial Buyer, Technical Influencer
- Ce qui compte pour chacun, leur défi, et la valeur que vous leur promettez

### 4. Problèmes et pain points
- Défi central auquel les clients font face avant de vous trouver
- Pourquoi les solutions actuelles sont insuffisantes
- Ce que cela leur coûte (temps, argent, opportunités)
- Tension émotionnelle (stress, peur, doute)

### 5. Paysage concurrentiel
- **Concurrents directs** : même solution, même problème (ex. : Calendly vs SavvyCal)
- **Concurrents secondaires** : solution différente, même problème (ex. : Calendly vs scheduling de Superhuman)
- **Concurrents indirects** : approche conflictuelle (ex. : Calendly vs assistant personnel)
- En quoi chacun est insuffisant pour les clients

### 6. Différenciation
- Différenciateurs clés (capacités qui manquent aux alternatives)
- Comment vous le résolvez différemment
- Pourquoi c'est mieux (bénéfices)
- Pourquoi les clients vous choisissent plutôt que les alternatives

### 7. Objections et anti-personas
- Top 3 des objections entendues en vente et comment y répondre
- Qui n'est PAS un bon fit (anti-persona)

### 8. Dynamique de changement
Les quatre forces JTBD :
- **Push** : quelles frustrations les éloignent de la solution actuelle
- **Pull** : ce qui les attire vers vous
- **Habit** : ce qui les maintient bloqués dans l'approche actuelle
- **Anxiety** : ce qui les inquiète à propos du changement

### 9. Langage client
- Comment les clients décrivent le problème (verbatim)
- Comment ils décrivent votre solution (verbatim)
- Mots/phrases à utiliser
- Mots/phrases à éviter
- Glossaire des termes spécifiques au produit

### 10. Voix de marque
- Ton (professionnel, décontracté, ludique, etc.)
- Style de communication (direct, conversationnel, technique)
- Personnalité de la marque (3-5 adjectifs)

### 11. Proof points
- Métriques ou résultats clés à citer
- Clients/logos notables
- Extraits de témoignages
- Thèmes de valeur principaux et preuves à l'appui

### 12. Objectifs
- Objectif business principal
- Action de conversion clé (ce que vous voulez que les gens fassent)
- Métriques actuelles (si connues)

---

## Étape 3 : Créer le document

Après avoir rassemblé les informations, créez `.agents/product-marketing-context.md` avec cette structure :

```markdown
# Product Marketing Context

*Last updated: [date]*

## Product Overview
**One-liner:**
**What it does:**
**Product category:**
**Product type:**
**Business model:**

## Target Audience
**Target companies:**
**Decision-makers:**
**Primary use case:**
**Jobs to be done:**
-
**Use cases:**
-

## Personas
| Persona | Cares about | Challenge | Value we promise |
|---------|-------------|-----------|------------------|
| | | | |

## Problems & Pain Points
**Core problem:**
**Why alternatives fall short:**
-
**What it costs them:**
**Emotional tension:**

## Competitive Landscape
**Direct:** [Competitor] — falls short because...
**Secondary:** [Approach] — falls short because...
**Indirect:** [Alternative] — falls short because...

## Differentiation
**Key differentiators:**
-
**How we do it differently:**
**Why that's better:**
**Why customers choose us:**

## Objections
| Objection | Response |
|-----------|----------|
| | |

**Anti-persona:**

## Switching Dynamics
**Push:**
**Pull:**
**Habit:**
**Anxiety:**

## Customer Language
**How they describe the problem:**
- "[verbatim]"
**How they describe us:**
- "[verbatim]"
**Words to use:**
**Words to avoid:**
**Glossary:**
| Term | Meaning |
|------|---------|
| | |

## Brand Voice
**Tone:**
**Style:**
**Personality:**

## Proof Points
**Metrics:**
**Customers:**
**Testimonials:**
> "[quote]" — [who]
**Value themes:**
| Theme | Proof |
|-------|-------|
| | |

## Goals
**Business goal:**
**Conversion action:**
**Current metrics:**
```

---

## Étape 4 : Confirmer et sauvegarder

- Montrer le document complété
- Demander si quelque chose doit être ajusté
- Sauvegarder dans `.agents/product-marketing-context.md`
- Leur dire : "Les autres skills marketing utiliseront désormais ce contexte automatiquement. Lancez `/product-marketing-context` à tout moment pour le mettre à jour."

---

## Conseils

- **Soyez spécifique** : demandez "Quelle est la frustration n°1 qui les amène à vous ?" et non "Quel problème résolvent-ils ?"
- **Capturez les mots exacts** : le langage client bat les descriptions polies
- **Demandez des exemples** : "Pouvez-vous me donner un exemple ?" débloque de meilleures réponses
- **Validez au fur et à mesure** : résumez chaque section et confirmez avant de passer à la suivante
- **Sautez ce qui ne s'applique pas** : tous les produits n'ont pas besoin de toutes les sections (ex. : Personas pour le B2C)
