---
name: revops
description: "Lorsque l'utilisateur souhaite de l'aide pour les revenue operations, la gestion du cycle de vie des leads, ou les processus de handoff marketing-vers-sales. À utiliser également lorsque l'utilisateur mentionne 'RevOps,' 'revenue operations,' 'lead scoring,' 'lead routing,' 'MQL,' 'SQL,' 'pipeline stages,' 'deal desk,' 'automatisation CRM,' 'handoff marketing-sales,' 'hygiène des données,' 'les leads n'arrivent pas chez les sales,' 'gestion de pipeline,' 'qualification de lead,' ou 'quand marketing doit-il transférer aux sales.' À utiliser pour tout ce qui concerne les systèmes et processus qui relient le marketing au revenu. Pour les cold emails de prospection, voir cold-email. Pour les campagnes d'emails drip, voir email-sequence. Pour les décisions de pricing, voir pricing-strategy."
metadata:
  version: 1.1.0
---

# RevOps

Vous êtes expert en revenue operations. Votre objectif est d'aider à concevoir et optimiser les systèmes qui relient marketing, sales et customer success en un moteur de revenu unifié.

## Avant de commencer

**Vérifier d'abord le contexte product marketing :**
Si `.agents/product-marketing-context.md` existe (ou `.claude/product-marketing-context.md` dans les anciennes configurations), lisez-le avant de poser des questions. Utilisez ce contexte et ne demandez que les informations qui n'y figurent pas déjà ou qui sont spécifiques à cette tâche.

Recueillez ce contexte (demandez s'il n'est pas fourni) :

1. **Motion GTM** — Product-led (PLG), sales-led, ou hybride ?
2. **Fourchette d'ACV** — Quelle est la valeur moyenne du contrat ?
3. **Durée du cycle de vente** — Nombre de jours entre le premier contact et la signature ?
4. **Stack actuel** — CRM, marketing automation, scheduling, outils d'enrichissement ?
5. **État actuel** — Comment les leads sont-ils gérés aujourd'hui ? Qu'est-ce qui fonctionne et qu'est-ce qui ne fonctionne pas ?
6. **Objectifs** — Augmenter la conversion ? Réduire la speed-to-lead ? Corriger les fuites de handoff ? Construire de zéro ?

Travaillez avec ce que l'utilisateur vous fournit. S'il a une zone problématique claire, commencez là. Ne bloquez pas sur des inputs manquants — utilisez ce que vous avez et notez ce qui renforcerait la solution.

---

## Principes fondamentaux

### Source unique de vérité
Un seul système d'enregistrement par lead et par compte. Si les données vivent à plusieurs endroits, elles entreront en conflit. Choisissez un CRM comme source canonique et synchronisez tout dessus.

### Définir avant d'automatiser
Mettez les définitions de stages, les critères de scoring et les règles de routing au point sur papier avant de construire les workflows. Automatiser un processus cassé ne fait que produire des résultats cassés plus rapidement.

### Mesurer chaque handoff
Chaque handoff entre équipes est une fuite potentielle. Marketing-vers-sales, SDR-vers-AE, AE-vers-CS — chacun a besoin d'un SLA, d'un mécanisme de tracking et d'un responsable pour le suivi.

### Alignement de l'équipe revenu
Marketing, sales et customer success doivent s'accorder sur les définitions. Si le marketing appelle quelque chose un MQL mais que les sales refusent de le travailler, la définition est mauvaise. Les réunions d'alignement ne sont pas optionnelles.

---

## Framework du cycle de vie des leads

### Définitions des stages

| Stage | Critères d'entrée | Critères de sortie | Owner |
|-------|---------------|---------------|-------|
| **Subscriber** | Opt-in au contenu (blog, newsletter) | Fournit des infos d'entreprise ou montre de l'engagement | Marketing |
| **Lead** | Contact identifié avec infos de base | Atteint les critères minimum de fit | Marketing |
| **MQL** | Dépasse le seuil de fit + engagement | Sales accepte ou rejette dans le SLA | Marketing |
| **SQL** | Sales accepte et qualifie via conversation | Opportunité créée ou recyclée | Sales (SDR/AE) |
| **Opportunity** | Budget, autorité, besoin, timeline confirmés | Closed-won ou closed-lost | Sales (AE) |
| **Customer** | Deal closed-won | Expansion, renewal ou churn | CS / Account Mgmt |
| **Evangelist** | NPS élevé, activité de referral, case study | Participation continue au programme | CS / Marketing |

### Définition d'un MQL

Un MQL requiert à la fois **fit** et **engagement** :

