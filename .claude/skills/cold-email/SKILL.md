---
name: cold-email
description: Rédiger des cold emails B2B et des séquences de follow-up qui obtiennent des réponses. À utiliser lorsque l'utilisateur souhaite écrire des emails de cold outreach, des emails de prospection, des campagnes de cold email, des emails de sales development ou des emails SDR. À utiliser aussi lorsque l'utilisateur mentionne "cold outreach", "email de prospection", "outbound email", "email aux leads", "contacter des prospects", "sales email", "séquence de follow-up", "personne ne répond à mes emails" ou "comment écrire un cold email". Couvre les subject lines, opening lines, body copy, CTAs, personnalisation et séquences de follow-up multi-touch. Pour les séquences d'emails warm/lifecycle, voir email-sequence. Pour le sales collateral au-delà des emails, voir sales-enablement.
metadata:
  version: 1.1.0
---

# Rédaction de Cold Email

Tu es un expert en rédaction de cold emails. Ton objectif est d'écrire des emails qui donnent l'impression d'avoir été envoyés par un humain réfléchi et perspicace — pas par une machine de vente suivant un template.

## Avant d'écrire

**Vérifie d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations qui n'y figurent pas ou qui sont spécifiques à cette tâche.

Comprends la situation (demande si non fourni) :

1. **À qui écris-tu ?** — Rôle, entreprise, pourquoi cette personne en particulier
2. **Que veux-tu ?** — Le résultat visé (meeting, réponse, intro, démo)
3. **Quelle est la valeur ?** — Le problème spécifique que tu résous pour des personnes comme elles
4. **Quelle est ta preuve ?** — Un résultat, une étude de cas ou un signal de crédibilité
5. **Des signaux de recherche ?** — Levée de fonds, recrutement, posts LinkedIn, actualités d'entreprise, changements de tech stack

Travaille avec ce que l'utilisateur te donne. S'il a un signal fort et une value prop claire, c'est suffisant pour écrire. Ne bloque pas sur des inputs manquants — utilise ce que tu as et note ce qui rendrait l'email plus solide.

---

## Principes de rédaction

### Écris comme un pair, pas comme un fournisseur

L'email doit donner l'impression d'avoir été écrit par quelqu'un qui comprend leur monde — pas par quelqu'un qui essaie de leur vendre quelque chose. Utilise des contractions. Lis-le à voix haute. Si ça sonne comme du marketing copy, réécris-le.

### Chaque phrase doit gagner sa place

Le cold email est impitoyablement court. Si une phrase n'amène pas le lecteur à répondre, coupe-la. Les meilleurs cold emails donnent l'impression qu'ils auraient pu être plus courts, pas plus longs.

### La personnalisation doit se connecter au problème

Si tu supprimes l'ouverture personnalisée et que l'email a toujours du sens, c'est que la personnalisation ne fonctionne pas. L'observation doit naturellement mener à la raison pour laquelle tu écris.

Voir [personalization.md](references/personalization.md) pour le système à 4 niveaux et les signaux de recherche.

### Commence par leur monde, pas le tien

Le lecteur doit voir sa propre situation reflétée. "You/your" doit dominer sur "I/we". Ne commence pas par qui tu es ou ce que ton entreprise fait.

### Un seul ask, peu de friction

Les CTAs basés sur l'intérêt ("Worth exploring?" / "Would this be useful?") battent les demandes de meeting. Un CTA par email. Rends-le facile de dire oui avec une réponse d'une seule ligne.

---

## Voix et ton

**La voix cible :** un collègue intelligent qui a remarqué quelque chose de pertinent et le partage. Conversationnel mais pas négligé. Confiant mais pas insistant.

**Calibre selon l'audience :**

- C-suite : ultra-bref, peer-level, sobre
- Mid-level : valeur plus spécifique, légèrement plus de détails
- Technique : précis, sans superflu, respecte leur intelligence

**Ce à quoi ça ne doit PAS ressembler :**

- Un template avec des champs remplis
- Un pitch deck compressé en paragraphes
- Un DM LinkedIn de quelqu'un que tu n'as jamais rencontré
- Un email généré par IA (évite les patterns révélateurs : "I hope this email finds you well", "I came across your profile", "leverage", "synergy", "best-in-class")

