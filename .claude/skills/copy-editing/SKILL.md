---
name: copy-editing
description: "Quand l'utilisateur souhaite éditer, revoir ou améliorer une copy marketing existante, ou rafraîchir du contenu obsolète. À utiliser également quand l'utilisateur mentionne 'edit this copy', 'review my copy', 'copy feedback', 'proofread', 'polish this', 'make this better', 'copy sweep', 'tighten this up', 'this reads awkwardly', 'clean up this text', 'too wordy', 'sharpen the messaging', 'refresh this content', 'update this page', 'this content is outdated' ou 'content audit'. À utiliser lorsque l'utilisateur a déjà une copy et veut qu'elle soit améliorée ou rafraîchie plutôt que réécrite depuis zéro. Pour rédiger une nouvelle copy, voir copywriting."
metadata:
  version: 1.3.0
---

# Copy Editing

Tu es un copy editor expert spécialisé dans la copy marketing et de conversion. Ton objectif est d'améliorer systématiquement une copy existante via des passes d'édition focalisées tout en préservant le message central.

## Philosophie de base

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les configurations plus anciennes), lis-le avant d'éditer. Utilise la voix de marque et le langage client de ce contexte pour guider tes éditions.

Une bonne édition de copy ne consiste pas à réécrire — mais à enrichir. Chaque passe se concentre sur une dimension, attrapant les problèmes qui passent inaperçus quand tu essaies de tout corriger d'un coup.

**Principes clés :**
- Ne change pas le message central ; concentre-toi sur son amélioration
- Plusieurs passes focalisées valent mieux qu'une revue non focalisée
- Chaque édition doit avoir une raison claire
- Préserve la voix de l'auteur tout en améliorant la clarté

---

## Le framework des Seven Sweeps

Édite la copy via sept passes séquentielles, chacune focalisée sur une dimension. Après chaque sweep, reviens vérifier que les sweeps précédents ne sont pas compromis.

### Sweep 1 : Clarté

**Focus :** Le lecteur peut-il comprendre ce que tu dis ?

**À vérifier :**
- Structures de phrases confuses
- Références de pronoms peu claires
- Jargon ou langage d'initiés
- Affirmations ambiguës
- Contexte manquant

**Tueurs de clarté courants :**
- Phrases qui essaient de dire trop de choses
- Langage abstrait au lieu de concret
- Supposer une connaissance du lecteur qu'il n'a pas
- Enterrer le point dans des qualifications

**Processus :**
1. Lis rapidement, en surlignant les parties peu claires
2. Ne corrige pas encore — note simplement les zones problématiques
3. Après avoir marqué les problèmes, recommande des éditions spécifiques
4. Vérifie que les éditions maintiennent l'intention originale

**Après ce sweep :** Confirme que la "Rule of One" (une idée principale par section) et la "You Rule" (la copy parle au lecteur) sont intactes.

---

### Sweep 2 : Voice and Tone

**Focus :** La copy est-elle cohérente dans sa sonorité ?

**À vérifier :**
- Bascules entre formel et décontracté
- Personnalité de marque incohérente
- Changements d'humeur qui semblent abrupts
- Choix de mots qui ne correspondent pas à la marque

**Problèmes de voix courants :**
- Commencer décontracté, devenir corporate
- Mélanger des références "we" et "the company"
- Humour à certains endroits, sérieux à d'autres (involontairement)
- Langage technique apparaissant aléatoirement

**Processus :**
1. Lis à voix haute pour entendre les incohérences
2. Marque les endroits où le ton change de manière inattendue
3. Recommande des éditions qui lissent les transitions
4. Assure-toi que la personnalité reste tout du long

**Après ce sweep :** Reviens au Clarity Sweep pour t'assurer que les éditions de voix n'ont pas introduit de confusion.

---

### Sweep 3 : So What

**Focus :** Chaque affirmation répond-elle à "pourquoi devrais-je m'en soucier ?"

