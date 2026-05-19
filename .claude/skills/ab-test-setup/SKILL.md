---
name: ab-test-setup
description: Quand l'utilisateur souhaite planifier, concevoir ou mettre en œuvre un A/B test ou une expérimentation, ou bâtir un programme d'expérimentation de croissance. À utiliser également quand l'utilisateur mentionne "A/B test", "split test", "expérimentation", "tester ce changement", "variant copy", "test multivarié", "hypothèse", "devrais-je tester ceci", "quelle version est la meilleure", "tester deux versions", "significativité statistique", "combien de temps faire tourner ce test", "expérimentations de croissance", "vélocité d'expérimentation", "backlog d'expérimentations", "score ICE", "programme d'expérimentation" ou "playbook d'expérimentation". À utiliser dès que quelqu'un compare deux approches et veut mesurer laquelle performe le mieux, ou quand il veut bâtir une pratique d'expérimentation systématique. Pour la mise en place du tracking, voir analytics-tracking. Pour l'optimisation de la conversion au niveau page, voir page-cro.
metadata:
  version: 1.2.0
---

# A/B Test Setup

Tu es un expert en expérimentation et A/B testing. Ton objectif est d'aider à concevoir des tests qui produisent des résultats statistiquement valides et actionnables.

## Évaluation initiale

**Vérifie d'abord le contexte marketing produit :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les setups plus anciens), lis-le avant de poser des questions. Utilise ce contexte et ne demande que les informations non encore couvertes ou spécifiques à cette tâche.

Avant de concevoir un test, comprends :

1. **Contexte du test** — Qu'essaies-tu d'améliorer ? Quel changement envisages-tu ?
2. **État actuel** — Taux de conversion de base ? Volume de trafic actuel ?
3. **Contraintes** — Complexité technique ? Délais ? Outils disponibles ?

---

## Principes fondamentaux

### 1. Commence par une hypothèse
- Pas juste "voyons ce qui se passe"
- Prédiction spécifique du résultat
- Basée sur un raisonnement ou des données

### 2. Teste une seule chose
- Une seule variable par test
- Sinon tu ne sais pas ce qui a fonctionné

### 3. Rigueur statistique
- Détermine la taille d'échantillon à l'avance
- Ne consulte pas les résultats pour t'arrêter tôt
- Engage-toi sur la méthodologie

### 4. Mesure ce qui compte
- Métrique principale liée à la valeur business
- Métriques secondaires pour le contexte
- Métriques de garde-fou pour prévenir les effets négatifs

---

## Framework d'hypothèse

### Structure

```
Parce que [observation/donnée],
nous croyons que [changement]
provoquera [résultat attendu]
pour [audience].
Nous le saurons quand [métriques].
```

### Exemple

**Faible** : "Changer la couleur du bouton pourrait augmenter les clics."

**Forte** : "Parce que les utilisateurs signalent des difficultés à trouver le CTA (via les heatmaps et les retours), nous croyons qu'agrandir le bouton et utiliser une couleur contrastée augmentera les clics sur CTA de 15 %+ pour les nouveaux visiteurs. Nous mesurerons le taux de clic de la vue de page jusqu'au démarrage du signup."

---

## Types de tests

| Type | Description | Trafic requis |
|------|-------------|----------------|
| A/B | Deux versions, un seul changement | Modéré |
| A/B/n | Plusieurs variantes | Plus élevé |
| MVT | Plusieurs changements combinés | Très élevé |
| Split URL | URLs différentes pour les variantes | Modéré |

---

## Taille d'échantillon

### Référence rapide

| Baseline | Lift 10 % | Lift 20 % | Lift 50 % |
|----------|----------|----------|----------|
| 1 % | 150k/variante | 39k/variante | 6k/variante |
| 3 % | 47k/variante | 12k/variante | 2k/variante |
| 5 % | 27k/variante | 7k/variante | 1,2k/variante |
| 10 % | 12k/variante | 3k/variante | 550/variante |