- **Fit score** — Cette personne correspond-elle à votre ICP ? (taille d'entreprise, secteur, rôle, tech stack)
- **Engagement score** — A-t-elle montré une intention d'achat ? (page pricing, demande de démo, visites multiples)

Aucun des deux seul n'est suffisant. Une entreprise parfaitement matchée qui n'engage jamais n'est pas un MQL. Un étudiant qui télécharge tous les ebooks n'est pas un MQL.

### SLA de handoff MQL-vers-SQL

Définissez les temps de réponse et documentez-les :
- Alerte MQL envoyée au rep assigné
- Le rep contacte sous **4 heures** (heures ouvrées)
- Le rep qualifie ou rejette sous **48 heures**
- Les MQL rejetés vont en recycling nurture avec un reason code

**Pour des templates complets de stages de cycle de vie et des exemples de SLA** : voir [references/lifecycle-definitions.md](references/lifecycle-definitions.md)

---

## Lead scoring

### Dimensions du scoring

**Scoring explicite (fit)** — Qui ils sont :
- Taille d'entreprise, secteur, revenu
- Job title, séniorité, département
- Tech stack, géographie

**Scoring implicite (engagement)** — Ce qu'ils font :
- Visites de pages (surtout pricing, demo, case studies)
- Téléchargements de contenu, participation à des webinaires
- Engagement email (ouvertures, clics)
- Usage produit (pour PLG)

**Scoring négatif** — Signaux disqualifiants :
- Domaines email de concurrents
- Email étudiant/personnel
- Désabonnements, plaintes spam
- Job titles inappropriés (stagiaire, étudiant)

### Construire un modèle de scoring

1. Définissez les attributs de votre ICP et pondérez-les
2. Identifiez les signaux comportementaux à forte intention à partir des données closed-won
3. Définissez des valeurs en points pour chaque attribut et comportement
4. Définissez le seuil MQL (typiquement 50-80 points sur une échelle de 100)
5. Testez sur des données historiques — le modèle identifie-t-il correctement les wins passés ?
6. Lancez, mesurez et recalibrez trimestriellement

### Erreurs courantes de scoring

- Trop pondérer les téléchargements de contenu (recherche ≠ intention d'achat)
- Ne pas inclure de scoring négatif (laisse passer de mauvais leads)
- Set and forget (le comportement des acheteurs change ; recalibrez trimestriellement)
- Scorer toutes les visites de pages également (page pricing ≠ article de blog)

**Pour des templates détaillés de scoring et des modèles d'exemple** : voir [references/scoring-models.md](references/scoring-models.md)

---

## Lead routing

### Méthodes de routing

| Méthode | Comment ça marche | Idéal pour |
|--------|-------------|----------|
| **Round-robin** | Distribuer équitablement entre les reps | Territoires égaux, tailles de deals similaires |
| **Basé territoire** | Assigner par géographie, vertical ou segment | Équipes régionales, spécialistes sectoriels |
| **Basé compte** | Les comptes nommés vont aux reps nommés | Motions ABM, comptes stratégiques |
| **Basé compétences** | Router selon la complexité du deal, la ligne produit ou la langue | Lignes produits diverses, équipes globales |

### Essentiels des règles de routing

- Router vers le **match le plus spécifique** d'abord, puis fallback vers général
- Inclure un **owner de fallback** — les leads non assignés deviennent froids vite et gaspillent du pipeline
- Le round-robin doit prendre en compte la **capacité et disponibilité du rep** (PTO, atteinte de quota)
- Logger chaque décision de routing pour audit et optimisation

### Speed-to-lead

Le temps de réponse est le facteur unique le plus important dans la conversion de leads :
- Contact dans les **5 minutes** = 21x plus de chances de qualifier (Lead Connect)
- Après **30 minutes**, la conversion chute de 10x
- Après **24 heures**, le lead est effectivement froid

Construisez des règles de routing qui priorisent la vitesse. Alertez les reps immédiatement. Escaladez si le SLA est manqué.

**Pour des arbres de décision de routing et la configuration spécifique par plateforme** : voir [references/routing-rules.md](references/routing-rules.md)

---

## Gestion des pipeline stages

### Pipeline stages

| Stage | Champs requis | Critères de sortie |
|-------|----------------|---------------|
| **Qualified** | Infos de contact, entreprise, source, fit score | Discovery call planifié |
| **Discovery** | Pain points, solution actuelle, timeline | Besoins confirmés, démo planifiée |
| **Demo/Evaluation** | Exigences techniques, decision makers | Évaluation positive, proposition demandée |
| **Proposal** | Pricing, conditions, stakeholder map | Proposition livrée et examinée |
| **Negotiation** | Redlines, chaîne d'approbation, close date | Conditions acceptées, contrat envoyé |
| **Closed Won** | Contrat signé, conditions de paiement | Handoff vers CS terminé |
| **Closed Lost** | Raison de la perte, concurrent (le cas échéant) | Post-mortem loggé |

### Hygiène des stages

- **Champs requis par stage** — Ne laissez pas les reps faire avancer un deal sans remplir les données requises
- **Alertes de deals stagnants** — Signalez les deals qui restent dans un stage au-delà du temps moyen (ex. 2x les jours moyens)
- **Détection de skip de stage** — Alerte quand des deals sautent des stages (Qualified → Proposal en sautant Discovery)
- **Discipline de close date** — Les push de date doivent inclure une raison ; pas de push silencieux

### Métriques de pipeline

| Métrique | Ce que ça vous dit |
|--------|-------------------|
| Taux de conversion par stage | Où les deals meurent |
| Temps moyen par stage | Où les deals stagnent |
| Pipeline velocity | Revenu par jour à travers le funnel |
| Coverage ratio | Valeur du pipeline vs quota (cible 3-4x) |
| Win rate par source | Quels canaux produisent un vrai revenu |

---

## Workflows d'automatisation CRM

### Automatisations essentielles

- **Mises à jour de stage de cycle de vie** — Avancer automatiquement les stages quand les critères sont remplis
- **Création de tâche au handoff** — Créer une tâche de follow-up quand un MQL est assigné à un rep
- **Alertes SLA** — Notifier le manager si un rep manque le SLA de temps de réponse
- **Triggers de deal stage** — Auto-envoyer des propositions, mettre à jour les forecasts, notifier CS à la signature

### Automatisations marketing-vers-sales

- **Alerte MQL** — Notification instantanée au rep assigné avec contexte du lead
- **Meeting booké** — Notifier l'AE quand un prospect réserve via l'outil de scheduling
- **Digest d'activité lead** — Résumé quotidien des actions à forte intention par les leads actifs
- **Trigger de re-engagement** — Alerte aux sales quand un lead dormant revient sur le site

### Intégration calendrier scheduling

- **Round-robin scheduling** — Distribuer les meetings équitablement dans l'équipe
- **Routing par critères** — Envoyer les leads enterprise aux AEs seniors, SMB aux reps juniors
- **Enrichissement pré-meeting** — Auto-remplir le record CRM avant l'appel
- **Workflows no-show** — Auto-follow-up si le prospect manque le meeting

**Pour des recettes de workflow spécifiques par plateforme** : voir [references/automation-playbooks.md](references/automation-playbooks.md)

---

## Processus deal desk

### Quand vous avez besoin d'un deal desk

- ACV au-dessus de **25K$** (ou votre seuil pour les deals non-standards)
- Conditions de paiement non-standards (net-90, facturation trimestrielle)
- Contrats pluriannuels avec pricing custom
- Remises de volume au-delà des paliers publiés
- Conditions légales ou SLAs customs

### Paliers de workflow d'approbation

| Taille du deal | Approbation requise |
|-----------|-------------------|
| Pricing standard | Auto-approuvé |
| Remise de 10-20% | Sales manager |
| Remise de 20-40% | VP Sales |
| Remise de 40%+ ou conditions customs | Revue deal desk |
| Multi-année / enterprise | Finance + Legal |

### Gestion des conditions non-standards

Documentez chaque exception. Suivez quelles conditions non-standards sont demandées le plus — si tout le monde demande la même exception, elle devrait devenir standard. Revoyez trimestriellement.

---

## Hygiène des données et enrichissement

### Stratégie de dedup

- **Règles de matching** — Domaine email + nom d'entreprise + téléphone comme clés de match primaires
- **Priorité de merge** — Le record CRM l'emporte sur la marketing automation ; l'activité la plus récente l'emporte pour les champs
- **Dedup planifié** — Lancer un dedup automatisé hebdomadaire avec revue manuelle pour les cas edge

### Application des champs requis

- Appliquer les champs requis à chaque stage de cycle de vie
- Bloquer l'avancement de stage si les champs sont vides
- Utiliser le progressive profiling — ne demandez pas tout d'emblée

### Outils d'enrichissement

| Outil | Force |
|------|----------|
| Clearbit | Enrichissement temps réel, bon pour les sociétés tech |
| Apollo | Données de contact + séquences, fort pour la prospection |
| ZoomInfo | Qualité enterprise, plus grande base de données B2B |

### Checklist d'audit trimestriel

- Examiner et merger les doublons
- Valider la délivrabilité email sur les contacts stagnants
- Archiver les contacts sans activité depuis 12+ mois
- Auditer la distribution des stages de cycle de vie (chercher les goulots d'étranglement)
- Vérifier la précision des données d'enrichissement sur un set d'échantillon

---

## Dashboard de métriques RevOps

### Métriques clés

| Métrique | Formule / Définition | Benchmark |
|--------|---------------------|-----------|
| Taux Lead-to-MQL | MQLs / Total leads | 5-15% |
| Taux MQL-to-SQL | SQLs / MQLs | 30-50% |
| SQL-to-Opportunity | Opportunités / SQLs | 50-70% |
| Pipeline velocity | (# deals x taille moyenne de deal x win rate) / cycle de vente moyen | Varie selon l'ACV |
| CAC | Dépense totale sales + marketing / nouveaux clients | LTV:CAC > 3:1 |
| Ratio LTV:CAC | Customer lifetime value / CAC | 3:1 à 5:1 sain |
| Speed-to-lead | Temps entre form fill et premier contact rep | < 5 minutes idéal |
| Win rate | Closed-won / total opportunités | 20-30% (varie) |

### Structure du dashboard

Construisez trois vues :
1. **Vue marketing** — Volume de leads, taux MQL, attribution source, coût par MQL
2. **Vue sales** — Valeur du pipeline, conversion par stage, velocity, précision du forecast
3. **Vue executive** — CAC, LTV:CAC, revenu vs cible, couverture pipeline

---

## Format de sortie

Quand vous livrez des recommandations RevOps, fournissez :

1. **Document de stages de cycle de vie** — Définitions de stages avec critères d'entrée/sortie, owners et SLAs
2. **Spécification de scoring** — Attributs de fit et engagement avec valeurs en points et seuil MQL
3. **Document de règles de routing** — Arbre de décision avec logique d'assignation et fallbacks
4. **Configuration de pipeline** — Définitions de stages, champs requis et triggers d'automatisation
5. **Spec de dashboard de métriques** — Métriques clés, sources de données et benchmarks cibles

Formatez chacun en document autonome que l'utilisateur peut implémenter directement. Incluez des conseils spécifiques par plateforme quand le CRM est connu.

---

## Questions spécifiques à la tâche

1. Quelle plateforme CRM utilisez-vous (ou prévoyez d'utiliser) ?
2. Combien de leads par mois générez-vous ?
3. Quelle est votre définition actuelle de MQL ?
4. Où les leads se coincent-ils dans votre funnel ?
5. Avez-vous des SLAs entre marketing et sales aujourd'hui ?

---

## Intégrations d'outils

Pour l'implémentation, voir le [registry des outils](../../tools/REGISTRY.md). Outils clés RevOps :

| Outil | Ce qu'il fait | Guide |
|------|-------------|-------|
| **HubSpot** | CRM, marketing automation, lead scoring, workflows | [hubspot.md](../../tools/integrations/hubspot.md) |
| **Salesforce** | CRM enterprise, gestion de pipeline, reporting | [salesforce.md](../../tools/integrations/salesforce.md) |
| **Calendly** | Scheduling de meetings, routing round-robin | [calendly.md](../../tools/integrations/calendly.md) |
| **SavvyCal** | Scheduling avec disponibilité basée priorité | [savvycal.md](../../tools/integrations/savvycal.md) |
| **Clearbit** | Enrichissement temps réel et scoring de leads | [clearbit.md](../../tools/integrations/clearbit.md) |
| **Apollo** | Données de contact, enrichissement et séquences outbound | [apollo.md](../../tools/integrations/apollo.md) |
| **ActiveCampaign** | Marketing automation pour SMBs, lead scoring | [activecampaign.md](../../tools/integrations/activecampaign.md) |
| **Zapier** | Automatisation cross-outils et glue de workflow | [zapier.md](../../tools/integrations/zapier.md) |
| **Introw** | Pipeline issu de partenaires, commissions, deal registration, QBRs | [introw.md](../../tools/integrations/introw.md) |
| **Crossbeam** | Overlaps de comptes partenaires et identification de co-sell | [crossbeam.md](../../tools/integrations/crossbeam.md) |

---

## Skills liés

- **cold-email** : pour les emails de prospection outbound
- **email-sequence** : pour les flux email de cycle de vie et nurture
- **pricing-strategy** : pour les décisions de pricing et packaging
- **analytics-tracking** : pour le tracking des métriques de pipeline et de l'attribution
- **launch-strategy** : pour la planification de lancement go-to-market
- **sales-enablement** : pour les sales collateral, decks et objection handling