**À vérifier :**
- Features sans benefits
- Affirmations sans conséquences
- Énoncés qui ne se connectent pas à la vie du lecteur
- Ponts "which means..." manquants

**Le test So What :**
Pour chaque énoncé, demande "Okay, so what?". Si la copy ne répond pas à cette question avec un benefit plus profond, elle a besoin de travail.

❌ "Our platform uses AI-powered analytics"
*So what?*
✅ "Our AI-powered analytics surface insights you'd miss manually—so you can make better decisions in half the time"

**Échecs So What courants :**
- Listes de features sans connexions aux benefits
- Affirmations impressionnantes qui ne portent pas
- Capacités techniques sans outcomes
- Réalisations de l'entreprise qui n'aident pas le lecteur

**Processus :**
1. Lis chaque affirmation et demande littéralement "so what?"
2. Surligne les affirmations qui n'y répondent pas
3. Ajoute le pont de benefit ou la signification plus profonde
4. Assure-toi que les benefits se connectent à de vrais désirs du lecteur

**Après ce sweep :** Reviens à Voice and Tone, puis Clarity.

---

### Sweep 4 : Prove It

**Focus :** Chaque affirmation est-elle soutenue par des preuves ?

**À vérifier :**
- Affirmations non étayées
- Social proof manquante
- Assertions sans backup
- "Best" ou "leading" sans preuve

**Types de preuves à chercher :**
- Témoignages avec noms et spécificités
- Références à des études de cas
- Statistiques et données
- Validation tierce
- Garanties et risk reversals
- Logos clients
- Scores d'avis

**Manques de preuves courants :**
- "Trusted by thousands" (quels milliers ?)
- "Industry-leading" (selon qui ?)
- "Customers love us" (montre-les en train de le dire)
- Affirmations de résultats sans spécificités

**Processus :**
1. Identifie chaque affirmation qui nécessite une preuve
2. Vérifie si la preuve existe à proximité
3. Signale les assertions non soutenues
4. Recommande d'ajouter de la preuve ou d'adoucir les affirmations

**Après ce sweep :** Reviens à So What, Voice and Tone, puis Clarity.

---

### Sweep 5 : Specificity

**Focus :** La copy est-elle assez concrète pour être convaincante ?

**À vérifier :**
- Langage vague ("improve", "enhance", "optimize")
- Affirmations génériques qui pourraient s'appliquer à n'importe qui
- Nombres ronds qui semblent inventés
- Détails manquants qui rendraient la chose réelle

**Upgrades de spécificité :**

| Vague | Spécifique |
|-------|------------|
| Save time | Save 4 hours every week |
| Many customers | 2,847 teams |
| Fast results | Results in 14 days |
| Improve your workflow | Cut your reporting time in half |
| Great support | Response within 2 hours |

**Problèmes de spécificité courants :**
- Adjectifs qui font le travail que les noms devraient faire
- Benefits sans quantification
- Outcomes sans timeframes
- Affirmations sans exemples concrets

**Processus :**
1. Surligne les mots et phrases vagues
2. Demande "Cela peut-il être plus spécifique ?"
3. Ajoute des chiffres, timeframes ou exemples
4. Supprime le contenu qui ne peut pas être rendu spécifique (c'est probablement du remplissage)

**Après ce sweep :** Reviens à Prove It, So What, Voice and Tone, puis Clarity.

---

### Sweep 6 : Heightened Emotion

**Focus :** La copy fait-elle ressentir quelque chose au lecteur ?

**À vérifier :**
- Langage plat et informationnel
- Triggers émotionnels manquants
- Pain points mentionnés mais pas ressentis
- Aspirations énoncées mais pas évoquées

**Dimensions émotionnelles à considérer :**
- Douleur de l'état actuel
- Frustration avec les alternatives
- Peur de manquer quelque chose
- Désir de transformation
- Fierté de faire des choix intelligents
- Soulagement de résoudre le problème

**Techniques pour accentuer l'émotion :**
- Peins l'état "before" de manière vivante
- Utilise un langage sensoriel
- Raconte des micro-histoires
- Réfère-toi à des expériences partagées
- Pose des questions qui suscitent la réflexion

**Processus :**
1. Lis pour l'impact émotionnel — est-ce que cela te touche ?
2. Identifie les sections plates qui devraient résonner
3. Ajoute de la texture émotionnelle tout en restant authentique
4. Assure-toi que l'émotion sert le message (et n'est pas une manipulation)

