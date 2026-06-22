---
name: ckm:ui-styling
description: Créer des interfaces utilisateur belles et accessibles avec les composants shadcn/ui (bâtis sur Radix UI + Tailwind), le style utility-first de Tailwind CSS et des designs visuels sur canvas. À utiliser pour construire des interfaces utilisateur, implémenter des design systems, créer des mises en page responsives, ajouter des composants accessibles (dialogues, menus déroulants, formulaires, tableaux), personnaliser thèmes et couleurs, implémenter le mode sombre, générer des designs visuels et des posters, ou établir des patterns de style cohérents.
argument-hint: "[composant ou layout]"
license: MIT
metadata:
  author: claudekit
  version: "1.0.0"
---

# Skill UI Styling

Skill complète pour créer des interfaces utilisateur belles et accessibles, combinant les composants shadcn/ui, le style utility-first de Tailwind CSS et les systèmes de design visuels sur canvas.

## Références

- shadcn/ui : https://ui.shadcn.com/llms.txt
- Tailwind CSS : https://tailwindcss.com/docs

## Quand utiliser cette skill

À utiliser pour :
- Construire une UI avec des frameworks React (Next.js, Vite, Remix, Astro)
- Implémenter des composants accessibles (dialogues, formulaires, tableaux, navigation)
- Styliser avec une approche CSS utility-first
- Créer des mises en page responsives, mobile-first
- Implémenter le mode sombre et la personnalisation de thème
- Bâtir un design system avec des tokens cohérents
- Générer des designs visuels, posters ou supports de marque
- Prototyper rapidement avec retour visuel immédiat
- Ajouter des patterns d'UI complexes (data tables, graphiques, palettes de commandes)

## Stack de base

### Couche composants : shadcn/ui
- Composants accessibles prêts à l'emploi via les primitives Radix UI
- Modèle de distribution copier-coller (les composants vivent dans votre code)
- TypeScript-first avec sécurité de type complète
- Primitives composables pour des UI complexes
- Installation et gestion via CLI

### Couche style : Tailwind CSS
- Framework CSS utility-first
- Traitement à la compilation, aucun surcoût runtime
- Design responsive mobile-first
- Tokens de design cohérents (couleurs, espacement, typographie)
- Élimination automatique du code mort

### Couche design visuel : Canvas
- Compositions visuelles de qualité musée
- Approche de design guidée par la philosophie
- Communication visuelle sophistiquée
- Texte minimal, impact visuel maximal
- Patterns systématiques et esthétique raffinée

## Démarrage rapide

### Configuration composants + style

**Installer shadcn/ui avec Tailwind :**
```bash
npx shadcn@latest init
```

Le CLI demande framework, TypeScript, chemins et préférences de thème. Ceci configure à la fois shadcn/ui et Tailwind CSS.

**Ajouter des composants :**
```bash
npx shadcn@latest add button card dialog form
```

**Utiliser les composants avec le style utility :**
```tsx
import { Button } from "@/components/ui/button"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"

export function Dashboard() {
  return (
    <div className="container mx-auto p-6 grid gap-6 md:grid-cols-2 lg:grid-cols-3">
      <Card className="hover:shadow-lg transition-shadow">
        <CardHeader>
          <CardTitle className="text-2xl font-bold">Analytique</CardTitle>
        </CardHeader>
        <CardContent className="space-y-4">
          <p className="text-muted-foreground">Voir vos métriques</p>
          <Button variant="default" className="w-full">
            Voir les détails
          </Button>
        </CardContent>
      </Card>
    </div>
  )
}
```

### Alternative : configuration Tailwind seul

**Projets Vite :**
```bash
npm install -D tailwindcss @tailwindcss/vite
```

```javascript
// vite.config.ts
import tailwindcss from '@tailwindcss/vite'
export default { plugins: [tailwindcss()] }
```

```css
/* src/index.css */
@import "tailwindcss";
```

## Guide de la bibliothèque de composants

**Catalogue complet de composants avec patterns d'usage, installation et exemples de composition.**

Voir : `references/shadcn-components.md`

Couvre :
- Composants de formulaire et saisie (Button, Input, Select, Checkbox, Date Picker, validation Form)
- Mise en page et navigation (Card, Tabs, Accordion, Navigation Menu)
- Superpositions et dialogues (Dialog, Drawer, Popover, Toast, Command)
- Retour et statut (Alert, Progress, Skeleton)
- Composants d'affichage (Table, Data Table, Avatar, Badge)

## Thème et personnalisation

**Configuration de thème, variables CSS, implémentation du mode sombre et personnalisation des composants.**

Voir : `references/shadcn-theming.md`

Couvre :
- Mise en place du mode sombre avec next-themes
- Système de variables CSS
- Personnalisation des couleurs et palettes
- Personnalisation des variantes de composants
- Implémentation du toggle de thème

## Patterns d'accessibilité

**Patterns ARIA, navigation clavier, support lecteur d'écran et usage de composants accessibles.**

Voir : `references/shadcn-accessibility.md`

Couvre :
- Fonctionnalités d'accessibilité Radix UI
- Patterns de navigation clavier
- Gestion du focus
- Annonces aux lecteurs d'écran
- Accessibilité de la validation de formulaire

## Utilitaires Tailwind

**Classes utilitaires de base pour mise en page, espacement, typographie, couleurs, bordures et ombres.**

Voir : `references/tailwind-utilities.md`