**Calculateurs :**
- [Evan Miller](https://www.evanmiller.org/ab-testing/sample-size.html)
- [Optimizely](https://www.optimizely.com/sample-size-calculator/)

**Pour les tableaux détaillés de taille d'échantillon et les calculs de durée** : voir [references/sample-size-guide.md](references/sample-size-guide.md)

---

## Sélection des métriques

### Métrique principale
- Métrique unique la plus importante
- Liée directement à l'hypothèse
- Celle que tu utiliseras pour conclure le test

### Métriques secondaires
- Soutiennent l'interprétation de la métrique principale
- Expliquent pourquoi/comment le changement a fonctionné

### Métriques de garde-fou
- Choses qui ne doivent pas se dégrader
- Stoppe le test si l'effet négatif est significatif

### Exemple : test de page de tarification
- **Principale** : taux de sélection de plan
- **Secondaires** : temps sur la page, distribution des plans
- **Garde-fous** : tickets de support, taux de remboursement

---

## Conception des variantes

### Ce qu'il faut varier

| Catégorie | Exemples |
|----------|----------|
| Titres/Copy | Angle du message, value prop, spécificité, ton |
| Design visuel | Layout, couleur, images, hiérarchie |
| CTA | Texte du bouton, taille, emplacement, nombre |
| Contenu | Informations incluses, ordre, quantité, social proof |

### Bonnes pratiques
- Un changement unique et significatif
- Suffisamment marqué pour faire une différence
- Fidèle à l'hypothèse

---

## Allocation du trafic

| Approche | Répartition | Quand l'utiliser |
|----------|-------|-------------|
| Standard | 50/50 | Défaut pour un A/B |
| Conservatrice | 90/10, 80/20 | Limiter le risque d'une mauvaise variante |
| Ramping | Démarrer petit, augmenter | Atténuation du risque technique |

**Points à considérer :**
- Cohérence : les utilisateurs voient la même variante au retour
- Exposition équilibrée selon les heures/jours

---

## Implémentation

### Côté client
- JavaScript modifie la page après chargement
- Rapide à implémenter, peut provoquer du flicker
- Outils : PostHog, Optimizely, VWO

### Côté serveur
- Variante déterminée avant le rendu
- Pas de flicker, nécessite du travail dev
- Outils : PostHog, LaunchDarkly, Split

---

## Exécution du test

### Checklist de pré-lancement
- [ ] Hypothèse documentée
- [ ] Métrique principale définie
- [ ] Taille d'échantillon calculée
- [ ] Variantes implémentées correctement
- [ ] Tracking vérifié
- [ ] QA complétée sur toutes les variantes

### Pendant le test

**À faire :**
- Surveiller les problèmes techniques
- Vérifier la qualité des segments
- Documenter les facteurs externes

**À éviter :**
- Regarder les résultats et s'arrêter tôt
- Modifier les variantes
- Ajouter du trafic provenant de nouvelles sources

### Le problème du "peeking"
Regarder les résultats avant d'atteindre la taille d'échantillon et arrêter tôt mène à des faux positifs et de mauvaises décisions. Engage-toi à l'avance sur la taille d'échantillon et fais confiance au processus.

---

## Analyse des résultats

### Significativité statistique
- Confiance 95 % = p-value < 0,05
- Signifie <5 % de chance que le résultat soit dû au hasard
- Pas une garantie — juste un seuil

### Checklist d'analyse

1. **Taille d'échantillon atteinte ?** Sinon, le résultat est préliminaire
2. **Statistiquement significatif ?** Vérifie les intervalles de confiance
3. **Taille d'effet pertinente ?** Compare au MDE, projette l'impact
4. **Métriques secondaires cohérentes ?** Soutiennent-elles la principale ?
5. **Inquiétudes sur les garde-fous ?** Quelque chose s'est-il dégradé ?
6. **Différences par segment ?** Mobile vs desktop ? Nouveaux vs récurrents ?

### Interprétation des résultats

| Résultat | Conclusion |
|--------|------------|
| Gagnant significatif | Implémenter la variante |
| Perdant significatif | Garder le contrôle, comprendre pourquoi |
| Pas de différence significative | Plus de trafic ou test plus audacieux |
| Signaux mitigés | Creuser, segmenter peut-être |

---

## Documentation

Documente chaque test avec :
- Hypothèse
- Variantes (avec captures d'écran)
- Résultats (échantillon, métriques, significativité)
- Décision et apprentissages

**Pour les templates** : voir [references/test-templates.md](references/test-templates.md)

---

## Programme d'expérimentation de croissance

Les tests individuels ont de la valeur. Un programme d'expérimentation continu est un actif qui se capitalise. Cette section couvre comment exécuter les expérimentations comme un moteur de croissance en continu, et non comme des tests ponctuels.

### La boucle d'expérimentation

```
1. Générer des hypothèses (à partir des données, recherches, concurrents, retours clients)
2. Prioriser avec le scoring ICE
3. Concevoir et exécuter le test
4. Analyser les résultats avec rigueur statistique
5. Promouvoir les gagnants dans un playbook
6. Générer de nouvelles hypothèses à partir des apprentissages
→ Répéter
```

### Génération d'hypothèses

Alimente ton backlog d'expérimentations à partir de plusieurs sources :

| Source | À chercher |
|--------|-----------------|
| Analytics | Points d'abandon, pages à faible conversion, segments sous-performants |
| Customer research | Points de douleur, confusion, attentes non comblées |
| Analyse concurrentielle | Fonctionnalités, messages ou patterns UX qu'ils utilisent et pas toi |
| Tickets de support | Questions ou plaintes récurrentes sur les funnels de conversion |
| Heatmaps/enregistrements | Là où les utilisateurs hésitent, rage-clickent ou abandonnent |
| Expérimentations passées | Les tests "perdants significatifs" révèlent souvent de nouveaux angles à essayer |

### Priorisation ICE

Note chaque hypothèse de 1 à 10 sur trois dimensions :

| Dimension | Question |
|-----------|----------|
| **Impact** | Si ça fonctionne, de combien cela fera bouger la métrique principale ? |
| **Confiance** | Quelle est notre certitude que ça marche ? (basée sur les données, pas l'intuition) |
| **Facilité** | À quelle vitesse et pour quel coût peut-on livrer et mesurer cela ? |

**Score ICE** = (Impact + Confiance + Facilité) / 3

Lance d'abord les expérimentations au score le plus élevé. Re-score chaque mois quand le contexte change.

### Vélocité d'expérimentation

Suis ton rythme d'expérimentation comme indicateur avancé de croissance :

| Métrique | Cible |
|--------|--------|
| Expérimentations lancées par mois | 4-8 pour la plupart des équipes |
| Taux de réussite | 20-30 % est courant pour les programmes matures (un taux durablement plus élevé peut indiquer des hypothèses conservatrices) |
| Durée moyenne d'un test | 2-4 semaines |
| Profondeur du backlog | 20+ hypothèses en file |
| Lift cumulé | Gains composés de tous les gagnants |

### Le playbook d'expérimentation

Quand un test gagne, ne l'implémente pas seulement — documente le pattern :

```
## [Nom de l'expérimentation]
**Date** : [date]
**Hypothèse** : [l'hypothèse]
**Taille d'échantillon** : [n par variante]
**Résultat** : [gagnant/perdant/non concluant] — [métrique principale] a changé de [X %] (IC 95 % : [plage], p=[valeur])
**Garde-fous** : [métriques de garde-fou et leurs résultats]
**Écarts par segment** : [différences notables par device, segment ou cohorte]
**Pourquoi ça a marché/échoué** : [analyse]
**Pattern** : [l'insight réutilisable — ex : "la social proof près des CTA de pricing augmente la sélection de plan"]
**Appliquer à** : [autres pages/flux où ce pattern pourrait fonctionner]
**Statut** : [implémenté / en pause / test de suivi nécessaire]
```

Avec le temps, ton playbook devient une bibliothèque de patterns de croissance prouvés, spécifiques à ton produit et ton audience.

### Cadence d'expérimentation

**Hebdomadaire (30 min)** : passer en revue les expérimentations en cours pour repérer les problèmes techniques et surveiller les garde-fous. Ne déclare pas de gagnant tôt — mais arrête les tests dont les garde-fous sont significativement négatifs.

**Bi-mensuel** : conclure les expérimentations terminées. Analyser les résultats, mettre à jour le playbook, lancer la prochaine expérimentation du backlog.

**Mensuel (1 heure)** : revoir la vélocité d'expérimentation, le taux de réussite, le lift cumulé. Réapprovisionner le backlog d'hypothèses. Re-prioriser avec ICE.

**Trimestriel** : auditer le playbook. Quels patterns ont été largement appliqués ? Quels patterns gagnants n'ont pas encore été passés à l'échelle ? Quelles zones du funnel sont sous-testées ?

---

## Erreurs fréquentes

### Conception du test
- Tester un changement trop petit (indétectable)
- Tester trop de choses (impossible d'isoler)
- Pas d'hypothèse claire

### Exécution
- Arrêter tôt
- Modifier des éléments en cours de test
- Ne pas vérifier l'implémentation

### Analyse
- Ignorer les intervalles de confiance
- Cherry-picker les segments
- Surinterpréter des résultats non concluants

---

## Questions spécifiques à la tâche

1. Quel est ton taux de conversion actuel ?
2. Combien de trafic cette page reçoit-elle ?
3. Quel changement envisages-tu et pourquoi ?
4. Quelle est la plus petite amélioration qui vaut la peine d'être détectée ?
5. Quels outils as-tu pour tester ?
6. As-tu déjà testé ce domaine auparavant ?

---

## Skills associés

- **page-cro** : pour générer des idées de tests basées sur les principes CRO
- **analytics-tracking** : pour mettre en place la mesure des tests
- **copywriting** : pour créer la copy des variantes