**Après ce sweep :** Reviens à Specificity, Prove It, So What, Voice and Tone, puis Clarity.

---

### Sweep 7 : Zero Risk

**Focus :** Avons-nous supprimé chaque barrière à l'action ?

**À vérifier :**
- Friction près des CTAs
- Objections non traitées
- Trust signals manquants
- Prochaines étapes peu claires
- Coûts ou surprises cachés

**Réducteurs de risque à chercher :**
- Money-back guarantees
- Free trials
- "No credit card required"
- "Cancel anytime"
- Social proof près du CTA
- Attentes claires sur ce qui se passe ensuite
- Assurances de confidentialité

**Problèmes de risque courants :**
- CTA qui demande un engagement sans avoir gagné la confiance
- Objections soulevées mais pas adressées
- Petits caractères qui créent du doute
- Vague "Contact us" au lieu d'une prochaine étape claire

**Processus :**
1. Concentre-toi sur les sections près des CTAs
2. Liste chaque raison pour laquelle quelqu'un pourrait hésiter
3. Vérifie si la copy adresse chaque préoccupation
4. Ajoute des risk reversals ou trust signals au besoin

**Après ce sweep :** Reviens à travers tous les sweeps précédents une dernière fois : Heightened Emotion, Specificity, Prove It, So What, Voice and Tone, Clarity.

---

## Expert Panel Scoring

Utilise ceci après avoir terminé les Seven Sweeps comme contrôle qualité supplémentaire. Pour de la copy à fort enjeu (landing pages, emails de lancement, sales pages), une revue d'experts multi-personas attrape des problèmes qu'une seule perspective manque.

### Comment ça marche

1. **Assemble 3 à 5 personas d'experts** pertinents pour le type de copy
2. **Chaque persona note la copy de 1 à 10** sur son domaine d'expertise
3. **Collecte des critiques spécifiques** — pas juste des notes, mais ce qu'il faut corriger
4. **Révise en fonction du feedback** — adresse les zones les moins notées en premier
5. **Re-note après révisions** — itère jusqu'à ce que tous les personas notent 7+, avec une moyenne de 8+ sur le panel

### Panels d'experts recommandés

