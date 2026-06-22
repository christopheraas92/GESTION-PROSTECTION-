---
name: ui-ux-pro-max
description: "Intelligence design UI/UX pour web et mobile. Inclut 50+ styles, 161 palettes de couleurs, 57 paires de polices, 161 types de produits, 99 règles UX et 25 types de graphiques sur 10 stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui et HTML/CSS). Actions : planifier, construire, créer, concevoir, implémenter, revoir, corriger, améliorer, optimiser, enrichir, refactoriser et auditer du code UI/UX. Projets : site web, landing page, tableau de bord, panneau d'administration, e-commerce, SaaS, portfolio, blog et application mobile. Éléments : bouton, modale, navbar, sidebar, carte, tableau, formulaire et graphique. Styles : glassmorphisme, claymorphisme, minimalisme, brutalisme, neumorphisme, bento grid, mode sombre, responsive, skeuomorphisme et flat design. Sujets : systèmes de couleurs, accessibilité, animation, mise en page, typographie, paires de polices, espacement, états d'interaction, ombre et dégradé. Intégrations : MCP shadcn/ui pour la recherche et les exemples de composants."
---

# UI/UX Pro Max — Intelligence design

Guide design complet pour applications web et mobile. Contient 50+ styles, 161 palettes de couleurs, 57 paires de polices, 161 types de produits avec règles de raisonnement, 99 règles UX et 25 types de graphiques sur 10 stacks technologiques. Base de données interrogeable avec recommandations priorisées.

## Quand l'appliquer

Cette skill doit être utilisée lorsque la tâche concerne **la structure UI, les décisions de design visuel, les patterns d'interaction ou le contrôle qualité de l'expérience utilisateur**.

### À utiliser obligatoirement

Cette skill doit être invoquée dans les situations suivantes :