Couvre :
- Utilitaires de mise en page (Flexbox, Grid, positionnement)
- Système d'espacement (padding, margin, gap)
- Typographie (tailles de police, graisses, alignement, hauteur de ligne)
- Couleurs et fonds
- Bordures et ombres
- Valeurs arbitraires pour style personnalisé

## Design responsive

**Breakpoints mobile-first, utilitaires responsives et mises en page adaptatives.**

Voir : `references/tailwind-responsive.md`

Couvre :
- Approche mobile-first
- Système de breakpoints (sm, md, lg, xl, 2xl)
- Patterns d'utilitaires responsives
- Container queries
- Max-width queries
- Breakpoints personnalisés

## Personnalisation de Tailwind

**Structure du fichier de config, utilitaires personnalisés, plugins et extensions de thème.**

Voir : `references/tailwind-customization.md`

Couvre :
- Directive @theme pour tokens personnalisés
- Couleurs et polices personnalisées
- Extensions d'espacement et de breakpoints
- Création d'utilitaires personnalisés
- Variantes personnalisées
- Organisation par couches (@layer base, components, utilities)
- Directive Apply pour l'extraction de composants

## Système de design visuel

**Philosophie de design sur canvas, principes de communication visuelle et compositions sophistiquées.**

Voir : `references/canvas-design-system.md`

Couvre :
- Approche philosophie de design
- Communication visuelle plutôt que textuelle
- Patterns systématiques et composition
- Design de couleur, forme et spatial
- Intégration minimale de texte
- Exécution de qualité musée
- Design systems multi-pages

## Scripts utilitaires

**Automation Python pour installation de composants et génération de configuration.**

### shadcn_add.py
Ajouter des composants shadcn/ui avec gestion des dépendances :
```bash
python scripts/shadcn_add.py button card dialog
```

### tailwind_config_gen.py
Générer tailwind.config.js avec un thème personnalisé :
```bash
python scripts/tailwind_config_gen.py --colors brand:blue --fonts display:Inter
```

## Bonnes pratiques

1. **Composition de composants** : Construire des UI complexes à partir de primitives simples et composables
2. **Style utility-first** : Utiliser les classes Tailwind directement ; extraire des composants uniquement pour de vraies répétitions
3. **Responsive mobile-first** : Démarrer avec les styles mobile, superposer les variantes responsives
4. **Accessibilité d'abord** : Tirer parti des primitives Radix UI, ajouter les états de focus, utiliser du HTML sémantique
5. **Tokens de design** : Utiliser une échelle d'espacement, des palettes et un système typographique cohérents
6. **Cohérence du mode sombre** : Appliquer les variantes sombres à tous les éléments thématisés
7. **Performance** : Tirer parti du purge CSS automatique, éviter les noms de classes dynamiques
8. **TypeScript** : Utiliser la sécurité de type complète pour une meilleure DX
9. **Hiérarchie visuelle** : Laisser la composition guider l'attention, utiliser espacement et couleur intentionnellement
10. **Maîtrise d'expert** : Chaque détail compte — traiter l'UI comme un artisanat

## Navigation des références

**Bibliothèque de composants**
- `references/shadcn-components.md` — Catalogue complet de composants
- `references/shadcn-theming.md` — Thématisation et personnalisation
- `references/shadcn-accessibility.md` — Patterns d'accessibilité

**Système de style**
- `references/tailwind-utilities.md` — Classes utilitaires de base
- `references/tailwind-responsive.md` — Design responsive
- `references/tailwind-customization.md` — Configuration et extensions

**Design visuel**
- `references/canvas-design-system.md` — Philosophie de design et workflows canvas

**Automation**
- `scripts/shadcn_add.py` — Installation de composants
- `scripts/tailwind_config_gen.py` — Génération de config

## Patterns courants

**Formulaire avec validation :**
```tsx
import { useForm } from "react-hook-form"
import { zodResolver } from "@hookform/resolvers/zod"
import * as z from "zod"
import { Form, FormField, FormItem, FormLabel, FormControl, FormMessage } from "@/components/ui/form"
import { Input } from "@/components/ui/input"
import { Button } from "@/components/ui/button"

const schema = z.object({
  email: z.string().email(),
  password: z.string().min(8)
})

export function LoginForm() {
  const form = useForm({
    resolver: zodResolver(schema),
    defaultValues: { email: "", password: "" }
  })

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(console.log)} className="space-y-6">
        <FormField control={form.control} name="email" render={({ field }) => (
          <FormItem>
            <FormLabel>Courriel</FormLabel>
            <FormControl>
              <Input type="email" {...field} />
            </FormControl>
            <FormMessage />
          </FormItem>
        )} />
        <Button type="submit" className="w-full">Se connecter</Button>
      </form>
    </Form>
  )
}
```

**Mise en page responsive avec mode sombre :**
```tsx
<div className="min-h-screen bg-white dark:bg-gray-900">
  <div className="container mx-auto px-4 py-8">
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <Card className="bg-white dark:bg-gray-800 border-gray-200 dark:border-gray-700">
        <CardContent className="p-6">
          <h3 className="text-xl font-semibold text-gray-900 dark:text-white">
            Contenu
          </h3>
        </CardContent>
      </Card>
    </div>
  </div>
</div>
```

## Ressources

- Docs shadcn/ui : https://ui.shadcn.com
- Docs Tailwind CSS : https://tailwindcss.com
- Radix UI : https://radix-ui.com
- Tailwind UI : https://tailwindui.com
- Headless UI : https://headlessui.com
- v0 (générateur d'UI par IA) : https://v0.dev