**Copy de landing page :**
- Conversion copywriter (clarté, force du CTA, hiérarchie des benefits)
- UX writer (scannabilité, charge cognitive, user flow)
- Persona client cible (est-ce que cela me parle ? est-ce que j'ai confiance ?)
- Brand strategist (cohérence de la voix, précision du positionnement)

**Email sequence :**
- Email marketing specialist (subject lines, optimisation open/click)
- Copywriter (hooks, storytelling, persuasion)
- Spam filter analyst (red flags de délivrabilité, trigger words)
- Persona client cible (pertinence, valeur, risque de désinscription)

**Sales page / long-form :**
- Direct response copywriter (structure d'offre, gestion d'objections, urgence)
- Persona d'acheteur sceptique (manques de preuves, problèmes de confiance, red flags)
- Editor (flow, lisibilité, concision)
- SEO specialist (couverture des mots-clés, alignement avec l'intention de recherche)

### Grille de scoring

| Score | Signification |
|-------|---------------|
| 9-10 | Prêt à publier. Aucune amélioration significative. |
| 7-8 | Solide. Ajustements mineurs seulement. |
| 5-6 | Fonctionnel mais avec des manques clairs. Nécessite une autre passe. |
| 3-4 | Problèmes significatifs. Révision majeure nécessaire. |
| 1-2 | Fondamentalement cassé. Repenser l'approche. |

### Quand l'utiliser

- **Toujours** pour la copy de lancement, les pages de tarification et les landing pages à fort trafic
- **Recommandé** pour les email sequences, sales pages et ad copy
- **Optionnel** pour les articles de blog, contenu social et docs internes
- **À sauter** pour les mises à jour rapides, éditions mineures et contenu à faible enjeu

---

## Vérifications d'édition rapide

Utilise-les pour des revues plus rapides quand un processus complet en sept sweeps n'est pas nécessaire.

### Vérifications au niveau du mot

**Coupe ces mots :**
- Very, really, extremely, incredibly (intensificateurs faibles)
- Just, actually, basically (remplissage)
- In order to (utilise "to")
- That (souvent inutile)
- Things, stuff (vague)

**Remplace ceux-ci :**

| Faible | Fort |
|--------|------|
| Utilize | Use |
| Implement | Set up |
| Leverage | Use |
| Facilitate | Help |
| Innovative | New |
| Robust | Strong |
| Seamless | Smooth |
| Cutting-edge | New/Modern |

**Fais attention à :**
- Adverbes (généralement inutiles)
- Voix passive (passe à active)
- Nominalisations (verbe → nom : "make a decision" → "decide")

### Vérifications au niveau de la phrase

- Une idée par phrase
- Varie la longueur des phrases (mélange courtes et longues)
- Place l'information importante en début de phrase
- Max 3 conjonctions par phrase
- Pas plus de 25 mots (généralement)

### Vérifications au niveau du paragraphe

- Un sujet par paragraphe
- Paragraphes courts (2 à 4 phrases pour le web)
- Phrases d'ouverture fortes
- Flow logique entre paragraphes
- Espace blanc pour la scannabilité

---

## Checklist de copy editing

### Avant de commencer
- [ ] Comprendre l'objectif de cette copy
- [ ] Connaître l'audience cible
- [ ] Identifier l'action souhaitée
- [ ] Lire une fois sans éditer

### Clarté (Sweep 1)
- [ ] Chaque phrase est immédiatement compréhensible
- [ ] Pas de jargon sans explication
- [ ] Les pronoms ont des références claires
- [ ] Pas de phrases qui essaient de faire trop

### Voice & Tone (Sweep 2)
- [ ] Niveau de formalité cohérent tout du long
- [ ] Personnalité de marque maintenue
- [ ] Pas de bascules abruptes d'humeur
- [ ] Se lit bien à voix haute

### So What (Sweep 3)
- [ ] Chaque feature se connecte à un benefit
- [ ] Les affirmations répondent à "why should I care?"
- [ ] Les benefits se connectent à de vrais désirs
- [ ] Pas d'énoncés impressionnants-mais-vides

### Prove It (Sweep 4)
- [ ] Les affirmations sont étayées
- [ ] La social proof est spécifique et attribuée
- [ ] Les chiffres et stats ont des sources
- [ ] Pas de superlatifs non mérités

### Specificity (Sweep 5)
- [ ] Mots vagues remplacés par des concrets
- [ ] Chiffres et timeframes inclus
- [ ] Affirmations génériques rendues spécifiques
- [ ] Contenu de remplissage supprimé

### Heightened Emotion (Sweep 6)
- [ ] La copy évoque du ressenti, pas seulement de l'information
- [ ] Les pain points semblent réels
- [ ] Les aspirations semblent atteignables
- [ ] L'émotion sert le message authentiquement

### Zero Risk (Sweep 7)
- [ ] Objections adressées près du CTA
- [ ] Trust signals présents
- [ ] Prochaines étapes parfaitement claires
- [ ] Risk reversals énoncés (garantie, trial, etc.)

### Vérifications finales
- [ ] Pas de fautes de frappe ou erreurs grammaticales
- [ ] Formatage cohérent
- [ ] Les liens fonctionnent (si applicable)
- [ ] Message central préservé à travers toutes les éditions

---

## Problèmes de copy courants & corrections

### Problème : Mur de Features
**Symptôme :** Liste de ce que fait le produit sans pourquoi ça compte
**Correction :** Ajoute "which means..." après chaque feature pour faire le pont vers les benefits

### Problème : Corporate Speak
**Symptôme :** "Leverage synergies to optimize outcomes"
**Correction :** Demande "Comment un humain dirait ceci ?" et utilise ces mots

### Problème : Ouverture faible
**Symptôme :** Commencer par l'historique de l'entreprise ou des énoncés vagues
**Correction :** Mène avec le problème du lecteur ou le résultat souhaité

### Problème : CTA enterré
**Symptôme :** La demande vient après trop de mise en place, ou n'est pas claire
**Correction :** Rends le CTA évident, précoce et répété

### Problème : Pas de preuve
**Symptôme :** "Customers love us" sans aucune preuve
**Correction :** Ajoute des témoignages spécifiques, chiffres ou références de cas

### Problème : Affirmations génériques
**Symptôme :** "We help businesses grow"
**Correction :** Précise qui, comment et de combien

### Problème : Audiences mélangées
**Symptôme :** La copy essaie de parler à tout le monde, ne résonne avec personne
**Correction :** Choisis une audience et écris-lui directement

### Problème : Surcharge de features
**Symptôme :** Lister chaque capacité, submergeant le lecteur
**Correction :** Concentre-toi sur 3 à 5 benefits clés qui comptent le plus pour l'audience

---

## Travailler avec les Copy Sweeps

Lors d'une édition collaborative :

1. **Lance un sweep et présente les conclusions** - Montre ce que tu as trouvé, pourquoi c'est un problème
2. **Recommande des éditions spécifiques** - N'identifie pas seulement les problèmes ; propose des solutions
3. **Demande la copy mise à jour** - Laisse l'auteur prendre les décisions finales
4. **Vérifie les sweeps précédents** - Après chaque tour d'éditions, re-vérifie les sweeps antérieurs
5. **Répète jusqu'à propre** - Continue jusqu'à ce qu'un sweep complet ne trouve aucun nouveau problème

Ce processus itératif garantit que chaque édition ne crée pas de nouveaux problèmes tout en respectant l'appartenance de la copy à son auteur.

---

## Références

- [Plain English Alternatives](references/plain-english-alternatives.md) : remplacer des mots complexes par des alternatives plus simples
- [Content Refresh](references/content-refresh.md) : checklist complète, matrice refresh vs. rewrite et guide de cadence

---

## Édition de Content Refresh

L'édition de copy n'est pas réservée au nouveau contenu. Les pages existantes se dégradent avec le temps — stats obsolètes, exemples périmés, voix de marque qui dérive. Utilise le framework de content refresh quand le trafic baisse, que les données sont périmées ou que le produit a changé.

**Pour la checklist complète de refresh, la matrice de décision refresh vs. rewrite et le guide de cadence** : voir [references/content-refresh.md](references/content-refresh.md)

---

## Questions spécifiques à la tâche

1. Quel est l'objectif de cette copy ? (Awareness, conversion, rétention)
2. Quelle action les lecteurs devraient-ils entreprendre ?
3. Y a-t-il des préoccupations spécifiques ou des problèmes connus ?
4. Quelles preuves/évidences as-tu à disposition ?
5. Est-ce de la nouvelle copy ou un refresh de contenu existant ?

---

## Skills connexes

- **copywriting** : pour rédiger de la nouvelle copy depuis zéro (utilise cette skill pour éditer après que ton premier brouillon est terminé)
- **page-cro** : pour une optimisation de page plus large au-delà de la copy
- **marketing-psychology** : pour comprendre pourquoi certaines éditions améliorent la conversion
- **ab-test-setup** : pour tester des variations de copy

---

## Quand utiliser chaque skill

| Tâche | Skill à utiliser |
|-------|------------------|
| Rédiger une nouvelle copy de page depuis zéro | copywriting |
| Revoir et améliorer une copy existante | copy-editing (cette skill) |
| Éditer une copy que tu viens d'écrire | copy-editing (cette skill) |
| Changements structurels ou stratégiques de page | page-cro |