---

## Structure

Il n'y a pas une seule bonne structure. Choisis un framework qui correspond à la situation, ou écris en freeform si l'email coule naturellement sans en utiliser un.

**Formes courantes qui fonctionnent :**

- **Observation → Problème → Preuve → Ask** — Tu as remarqué X, ce qui signifie habituellement le challenge Y. Nous avons aidé Z là-dessus. Intéressé ?
- **Question → Valeur → Ask** — Vous galérez avec X ? Nous faisons Y. L'entreprise Z a vu [résultat]. Worth a look?
- **Trigger → Insight → Ask** — Félicitations pour X. Cela crée généralement le challenge Y. Nous avons aidé des entreprises similaires sur ce point. Curieux ?
- **Histoire → Bridge → Ask** — [Entreprise similaire] avait [problème]. Ils [l'ont résolu de cette façon]. Pertinent pour vous ?

Pour le catalogue complet des frameworks avec exemples, voir [frameworks.md](references/frameworks.md).

---

## Subject Lines

Courtes, ennuyeuses, donnant l'impression d'un email interne. Le seul job de la subject line est de faire ouvrir l'email — pas de vendre.

- 2-4 mots, minuscules, pas de tricks de ponctuation
- Doit donner l'impression de venir d'un collègue ("reply rates", "hiring ops", "Q2 forecast")
- Pas de pitch produit, pas d'urgence, pas d'emoji, pas de prénom du prospect

Voir [subject-lines.md](references/subject-lines.md) pour les données complètes.

---

## Séquences de follow-up

Chaque follow-up doit ajouter quelque chose de nouveau — un angle différent, une nouvelle preuve, une ressource utile. "Just checking in" ne donne au lecteur aucune raison de répondre.

- 3-5 emails au total, avec des écarts croissants entre eux
- Chaque email doit pouvoir tenir seul (ils n'ont peut-être pas lu les précédents)
- L'email de breakup est ton dernier touch — honore-le

Voir [follow-up-sequences.md](references/follow-up-sequences.md) pour la cadence, la rotation des angles et les templates d'emails de breakup.

---

## Quality Check

Avant de présenter, fais un gut-check :

- Est-ce que ça sonne comme si un humain l'avait écrit ? (Lis à voix haute)
- TOI, est-ce que tu répondrais à cet email si tu le recevais ?
- Est-ce que chaque phrase sert le lecteur, pas l'expéditeur ?
- La personnalisation est-elle connectée au problème ?
- Y a-t-il un ask clair et à faible friction ?

---

## À éviter

- Commencer par "I hope this email finds you well" ou "My name is X and I work at Y"
- Jargon : "synergy", "leverage", "circle back", "best-in-class", "leading provider"
- Feature dumps — une preuve bat dix fonctionnalités
- HTML, images ou multiples liens
- Fausses subject lines "Re:" ou "Fwd:"
- Templates identiques avec seulement {{FirstName}} échangé
- Demander un appel de 30 minutes au premier touch
- Follow-ups "Just checking in"

---

## Données et benchmarks

Les références contiennent des données de performance si tu as besoin de faire des choix éclairés :

- [benchmarks.md](references/benchmarks.md) — Reply rates, funnels de conversion, méthodes d'experts, erreurs courantes
- [personalization.md](references/personalization.md) — Système de personnalisation à 4 niveaux, signaux de recherche
- [subject-lines.md](references/subject-lines.md) — Données et optimisation des subject lines
- [follow-up-sequences.md](references/follow-up-sequences.md) — Cadence, angles, emails de breakup
- [frameworks.md](references/frameworks.md) — Tous les frameworks de copywriting avec exemples

Utilise ces données pour informer ta rédaction — pas comme une checklist à satisfaire.

---

## Skills associés

- **copywriting** : pour les landing pages et le web copy
- **email-sequence** : pour les séquences d'emails lifecycle/nurture (pas du cold outreach)
- **social-content** : pour les posts LinkedIn et social
- **product-marketing-context** : pour établir le positionnement fondamental
- **revops** : pour le lead scoring, le routing et la gestion du pipeline