- Concevoir de nouvelles pages (Landing Page, Tableau de bord, Admin, SaaS, App mobile)
- Créer ou refactoriser des composants UI (boutons, modales, formulaires, tableaux, graphiques, etc.)
- Choisir des schémas de couleurs, systèmes typographiques, standards d'espacement ou systèmes de mise en page
- Réviser le code UI pour l'expérience utilisateur, l'accessibilité ou la cohérence visuelle
- Implémenter les structures de navigation, animations ou comportements responsives
- Prendre des décisions de design au niveau produit (style, hiérarchie de l'information, expression de marque)
- Améliorer la qualité perçue, la clarté ou l'utilisabilité des interfaces

### Recommandé

Cette skill est recommandée dans les situations suivantes :

- L'UI semble « pas assez professionnelle » mais la raison est floue
- Recevoir des retours sur l'utilisabilité ou l'expérience
- Optimisation qualité UI avant lancement
- Aligner le design multi-plateforme (Web / iOS / Android)
- Bâtir des design systems ou des bibliothèques de composants réutilisables

### À ignorer

Cette skill n'est pas nécessaire dans les situations suivantes :

- Développement de logique backend pure
- Conception d'API ou base de données uniquement
- Optimisation de performance sans rapport avec l'interface
- Travail d'infrastructure ou DevOps
- Scripts non visuels ou tâches d'automatisation

**Critère de décision :** Si la tâche modifie la façon dont une fonctionnalité **est vue, ressentie, animée ou utilisée**, cette skill doit être utilisée.

## Catégories de règles par priorité

*Référence humain/IA : suivre la priorité 1→10 pour décider sur quelle catégorie de règle se concentrer en premier ; utiliser `--domain <Domaine>` pour interroger les détails au besoin. Les scripts ne lisent pas ce tableau.*

| Priorité | Catégorie | Impact | Domaine | Contrôles clés (obligatoires) | Anti-patterns (à éviter) |
|----------|-----------|--------|---------|-------------------------------|---------------------------|
| 1 | Accessibilité | CRITIQUE | `ux` | Contraste 4.5:1, texte alt, navigation clavier, aria-labels | Suppression des focus rings, boutons icône seule sans label |
| 2 | Touch & Interaction | CRITIQUE | `ux` | Taille min 44×44 px, espacement 8 px+, retour de chargement | Dépendance au hover seul, changements d'état instantanés (0 ms) |
| 3 | Performance | ÉLEVÉ | `ux` | WebP/AVIF, lazy loading, réserver l'espace (CLS &lt; 0.1) | Layout thrashing, Cumulative Layout Shift |
| 4 | Sélection de style | ÉLEVÉ | `style`, `product` | Adapter au type de produit, cohérence, icônes SVG (pas d'emoji) | Mélanger flat et skeuomorphique aléatoirement, emojis comme icônes |
| 5 | Mise en page & Responsive | ÉLEVÉ | `ux` | Breakpoints mobile-first, meta viewport, pas de scroll horizontal | Scroll horizontal, largeurs de conteneur en px fixes, désactiver le zoom |
| 6 | Typographie & Couleur | MOYEN | `typography`, `color` | Base 16 px, line-height 1.5, tokens de couleur sémantiques | Texte corps &lt; 12 px, gris sur gris, hex brut dans les composants |
| 7 | Animation | MOYEN | `ux` | Durée 150–300 ms, mouvement porteur de sens, continuité spatiale | Animation purement décorative, animer width/height, pas de reduced-motion |
| 8 | Formulaires & Retours | MOYEN | `ux` | Labels visibles, erreur près du champ, texte d'aide, divulgation progressive | Label en placeholder seul, erreurs uniquement en haut, surcharge initiale |
| 9 | Patterns de navigation | ÉLEVÉ | `ux` | Retour prévisible, nav bas ≤5, deep linking | Nav surchargée, retour cassé, pas de deep links |
| 10 | Graphiques & Données | FAIBLE | `chart` | Légendes, infobulles, couleurs accessibles | Reposer sur la couleur seule pour transmettre le sens |

## Référence rapide

### 1. Accessibilité (CRITIQUE)

- `color-contrast` — Ratio minimum 4.5:1 pour texte normal (texte large 3:1) ; Material Design
- `focus-states` — Anneaux de focus visibles sur les éléments interactifs (2–4 px ; Apple HIG, MD)
- `alt-text` — Texte alt descriptif pour les images significatives
- `aria-labels` — aria-label pour les boutons icône seule ; accessibilityLabel en natif (Apple HIG)
- `keyboard-nav` — Ordre de tabulation conforme à l'ordre visuel ; support clavier complet (Apple HIG)
- `form-labels` — Utiliser label avec attribut for
- `skip-links` — « Skip to main content » pour les utilisateurs clavier
- `heading-hierarchy` — h1→h6 séquentiel, pas de saut de niveau
- `color-not-only` — Ne pas véhiculer l'info par la couleur seule (ajouter icône/texte)
- `dynamic-type` — Supporter la mise à l'échelle du texte système ; éviter la troncature à mesure que le texte grandit (Apple Dynamic Type, MD)
- `reduced-motion` — Respecter prefers-reduced-motion ; réduire/désactiver les animations sur demande (Apple Reduced Motion API, MD)
- `voiceover-sr` — accessibilityLabel/accessibilityHint significatifs ; ordre de lecture logique pour VoiceOver/lecteurs d'écran (Apple HIG, MD)
- `escape-routes` — Fournir annuler/retour dans les modales et flux multi-étapes (Apple HIG)
- `keyboard-shortcuts` — Préserver les raccourcis système et a11y ; offrir des alternatives clavier au drag-and-drop (Apple HIG)

### 2. Touch & Interaction (CRITIQUE)

- `touch-target-size` — Min 44×44 pt (Apple) / 48×48 dp (Material) ; étendre la zone d'impact au-delà des bornes visuelles si besoin
- `touch-spacing` — Espacement minimum 8 px/8 dp entre cibles tactiles (Apple HIG, MD)
- `hover-vs-tap` — Utiliser clic/tap pour les interactions principales ; ne pas dépendre du hover seul
- `loading-buttons` — Désactiver le bouton durant les opérations async ; afficher spinner ou progression
- `error-feedback` — Messages d'erreur clairs près du problème
- `cursor-pointer` — Ajouter cursor-pointer aux éléments cliquables (Web)
- `gesture-conflicts` — Éviter le swipe horizontal sur le contenu principal ; préférer le scroll vertical
- `tap-delay` — Utiliser touch-action: manipulation pour réduire le délai de 300 ms (Web)
- `standard-gestures` — Utiliser les gestes standards de la plateforme de manière cohérente ; ne pas redéfinir (swipe-back, pinch-zoom) (Apple HIG)
- `system-gestures` — Ne pas bloquer les gestes système (Centre de contrôle, swipe retour, etc.) (Apple HIG)
- `press-feedback` — Retour visuel à l'appui (ripple/highlight ; couches d'état MD)
- `haptic-feedback` — Utiliser le haptique pour les confirmations et actions importantes ; éviter la surutilisation (Apple HIG)
- `gesture-alternative` — Ne pas dépendre d'interactions uniquement par geste ; toujours fournir des contrôles visibles pour les actions critiques
- `safe-area-awareness` — Garder les cibles tactiles principales à l'écart du notch, Dynamic Island, barre de geste et bords d'écran
- `no-precision-required` — Éviter d'exiger des taps au pixel près sur de petites icônes ou bords fins
- `swipe-clarity` — Les actions de swipe doivent montrer une affordance claire (chevron, label, tutoriel)
- `drag-threshold` — Utiliser un seuil de mouvement avant de démarrer le drag pour éviter les drags accidentels

### 3. Performance (ÉLEVÉ)

- `image-optimization` — Utiliser WebP/AVIF, images responsives (srcset/sizes), lazy load des assets non critiques
- `image-dimension` — Déclarer width/height ou utiliser aspect-ratio pour empêcher le shift de mise en page (Core Web Vitals : CLS)
- `font-loading` — Utiliser font-display: swap/optional pour éviter le texte invisible (FOIT) ; réserver l'espace pour réduire le layout shift (MD)
- `font-preload` — Précharger uniquement les polices critiques ; éviter d'utiliser preload sur chaque variante
- `critical-css` — Prioriser le CSS au-dessus de la ligne de flottaison (CSS critique inline ou feuille chargée tôt)
- `lazy-loading` — Lazy load des composants non-hero via import dynamique / découpage par route
- `bundle-splitting` — Découper le code par route/fonctionnalité (React Suspense / Next.js dynamic) pour réduire la charge initiale et le TTI
- `third-party-scripts` — Charger les scripts tiers async/defer ; auditer et retirer les inutiles (MD)
- `reduce-reflows` — Éviter les lectures/écritures de mise en page fréquentes ; regrouper les lectures DOM puis les écritures
- `content-jumping` — Réserver l'espace pour le contenu async pour éviter les sauts de mise en page (Core Web Vitals : CLS)
- `lazy-load-below-fold` — Utiliser loading="lazy" pour les images sous la ligne de flottaison et médias lourds
- `virtualize-lists` — Virtualiser les listes de 50+ éléments pour améliorer l'efficacité mémoire et la performance de scroll
- `main-thread-budget` — Garder le travail par frame sous ~16 ms pour 60 fps ; déplacer les tâches lourdes hors du main thread (HIG, MD)
- `progressive-loading` — Utiliser skeleton screens / shimmer au lieu de spinners bloquants longs pour les opérations >1 s (Apple HIG)
- `input-latency` — Garder la latence d'entrée sous ~100 ms pour taps/scrolls (standard de réactivité Material)
- `tap-feedback-speed` — Fournir un retour visuel dans les 100 ms suivant le tap (Apple HIG)
- `debounce-throttle` — Utiliser debounce/throttle pour les événements à haute fréquence (scroll, resize, input)
- `offline-support` — Fournir des messages d'état hors ligne et un fallback de base (PWA / mobile)
- `network-fallback` — Offrir des modes dégradés pour réseaux lents (images plus basse résolution, moins d'animations)

### 4. Sélection de style (ÉLEVÉ)

- `style-match` — Adapter le style au type de produit (utiliser `--design-system` pour les recommandations)
- `consistency` — Utiliser le même style sur toutes les pages
- `no-emoji-icons` — Utiliser des icônes SVG (Heroicons, Lucide), pas d'emojis
- `color-palette-from-product` — Choisir la palette en fonction du produit/industrie (chercher `--domain color`)
- `effects-match-style` — Ombres, flou, rayon alignés au style choisi (glass / flat / clay etc.)
- `platform-adaptive` — Respecter les idiomes de la plateforme (iOS HIG vs Material) : navigation, contrôles, typographie, mouvement
- `state-clarity` — Rendre les états hover/pressed/disabled visuellement distincts tout en restant dans le style (couches d'état Material)
- `elevation-consistent` — Utiliser une échelle d'élévation/ombre cohérente pour cartes, sheets, modales ; éviter les valeurs d'ombre aléatoires
- `dark-mode-pairing` — Concevoir les variantes claire/sombre ensemble pour garder marque, contraste et style cohérents
- `icon-style-consistent` — Utiliser un seul jeu d'icônes/langage visuel (épaisseur de trait, rayon) à travers le produit
- `system-controls` — Préférer les contrôles natifs/système aux entièrement personnalisés ; personnaliser uniquement quand la marque l'exige (Apple HIG)
- `blur-purpose` — Utiliser le flou pour indiquer une dismissal de fond (modales, sheets), pas comme décoration (Apple HIG)
- `primary-action` — Chaque écran ne doit avoir qu'un CTA principal ; les actions secondaires visuellement subordonnées (Apple HIG)

### 5. Mise en page & Responsive (ÉLEVÉ)

- `viewport-meta` — width=device-width initial-scale=1 (ne jamais désactiver le zoom)
- `mobile-first` — Concevoir mobile-first, puis monter en tablette et bureau
- `breakpoint-consistency` — Utiliser des breakpoints systématiques (ex : 375 / 768 / 1024 / 1440)
- `readable-font-size` — Texte corps min 16 px sur mobile (évite l'auto-zoom iOS)
- `line-length-control` — Mobile 35–60 caractères par ligne ; bureau 60–75 caractères
- `horizontal-scroll` — Pas de scroll horizontal sur mobile ; s'assurer que le contenu tient dans la largeur du viewport
- `spacing-scale` — Utiliser un système d'espacement incrémental 4 pt/8 dp (Material Design)
- `touch-density` — Garder un espacement de composants confortable au toucher : ni serré, ni source de mis-taps
- `container-width` — Max-width cohérent sur bureau (max-w-6xl / 7xl)
- `z-index-management` — Définir une échelle de z-index par couche (0 / 10 / 20 / 40 / 100 / 1000)
- `fixed-element-offset` — La navbar/barre du bas fixe doit réserver un padding sûr pour le contenu sous-jacent
- `scroll-behavior` — Éviter les régions de scroll imbriquées qui perturbent l'expérience principale de scroll
- `viewport-units` — Préférer min-h-dvh à 100vh sur mobile
- `orientation-support` — Garder la mise en page lisible et utilisable en paysage
- `content-priority` — Montrer le contenu central en premier sur mobile ; replier ou cacher le secondaire
- `visual-hierarchy` — Établir la hiérarchie par la taille, l'espacement, le contraste — pas la couleur seule

### 6. Typographie & Couleur (MOYEN)

- `line-height` — Utiliser 1.5-1.75 pour le texte corps
- `line-length` — Limiter à 65-75 caractères par ligne
- `font-pairing` — Faire correspondre les personnalités des polices titre/corps
- `font-scale` — Échelle typographique cohérente (ex : 12 14 16 18 24 32)
- `contrast-readability` — Texte plus sombre sur fonds clairs (ex : slate-900 sur blanc)
- `text-styles-system` — Utiliser le système typographique de la plateforme : styles iOS 11 Dynamic Type / rôles Material 5 (display, headline, title, body, label) (HIG, MD)
- `weight-hierarchy` — Utiliser la graisse pour renforcer la hiérarchie : titres gras (600–700), corps regular (400), labels medium (500) (MD)
- `color-semantic` — Définir des tokens de couleur sémantiques (primary, secondary, error, surface, on-surface), pas de hex brut dans les composants (système de couleurs Material)
- `color-dark-mode` — Le mode sombre utilise des variantes tonales désaturées/plus claires, pas des couleurs inversées ; tester le contraste séparément (HIG, MD)
- `color-accessible-pairs` — Les paires premier-plan/fond doivent atteindre 4.5:1 (AA) ou 7:1 (AAA) ; utiliser des outils pour vérifier (WCAG, MD)
- `color-not-decorative-only` — Les couleurs fonctionnelles (rouge erreur, vert succès) doivent inclure icône/texte ; éviter le sens uniquement par couleur (HIG, MD)
- `truncation-strategy` — Préférer le retour à la ligne à la troncature ; en cas de troncature utiliser des points de suspension et fournir le texte complet via tooltip/expand (Apple HIG)
- `letter-spacing` — Respecter le letter-spacing par défaut de la plateforme ; éviter un tracking serré sur le texte corps (HIG, MD)
- `number-tabular` — Utiliser des chiffres tabulaires/monospace pour les colonnes de données, prix et timers afin d'éviter le shift de mise en page
- `whitespace-balance` — Utiliser le blanc intentionnellement pour regrouper les éléments liés et séparer les sections ; éviter l'encombrement visuel (Apple HIG)

### 7. Animation (MOYEN)

- `duration-timing` — Utiliser 150–300 ms pour les micro-interactions ; transitions complexes ≤400 ms ; éviter >500 ms (MD)
- `transform-performance` — Utiliser transform/opacity uniquement ; éviter d'animer width/height/top/left
- `loading-states` — Afficher un skeleton ou indicateur de progression quand le chargement dépasse 300 ms
- `excessive-motion` — Animer 1-2 éléments clés par vue au maximum
- `easing` — Utiliser ease-out à l'entrée, ease-in à la sortie ; éviter linear pour les transitions UI
- `motion-meaning` — Chaque animation doit exprimer une relation cause-effet, pas seulement décorer (Apple HIG)
- `state-transition` — Les changements d'état (hover / active / expanded / collapsed / modal) doivent s'animer en douceur, pas claquer
- `continuity` — Les transitions de page/écran doivent maintenir la continuité spatiale (élément partagé, slide directionnel) (Apple HIG)
- `parallax-subtle` — Utiliser la parallaxe avec parcimonie ; doit respecter reduced-motion et ne pas désorienter (Apple HIG)
- `spring-physics` — Préférer les courbes spring/physiques aux linéaires ou cubic-bezier pour un ressenti naturel (animations fluides Apple HIG)
- `exit-faster-than-enter` — Animations de sortie plus courtes que l'entrée (~60–70 % de la durée d'entrée) pour paraître réactif (MD motion)
- `stagger-sequence` — Décaler l'entrée des items de liste/grille de 30–50 ms par item ; éviter le « tout d'un coup » ou les révélations trop lentes (MD)
- `shared-element-transition` — Utiliser des transitions d'élément partagé / hero pour la continuité visuelle entre écrans (MD, HIG)
- `interruptible` — Les animations doivent être interruptibles ; tap/geste utilisateur annule immédiatement l'animation en cours (Apple HIG)
- `no-blocking-animation` — Ne jamais bloquer l'entrée utilisateur durant une animation ; l'UI doit rester interactive (Apple HIG)
- `fade-crossfade` — Utiliser le crossfade pour le remplacement de contenu dans le même conteneur (MD)
- `scale-feedback` — Légère mise à l'échelle (0.95–1.05) à l'appui pour cartes/boutons tappables ; restaurer au relâchement (HIG, MD)
- `gesture-feedback` — Drag, swipe et pinch doivent fournir une réponse visuelle en temps réel suivant le doigt (MD Motion)
- `hierarchy-motion` — Utiliser la direction translate/scale pour exprimer la hiérarchie : entrer par le bas = plus profond, sortir vers le haut = retour (MD)
- `motion-consistency` — Unifier les tokens de durée/easing globalement ; toutes les animations partagent le même rythme et ressenti
- `opacity-threshold` — Les éléments en fondu ne doivent pas s'attarder sous 0.2 d'opacité ; soit fondre complètement, soit rester visibles
- `modal-motion` — Modales/sheets doivent s'animer depuis leur source de déclenchement (scale+fade ou slide-in) pour le contexte spatial (HIG, MD)
- `navigation-direction` — La navigation avant s'anime vers la gauche/haut ; la navigation arrière vers la droite/bas — garder la direction logiquement cohérente (HIG)
- `layout-shift-avoid` — Les animations ne doivent pas provoquer de reflow ou CLS ; utiliser transform pour les changements de position

### 8. Formulaires & Retours (MOYEN)

- `input-labels` — Label visible par champ (pas seulement placeholder)
- `error-placement` — Afficher l'erreur sous le champ concerné
- `submit-feedback` — État chargement puis succès/erreur à la soumission
- `required-indicators` — Marquer les champs obligatoires (astérisque)
- `empty-states` — Message utile et action quand pas de contenu
- `toast-dismiss` — Auto-fermeture des toasts en 3-5 s
- `confirmation-dialogs` — Confirmer avant les actions destructives
- `input-helper-text` — Fournir un texte d'aide persistant sous les inputs complexes, pas juste un placeholder (Material Design)
- `disabled-states` — Les éléments désactivés utilisent une opacité réduite (0.38–0.5) + changement de curseur + attribut sémantique (MD)
- `progressive-disclosure` — Révéler les options complexes progressivement ; ne pas submerger l'utilisateur d'emblée (Apple HIG)
- `inline-validation` — Valider au blur (pas à chaque frappe) ; afficher l'erreur après que l'utilisateur ait fini la saisie (MD)
- `input-type-keyboard` — Utiliser des types d'input sémantiques (email, tel, number) pour déclencher le bon clavier mobile (HIG, MD)
- `password-toggle` — Fournir un bouton afficher/masquer pour les champs mot de passe (MD)
- `autofill-support` — Utiliser les attributs autocomplete / textContentType pour que le système puisse autoremplir (HIG, MD)
- `undo-support` — Autoriser l'annulation pour les actions destructives ou de masse (ex : toast « Annuler la suppression ») (Apple HIG)
- `success-feedback` — Confirmer les actions terminées avec un bref retour visuel (coche, toast, flash de couleur) (MD)
- `error-recovery` — Les messages d'erreur doivent inclure un chemin de récupération clair (réessayer, modifier, aide) (HIG, MD)
- `multi-step-progress` — Les flux multi-étapes montrent un indicateur d'étape ou barre de progression ; autoriser la navigation arrière (MD)
- `form-autosave` — Les longs formulaires doivent auto-sauvegarder les brouillons pour éviter la perte de données en cas de fermeture accidentelle (Apple HIG)
- `sheet-dismiss-confirm` — Confirmer avant de fermer une sheet/modale avec des changements non sauvegardés (Apple HIG)
- `error-clarity` — Les messages d'erreur doivent indiquer la cause + comment corriger (pas juste « Entrée invalide ») (HIG, MD)
- `field-grouping` — Regrouper les champs liés logiquement (fieldset/legend ou regroupement visuel) (MD)
- `read-only-distinction` — L'état lecture seule doit être visuellement et sémantiquement différent de désactivé (MD)
- `focus-management` — Après une erreur de soumission, focus automatiquement le premier champ invalide (WCAG, MD)
- `error-summary` — Pour de multiples erreurs, afficher un résumé en haut avec ancres vers chaque champ (WCAG)
- `touch-friendly-input` — Hauteur d'input mobile ≥44 px pour satisfaire les exigences de cible tactile (Apple HIG)
- `destructive-emphasis` — Les actions destructives utilisent une couleur de danger sémantique (rouge) et sont visuellement séparées des actions principales (HIG, MD)
- `toast-accessibility` — Les toasts ne doivent pas voler le focus ; utiliser aria-live="polite" pour l'annonce aux lecteurs d'écran (WCAG)
- `aria-live-errors` — Les erreurs de formulaire utilisent aria-live ou role="alert" pour notifier les lecteurs d'écran (WCAG)
- `contrast-feedback` — Les couleurs d'état erreur et succès doivent atteindre un ratio de contraste 4.5:1 (WCAG, MD)
- `timeout-feedback` — Le timeout de requête doit afficher un retour clair avec option de réessai (MD)

### 9. Patterns de navigation (ÉLEVÉ)

- `bottom-nav-limit` — Navigation du bas : 5 items max ; utiliser des labels avec icônes (Material Design)
- `drawer-usage` — Utiliser drawer/sidebar pour la navigation secondaire, pas les actions principales (Material Design)
- `back-behavior` — La navigation arrière doit être prévisible et cohérente ; préserver scroll/état (Apple HIG, MD)
- `deep-linking` — Tous les écrans clés doivent être atteignables via deep link / URL pour le partage et notifications (Apple HIG, MD)
- `tab-bar-ios` — iOS : utiliser la Tab Bar du bas pour la navigation de niveau supérieur (Apple HIG)
- `top-app-bar-android` — Android : utiliser la Top App Bar avec icône de navigation pour la structure principale (Material Design)
- `nav-label-icon` — Les items de navigation doivent avoir à la fois icône et label texte ; la nav icône seule nuit à la découvrabilité (MD)
- `nav-state-active` — La position courante doit être visuellement mise en évidence (couleur, graisse, indicateur) dans la navigation (HIG, MD)
- `nav-hierarchy` — La nav primaire (tabs/barre du bas) vs nav secondaire (drawer/paramètres) doit être clairement séparée (MD)
- `modal-escape` — Modales et sheets doivent offrir une affordance claire de fermeture ; swipe vers le bas pour fermer sur mobile (Apple HIG)
- `search-accessible` — La recherche doit être facilement accessible (barre du haut ou onglet) ; fournir requêtes récentes/suggérées (MD)
- `breadcrumb-web` — Web : utiliser les breadcrumbs pour les hiérarchies à 3+ niveaux pour aider à l'orientation (MD)
- `state-preservation` — Le retour en arrière doit restaurer la position de scroll, l'état des filtres et la saisie (HIG, MD)
- `gesture-nav-support` — Supporter la navigation par geste système (swipe-back iOS, retour prédictif Android) sans conflit (HIG, MD)
- `tab-badge` — Utiliser des badges sur les items de nav avec parcimonie pour indiquer non lu/en attente ; effacer après visite (HIG, MD)
- `overflow-menu` — Quand les actions dépassent l'espace disponible, utiliser un menu overflow/plus au lieu d'entasser (MD)
- `bottom-nav-top-level` — La nav du bas est uniquement pour les écrans de niveau supérieur ; ne jamais imbriquer une sous-navigation dedans (MD)
- `adaptive-navigation` — Grands écrans (≥1024 px) préfèrent la sidebar ; petits écrans utilisent nav bas/haut (Material Adaptive)
- `back-stack-integrity` — Ne jamais réinitialiser silencieusement la pile de navigation ni sauter au home de manière inattendue (HIG, MD)
- `navigation-consistency` — Le placement de la navigation doit rester identique sur toutes les pages ; ne pas le changer par type de page
- `avoid-mixed-patterns` — Ne pas mélanger Tab + Sidebar + Nav du bas au même niveau hiérarchique
- `modal-vs-navigation` — Les modales ne doivent pas être utilisées pour les flux de navigation principaux ; elles brisent le chemin de l'utilisateur (HIG)
- `focus-on-route-change` — Après une transition de page, déplacer le focus vers la région de contenu principal pour les lecteurs d'écran (WCAG)
- `persistent-nav` — La navigation centrale doit rester accessible depuis les pages profondes ; ne pas la cacher entièrement dans les sous-flux (HIG, MD)
- `destructive-nav-separation` — Les actions dangereuses (supprimer compte, déconnexion) doivent être visuellement et spatialement séparées des items de nav normaux (HIG, MD)
- `empty-nav-state` — Quand une destination de nav est indisponible, expliquer pourquoi au lieu de la cacher silencieusement (MD)

### 10. Graphiques & Données (FAIBLE)

- `chart-type` — Adapter le type de graphique au type de données (tendance → ligne, comparaison → barres, proportion → camembert/donut)
- `color-guidance` — Utiliser des palettes de couleurs accessibles ; éviter les paires rouge/vert uniquement pour les utilisateurs daltoniens (WCAG, MD)
- `data-table` — Fournir une alternative en tableau pour l'accessibilité ; les graphiques seuls ne sont pas compatibles lecteurs d'écran (WCAG)
- `pattern-texture` — Compléter la couleur avec motifs, textures ou formes pour que les données soient distinguables sans couleur (WCAG, MD)
- `legend-visible` — Toujours afficher la légende ; la positionner près du graphique, pas détachée sous une ligne de flottaison (MD)
- `tooltip-on-interact` — Fournir des infobulles/étiquettes de données au survol (Web) ou au tap (mobile) montrant les valeurs exactes (HIG, MD)
- `axis-labels` — Étiqueter les axes avec unités et échelle lisible ; éviter les étiquettes tronquées ou pivotées sur mobile
- `responsive-chart` — Les graphiques doivent se réorganiser ou se simplifier sur petits écrans (ex : barres horizontales au lieu de verticales, moins de graduations)
- `empty-data-state` — Afficher un état vide significatif quand pas de données (« Pas encore de données » + guidance), pas un graphique vide (MD)
- `loading-chart` — Utiliser un placeholder skeleton ou shimmer pendant le chargement des données ; ne pas montrer un cadre d'axe vide
- `animation-optional` — Les animations d'entrée de graphique doivent respecter prefers-reduced-motion ; les données doivent être lisibles immédiatement (HIG)
- `large-dataset` — Pour 1000+ points de données, agréger ou échantillonner ; fournir un drill-down pour le détail au lieu de tout rendre (MD)
- `number-formatting` — Utiliser un formatage localisé pour les nombres, dates, devises sur les axes et étiquettes (HIG, MD)
- `touch-target-chart` — Les éléments interactifs du graphique (points, segments) doivent avoir une zone tap ≥44 pt ou s'étendre au toucher (Apple HIG)
- `no-pie-overuse` — Éviter le camembert/donut pour >5 catégories ; passer aux barres pour la clarté
- `contrast-data` — Lignes/barres de données vs fond ≥3:1 ; étiquettes de texte de données ≥4.5:1 (WCAG)
- `legend-interactive` — Les légendes doivent être cliquables pour basculer la visibilité des séries (MD)
- `direct-labeling` — Pour les petits jeux de données, étiqueter les valeurs directement sur le graphique pour réduire le déplacement du regard
- `tooltip-keyboard` — Le contenu des infobulles doit être atteignable au clavier et ne pas reposer sur le hover seul (WCAG)
- `sortable-table` — Les tableaux de données doivent supporter le tri avec aria-sort indiquant l'état de tri courant (WCAG)
- `axis-readability` — Les graduations d'axe ne doivent pas être serrées ; maintenir un espacement lisible, auto-skip sur petits écrans
- `data-density` — Limiter la densité d'information par graphique pour éviter la surcharge cognitive ; découper en plusieurs graphiques au besoin
- `trend-emphasis` — Mettre l'accent sur les tendances plutôt que la décoration ; éviter les dégradés/ombres lourds qui masquent les données
- `gridline-subtle` — Les lignes de grille doivent être à faible contraste (ex : gray-200) pour ne pas concurrencer les données
- `focusable-elements` — Les éléments interactifs du graphique (points, barres, parts) doivent être navigables au clavier (WCAG)
- `screen-reader-summary` — Fournir un résumé texte ou aria-label décrivant l'insight clé du graphique pour les lecteurs d'écran (WCAG)
- `error-state-chart` — Un échec de chargement des données doit afficher un message d'erreur avec action de réessai, pas un graphique cassé/vide
- `export-option` — Pour les produits riches en données, offrir l'export CSV/image des données du graphique
- `drill-down-consistency` — Les interactions de drill-down doivent maintenir un chemin de retour clair et un fil d'Ariane hiérarchique
- `time-scale-clarity` — Les graphiques de séries temporelles doivent clairement étiqueter la granularité (jour/semaine/mois) et permettre la bascule

## Comment utiliser

Chercher des domaines spécifiques avec l'outil CLI ci-dessous.

---

## Prérequis

Vérifier si Python est installé :

```bash
python3 --version || python --version
```

Si Python n'est pas installé, l'installer selon l'OS de l'utilisateur :

**macOS :**
```bash
brew install python3
```

**Ubuntu/Debian :**
```bash
sudo apt update && sudo apt install python3
```

**Windows :**
```powershell
winget install Python.Python.3.12
```

---

## Comment utiliser cette skill

Utiliser cette skill quand l'utilisateur demande l'une des choses suivantes :

| Scénario | Exemples de déclenchement | Démarrer à |
|----------|---------------------------|------------|
| **Nouveau projet / page** | « Construis une landing page », « Construis un tableau de bord » | Étape 1 → Étape 2 (design system) |
| **Nouveau composant** | « Crée une carte de tarif », « Ajoute une modale » | Étape 3 (recherche par domaine : style, ux) |
| **Choisir style / couleur / police** | « Quel style convient à une app fintech ? », « Recommande une palette » | Étape 2 (design system) |
| **Revoir une UI existante** | « Revois cette page pour les problèmes UX », « Vérifie l'accessibilité » | Checklist Référence rapide ci-dessus |
| **Corriger un bug UI** | « Le hover du bouton est cassé », « Le layout shifte au chargement » | Référence rapide → section pertinente |
| **Améliorer / optimiser** | « Rends ceci plus rapide », « Améliore l'expérience mobile » | Étape 3 (domaine : ux, react) |
| **Implémenter le mode sombre** | « Ajoute le support du mode sombre » | Étape 3 (domaine : style « dark mode ») |
| **Ajouter graphiques / dataviz** | « Ajoute un graphique de dashboard analytique » | Étape 3 (domaine : chart) |
| **Bonnes pratiques de stack** | « Astuces de perf React », « Navigation SwiftUI » | Étape 4 (recherche par stack) |

Suivre ce workflow :

### Étape 1 : Analyser les besoins utilisateur

Extraire les informations clés de la demande :
- **Type de produit** : Divertissement (social, vidéo, musique, gaming), Outil (scanner, éditeur, convertisseur), Productivité (gestionnaire de tâches, notes, calendrier), ou hybride
- **Audience cible** : utilisateurs C-end ; considérer la tranche d'âge, le contexte d'usage (transport, loisir, travail)
- **Mots-clés de style** : ludique, vibrant, minimal, mode sombre, content-first, immersif, etc.
- **Stack** : React Native (seul stack technique de ce projet)

### Étape 2 : Générer le design system (OBLIGATOIRE)

**Toujours commencer par `--design-system`** pour obtenir des recommandations complètes avec raisonnement :

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<type_produit> <industrie> <mots-clés>" --design-system [-p "Nom du projet"]
```

Cette commande :
1. Cherche les domaines en parallèle (product, style, color, landing, typography)
2. Applique les règles de raisonnement de `ui-reasoning.csv` pour sélectionner les meilleurs matchs
3. Retourne un design system complet : pattern, style, couleurs, typographie, effets
4. Inclut les anti-patterns à éviter

**Exemple :**
```bash
python3 skills/ui-ux-pro-max/scripts/search.py "beauty spa wellness service" --design-system -p "Serenity Spa"
```

### Étape 2b : Persister le design system (pattern Master + Overrides)

Pour sauvegarder le design system pour **une récupération hiérarchique entre sessions**, ajouter `--persist` :

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<requête>" --design-system --persist -p "Nom du projet"
```

Cela crée :
- `design-system/MASTER.md` — Source de vérité globale avec toutes les règles de design
- `design-system/pages/` — Dossier pour les overrides spécifiques aux pages

**Avec override spécifique à une page :**
```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<requête>" --design-system --persist -p "Nom du projet" --page "dashboard"
```

Cela crée aussi :
- `design-system/pages/dashboard.md` — Déviations spécifiques à la page par rapport au Master

**Comment fonctionne la récupération hiérarchique :**
1. Lors de la construction d'une page spécifique (ex : « Checkout »), vérifier d'abord `design-system/pages/checkout.md`
2. Si le fichier de page existe, ses règles **remplacent** le fichier Master
3. Sinon, utiliser `design-system/MASTER.md` exclusivement

**Prompt de récupération contextuelle :**
```
Je construis la page [Nom de page]. Lis design-system/MASTER.md.
Vérifie aussi si design-system/pages/[nom-page].md existe.
Si le fichier de page existe, priorise ses règles.
Sinon, utilise les règles Master exclusivement.
Maintenant, génère le code...
```

### Étape 3 : Compléter avec des recherches détaillées (selon besoin)

Après avoir obtenu le design system, utiliser les recherches par domaine pour des détails additionnels :

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<mot-clé>" --domain <domaine> [-n <max_résultats>]
```

**Quand utiliser les recherches détaillées :**

| Besoin | Domaine | Exemple |
|--------|---------|---------|
| Patterns de type de produit | `product` | `--domain product "entertainment social"` |
| Plus d'options de style | `style` | `--domain style "glassmorphism dark"` |
| Palettes de couleurs | `color` | `--domain color "entertainment vibrant"` |
| Paires de polices | `typography` | `--domain typography "playful modern"` |
| Recommandations de graphiques | `chart` | `--domain chart "real-time dashboard"` |
| Bonnes pratiques UX | `ux` | `--domain ux "animation accessibility"` |
| Polices alternatives | `typography` | `--domain typography "elegant luxury"` |
| Google Fonts individuelles | `google-fonts` | `--domain google-fonts "sans serif popular variable"` |
| Structure de landing | `landing` | `--domain landing "hero social-proof"` |
| Perf React Native | `react` | `--domain react "rerender memo list"` |
| A11y d'interface d'app | `web` | `--domain web "accessibilityLabel touch safe-areas"` |
| Prompts IA / mots-clés CSS | `prompt` | `--domain prompt "minimalism"` |

### Étape 4 : Guides de stack (React Native)

Obtenir les bonnes pratiques spécifiques à React Native :

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<mot-clé>" --stack react-native
```

---

## Référence de recherche

### Domaines disponibles

| Domaine | À utiliser pour | Exemples de mots-clés |
|---------|-----------------|------------------------|
| `product` | Recommandations par type de produit | SaaS, e-commerce, portfolio, healthcare, beauty, service |
| `style` | Styles UI, couleurs, effets | glassmorphism, minimalism, dark mode, brutalism |
| `typography` | Paires de polices, Google Fonts | elegant, playful, professional, modern |
| `color` | Palettes par type de produit | saas, ecommerce, healthcare, beauty, fintech, service |
| `landing` | Structure de page, stratégies CTA | hero, hero-centric, testimonial, pricing, social-proof |
| `chart` | Types de graphiques, recommandations de bibliothèques | trend, comparison, timeline, funnel, pie |
| `ux` | Bonnes pratiques, anti-patterns | animation, accessibility, z-index, loading |
| `google-fonts` | Recherche de Google Fonts individuelles | sans serif, monospace, japanese, variable font, popular |
| `react` | Performance React/Next.js | waterfall, bundle, suspense, memo, rerender, cache |
| `web` | Guidelines d'interface d'app (iOS/Android/React Native) | accessibilityLabel, touch targets, safe areas, Dynamic Type |
| `prompt` | Prompts IA, mots-clés CSS | (nom de style) |

### Stacks disponibles

| Stack | Focus |
|-------|-------|
| `react-native` | Composants, Navigation, Listes |

---

## Exemple de workflow

**Demande utilisateur :** « Fais une page d'accueil de recherche IA. »

### Étape 1 : Analyser les besoins
- Type de produit : Outil (moteur de recherche IA)
- Audience cible : utilisateurs C-end cherchant une recherche rapide et intelligente
- Mots-clés de style : moderne, minimal, content-first, mode sombre
- Stack : React Native

### Étape 2 : Générer le design system (OBLIGATOIRE)

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "AI search tool modern minimal" --design-system -p "AI Search"
```

**Sortie :** design system complet avec pattern, style, couleurs, typographie, effets et anti-patterns.

### Étape 3 : Compléter avec des recherches détaillées (selon besoin)

```bash
# Obtenir les options de style pour un produit outil moderne
python3 skills/ui-ux-pro-max/scripts/search.py "minimalism dark mode" --domain style

# Obtenir les bonnes pratiques UX pour l'interaction de recherche et le chargement
python3 skills/ui-ux-pro-max/scripts/search.py "search loading animation" --domain ux
```

### Étape 4 : Guides de stack

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "list performance navigation" --stack react-native
```

**Puis :** Synthétiser design system + recherches détaillées et implémenter le design.

---

## Formats de sortie

Le flag `--design-system` supporte deux formats de sortie :

```bash
# Boîte ASCII (par défaut) — idéal pour affichage terminal
python3 skills/ui-ux-pro-max/scripts/search.py "fintech crypto" --design-system

# Markdown — idéal pour la documentation
python3 skills/ui-ux-pro-max/scripts/search.py "fintech crypto" --design-system -f markdown
```

---

## Astuces pour de meilleurs résultats

### Stratégie de requête

- Utiliser des **mots-clés multidimensionnels** — combiner produit + industrie + ton + densité : `"entertainment social vibrant content-dense"` plutôt que juste `"app"`
- Essayer différents mots-clés pour le même besoin : `"playful neon"` → `"vibrant dark"` → `"content-first minimal"`
- Utiliser `--design-system` d'abord pour les recommandations complètes, puis `--domain` pour creuser une dimension dont vous n'êtes pas sûr
- Toujours ajouter `--stack react-native` pour les conseils d'implémentation spécifiques

### Points de blocage courants

| Problème | Quoi faire |
|----------|------------|
| Impossible de décider du style/couleur | Relancer `--design-system` avec des mots-clés différents |
| Problèmes de contraste en mode sombre | Référence rapide §6 : `color-dark-mode` + `color-accessible-pairs` |
| Animations qui semblent peu naturelles | Référence rapide §7 : `spring-physics` + `easing` + `exit-faster-than-enter` |
| UX de formulaire médiocre | Référence rapide §8 : `inline-validation` + `error-clarity` + `focus-management` |
| Navigation déroutante | Référence rapide §9 : `nav-hierarchy` + `bottom-nav-limit` + `back-behavior` |
| Mise en page cassée sur petits écrans | Référence rapide §5 : `mobile-first` + `breakpoint-consistency` |
| Performance / saccades | Référence rapide §3 : `virtualize-lists` + `main-thread-budget` + `debounce-throttle` |

### Checklist avant livraison

- Exécuter `--domain ux "animation accessibility z-index loading"` comme passe de validation UX avant l'implémentation
- Parcourir la Référence rapide **§1–§3** (CRITIQUE + ÉLEVÉ) comme revue finale
- Tester en 375 px (petit téléphone) et en orientation paysage
- Vérifier le comportement avec **reduced-motion** activé et **Dynamic Type** à la taille maximale
- Vérifier le contraste du mode sombre indépendamment (ne pas supposer que les valeurs du mode clair fonctionnent)
- Confirmer que toutes les cibles tactiles ≥44 pt et qu'aucun contenu n'est caché derrière les safe areas

---

## Règles courantes pour une UI professionnelle

Voici les problèmes fréquemment négligés qui rendent une UI non professionnelle :
Note de périmètre : les règles ci-dessous concernent l'UI d'application (iOS/Android/React Native/Flutter), pas les patterns d'interaction web bureau.

### Icônes et éléments visuels

| Règle | Standard | À éviter | Pourquoi c'est important |
|-------|----------|----------|--------------------------|
| **Pas d'emoji comme icône structurelle** | Utiliser des icônes vectorielles (Lucide, react-native-vector-icons, @expo/vector-icons). | Utiliser des emojis (🎨 🚀 ⚙️) pour la navigation, les paramètres ou les contrôles système. | Les emojis dépendent de la police, sont incohérents entre plateformes et ne peuvent pas être contrôlés par les design tokens. |
| **Assets vectoriels uniquement** | Utiliser des SVG ou icônes vectorielles de plateforme qui scalent proprement et supportent la thématisation. | Icônes PNG matricielles qui floutent ou pixellisent. | Garantit la scalabilité, un rendu net et l'adaptabilité aux modes sombre/clair. |
| **États d'interaction stables** | Utiliser des transitions de couleur, opacité ou élévation pour les états pressés sans changer les bornes de mise en page. | Transformations qui déplacent le contenu environnant ou provoquent du jitter visuel. | Évite les interactions instables et préserve la fluidité/qualité perçue sur mobile. |
| **Logos de marque corrects** | Utiliser les assets officiels et suivre leurs guidelines (espacement, couleur, clear space). | Deviner les chemins de logo, recolorer non officiellement, modifier les proportions. | Évite l'usage abusif de marque et garantit la conformité légale/plateforme. |
| **Taille d'icône cohérente** | Définir les tailles d'icône comme tokens de design (icon-sm, icon-md = 24 pt, icon-lg). | Mélanger des valeurs arbitraires comme 20 pt / 24 pt / 28 pt au hasard. | Maintient le rythme et la hiérarchie visuelle dans l'interface. |
| **Cohérence d'épaisseur de trait** | Utiliser une épaisseur de trait cohérente dans la même couche visuelle (1.5 px ou 2 px). | Mélanger styles épais et fins arbitrairement. | Des traits incohérents réduisent le poli perçu et la cohésion. |
| **Discipline filled vs outline** | Utiliser un seul style d'icône par niveau hiérarchique. | Mélanger icônes pleines et contours au même niveau hiérarchique. | Maintient la clarté sémantique et la cohérence stylistique. |
| **Minimum de cible tactile** | Zone interactive minimum 44×44 pt (utiliser hitSlop si l'icône est plus petite). | Petites icônes sans zone tap étendue. | Respecte les standards d'accessibilité et d'utilisabilité de la plateforme. |
| **Alignement d'icône** | Aligner les icônes sur la baseline du texte et maintenir un padding cohérent. | Icônes mal alignées ou espacement incohérent autour. | Évite un léger déséquilibre visuel qui réduit la qualité perçue. |
| **Contraste d'icône** | Suivre les standards WCAG : 4.5:1 pour les petits éléments, 3:1 minimum pour les glyphes UI plus grands. | Icônes à faible contraste qui se fondent dans le fond. | Garantit l'accessibilité en mode clair comme sombre. |


### Interaction (App)

| Règle | À faire | À éviter |
|-------|---------|---------- |
| **Retour au tap** | Fournir un retour clair à l'appui (ripple/opacité/élévation) en 80-150 ms | Aucune réponse visuelle au tap |
| **Timing d'animation** | Garder les micro-interactions autour de 150-300 ms avec un easing natif | Transitions instantanées ou animations lentes (>500 ms) |
| **Focus d'accessibilité** | S'assurer que l'ordre de focus du lecteur d'écran correspond à l'ordre visuel et que les labels sont descriptifs | Contrôles sans label ou traversée de focus confuse |
| **Clarté de l'état désactivé** | Utiliser la sémantique disabled (`disabled`/props natives), une emphase réduite et aucune action au tap | Contrôles qui semblent tappables mais ne font rien |
| **Minimum de cible tactile** | Garder des zones de tap >=44x44 pt (iOS) ou >=48x48 dp (Android), étendre la zone d'impact quand l'icône est plus petite | Cibles minuscules ou zones icône seule sans padding |
| **Prévention des conflits de geste** | Garder un geste principal par région et éviter les conflits tap/drag imbriqués | Gestes qui se chevauchent provoquant des actions accidentelles |
| **Contrôles natifs sémantiques** | Préférer les primitives interactives natives (`Button`, `Pressable`, équivalents plateforme) avec les rôles d'accessibilité appropriés | Conteneurs génériques utilisés comme contrôles principaux sans sémantique |

### Contraste mode clair/sombre

| Règle | À faire | À éviter |
|-------|---------|---------- |
| **Lisibilité de surface (clair)** | Garder cartes/surfaces clairement séparées du fond par opacité/élévation suffisantes | Surfaces trop transparentes qui floutent la hiérarchie |
| **Contraste de texte (clair)** | Maintenir un contraste du texte corps >=4.5:1 sur surfaces claires | Texte corps gris à faible contraste |
| **Contraste de texte (sombre)** | Maintenir un contraste >=4.5:1 pour le texte primaire et >=3:1 pour le secondaire sur surfaces sombres | Texte mode sombre qui se fond dans le fond |
| **Visibilité des bordures et séparateurs** | S'assurer que les séparateurs sont visibles dans les deux thèmes (pas seulement clair) | Bordures spécifiques à un thème qui disparaissent dans l'autre mode |
| **Parité de contraste des états** | Garder les états pressé/focus/désactivé tout aussi distinguables en clair et sombre | Définir des états d'interaction pour un seul thème |
| **Thématisation par tokens** | Utiliser des tokens de couleur sémantiques mappés par thème sur les surfaces/textes/icônes de l'app | Valeurs hex codées en dur par écran |
| **Lisibilité de scrim et modale** | Utiliser un scrim de modale assez fort pour isoler le contenu de premier plan (typiquement 40-60 % noir) | Scrim faible laissant le fond visuellement concurrent |

### Mise en page & Espacement

| Règle | À faire | À éviter |
|-------|---------|---------- |
| **Conformité aux safe areas** | Respecter les safe areas en haut/bas pour tous les headers fixes, tab bars et barres CTA | Placer une UI fixe sous notch, barre de statut ou zone de geste |
| **Dégagement des barres système** | Ajouter de l'espace pour les barres de statut/navigation et l'indicateur home de geste | Laisser le contenu tappable entrer en collision avec le chrome OS |
| **Largeur de contenu cohérente** | Garder une largeur de contenu prévisible par classe d'appareil (téléphone/tablette) | Mélanger des largeurs arbitraires entre écrans |
| **Rythme d'espacement 8 dp** | Utiliser un système d'espacement 4/8 dp cohérent pour padding/gaps/espacement de sections | Incréments d'espacement aléatoires sans rythme |
| **Mesure de texte lisible** | Garder le texte long lisible sur les grands appareils (éviter les paragraphes bord à bord sur tablettes) | Texte long pleine largeur qui nuit à la lisibilité |
| **Hiérarchie d'espacement de sections** | Définir des paliers de rythme vertical clairs (ex : 16/24/32/48) par hiérarchie | Niveaux UI similaires avec espacement incohérent |
| **Gouttières adaptatives par breakpoint** | Augmenter les marges horizontales sur largeurs plus grandes et en paysage | Même gouttière étroite sur toutes les tailles/orientations |
| **Coexistence scroll et élément fixe** | Ajouter des insets de contenu bas/haut pour que les listes ne soient pas cachées derrière les barres fixes | Contenu scrollable obscurci par headers/footers collants |

---

## Checklist avant livraison

Avant de livrer du code UI, vérifier ces points :
Note de périmètre : cette checklist est pour l'UI d'application (iOS/Android/React Native/Flutter).

### Qualité visuelle
- [ ] Pas d'emojis utilisés comme icônes (utiliser SVG à la place)
- [ ] Toutes les icônes proviennent d'une famille et d'un style cohérents
- [ ] Les assets officiels de marque sont utilisés avec proportions et clear space corrects
- [ ] Les visuels d'état pressé ne décalent pas les bornes de mise en page ni ne provoquent de jitter
- [ ] Les tokens de thème sémantiques sont utilisés de manière cohérente (pas de couleurs codées en dur ad-hoc par écran)

### Interaction
- [ ] Tous les éléments tappables fournissent un retour pressé clair (ripple/opacité/élévation)
- [ ] Les cibles tactiles respectent la taille minimum (>=44x44 pt iOS, >=48x48 dp Android)
- [ ] Le timing des micro-interactions reste dans la plage 150-300 ms avec un easing au ressenti natif
- [ ] Les états désactivés sont visuellement clairs et non interactifs
- [ ] L'ordre de focus du lecteur d'écran correspond à l'ordre visuel, et les labels interactifs sont descriptifs
- [ ] Les régions de geste évitent les interactions imbriquées/conflictuelles (conflits tap/drag/back-swipe)

### Mode clair/sombre
- [ ] Contraste du texte primaire >=4.5:1 en mode clair et sombre
- [ ] Contraste du texte secondaire >=3:1 en mode clair et sombre
- [ ] Séparateurs/bordures et états d'interaction sont distinguables dans les deux modes
- [ ] L'opacité du scrim de modale/drawer est assez forte pour préserver la lisibilité du premier plan (typiquement 40-60 % noir)
- [ ] Les deux thèmes sont testés avant livraison (pas inférés depuis un seul thème)

### Mise en page
- [ ] Les safe areas sont respectées pour headers, tab bars et barres CTA du bas
- [ ] Le contenu scrollable n'est pas caché derrière des barres fixes/collantes
- [ ] Vérifié sur petit téléphone, grand téléphone et tablette (portrait + paysage)
- [ ] Les marges/gouttières horizontales s'adaptent correctement à la taille et à l'orientation
- [ ] Le rythme d'espacement 4/8 dp est maintenu aux niveaux composant, section et page
- [ ] La mesure de texte long reste lisible sur grands appareils (pas de paragraphes bord à bord)

### Accessibilité
- [ ] Toutes les images/icônes significatives ont des labels d'accessibilité
- [ ] Les champs de formulaire ont labels, hints et messages d'erreur clairs
- [ ] La couleur n'est pas le seul indicateur
- [ ] Reduced motion et taille de texte dynamique sont supportés sans casse de mise en page
- [ ] Les traits/rôles/états d'accessibilité (selected, disabled, expanded) sont correctement annoncés
