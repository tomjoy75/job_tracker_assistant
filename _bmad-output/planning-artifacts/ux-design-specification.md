---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14]
inputDocuments:
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/prd.md"
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/product-brief-job_tracker_assistant-2026-01-11.md"
lastStep: 14
---

# UX Design Specification job_tracker_assistant

**Author:** Tjoyeux
**Date:** 2026-01-12

---

<!-- UX design content will be appended sequentially through collaborative workflow steps -->
## Executive Summary

### Project Vision

Réduire la dispersion de la recherche d’emploi via un back‑office personnel qui permet de capturer rapidement des entreprises, compléter les fiches plus tard, et recevoir des alertes ciblées depuis les pages carrière officielles.

### Target Users

- Thomas (reconversion dev) + juniors/chercheurs d’emploi
- Utilisateurs secondaires : admin/ops, support

### Key Design Challenges

- Capture ultra‑rapide “en contexte” (sans casser le flow)
- Réglage des critères sans complexité
- Gestion du bruit (trop d’alertes) sans frustration

### Design Opportunities

- “Capture en 2 temps” comme pattern clé
- Onboarding guidé sur critères + auto‑ajustements
- Tableau de bord “calme” qui réduit la charge mentale

## Core User Experience

### Defining Experience

L’expérience cœur repose sur une capture immédiate d’opportunités depuis le navigateur, avec un enrichissement différé, afin de réduire la charge mentale et préserver le flux de recherche.

### Platform Strategy

- Web App (SPA) comme centre de contrôle
- Extension navigateur (Chrome, Firefox, Safari, Edge) comme point d’entrée principal pour la capture instantanée
- Accès mobile pour consultation et suivi

### Effortless Interactions

- Capture en 1–2 clics depuis une page carrière
- Sauvegarde “en deux temps” : URL maintenant, détails plus tard
- Enrichissement a posteriori sans friction
- Feedback instantané après capture (toast, statut)

### Critical Success Moments

- Réception d’une alerte ultra‑ciblée en temps quasi‑réel (stack + localisation) avec fiabilité perçue
- Visibilité claire du statut des sources (ex. source dégradée)
- Back‑office lisible qui montre que l’outil travaille pour l’utilisateur

### Experience Principles

- **Zéro friction à la capture**
- **Réduction immédiate de la charge mentale**
- **Alertes pertinentes avant tout**
- **Contrôle utilisateur sur les sources et critères**
- **Capture d’abord, réflexion ensuite**

## Desired Emotional Response

### Primary Emotional Goals

- Sérénité : l’outil agit comme un filet intelligent qui travaille en arrière‑plan.

### Emotional Journey Mapping

- Découverte : calme, curiosité.
- Capture réussie : légèreté immédiate, attention libérée.
- Alerte ultra‑pertinente : satisfaction, sentiment d’opportunité réelle.
- En cas de problème : confiance grâce à la transparence et la résilience.

### Micro-Emotions

- Contrôle : maîtrise du marché sans effort constant.
- Soulagement : aucune offre importante ne passe entre les mailles du filet.
- Confiance : système fiable et résilient.

### Design Implications

- Réduire le bruit et privilégier la pertinence pour éviter le stress.
- Rendre la capture instantanée et non intrusive.
- Rendre visible l’état des sources pour renforcer la confiance.

### Emotional Design Principles

- **Calme avant tout**
- **Pertinence = confiance**
- **Simplicité pour éviter l’accablement**

## UX Pattern Analysis & Inspiration

### Inspiring Products Analysis

- **Linear** : performance perçue et clarté visuelle. Le minimalisme informatif permet d’afficher beaucoup de données sans surcharge mentale.
- **Todoist** : capture “Quick Add” et organisation différée. La saisie intelligente inspire la capture en 2 temps.
- **Notion** : fiches structurées et vues multiples. Le pattern “page dans une base” convient aux fiches enrichies et au suivi.

### Transferable UX Patterns

- **Performance instantanée** (Linear) → dashboard fluide et temps de réponse courts.
- **Minimalisme informatif** (Linear) → hiérarchie claire sans effet “usine à gaz”.
- **Capture en 2 temps** (Todoist) → sauver maintenant, compléter plus tard.
- **Saisie intelligente** (Todoist) → suggestions discrètes pour extraction du nom/source, jamais bloquantes.
- **Fiches enrichies** (Notion) → notes, CV, historique par entreprise.
- **Progressive disclosure** (Notion) → liste par défaut, mode suivi seulement en recherche active.

### Anti-Patterns to Avoid

- Interfaces surchargées ou trop configurables (risque de dispersion).
- Flots d’alertes non filtrés qui créent du stress.
- Parcours de capture trop longs qui cassent le “flow”.

### Design Inspiration Strategy

**Adopter :**
- Rapidité et sobriété visuelle (Linear)
- Capture rapide + enrichissement différé (Todoist)

**Adapter :**
- Saisie intelligente comme assistance (Todoist) : capture brute toujours possible
- Fiches structurées et vues flexibles (Notion) sans complexité excessive

**Éviter :**
- La lourdeur d’outils généralistes (Notion) dans le MVP

## Design System Foundation

### 1.1 Design System Choice

**Choix :** MUI (themeable system)

### Rationale for Selection

- Rapidité de développement avec composants éprouvés
- Personnalisation suffisante pour un style “calme et minimal”
- Accessibilité et cohérence visuelle out-of-the-box

### Implementation Approach

- Baseline MUI + thème personnalisé (couleurs, typographies, spacing)
- Composants MUI par défaut pour le MVP
- Extensions spécifiques uniquement si nécessaire

### Customization Strategy

- Définir des design tokens (couleurs, typographie, rayons, ombres)
- Prioriser lisibilité, sobriété et faible charge cognitive
- Définir 2–3 tokens majeurs dès le départ (couleur principale, gris neutres, rayon)
- Pas de composants avancés avant validation du MVP
- Personnaliser typography/spacing et réserver 1–2 composants “signature” pour la phase 2

## 2. Core User Experience

### 2.1 Defining Experience

La capture ultra‑rapide via l’extension navigateur (1–2 clics) pour enregistrer une offre/entreprise.

### 2.2 User Mental Model

Un marque‑page intelligent / “vide‑poche” numérique où l’utilisateur dépose des opportunités sans les traiter immédiatement.

### 2.3 Success Criteria

L’utilisateur peut fermer l’onglet immédiatement avec la certitude que le système prend le relais (scraping + veille).

### 2.4 Novel UX Patterns

Pattern établi (Quick Add à la Todoist) pour réduire l’effort d’apprentissage et maximiser l’adoption.

### 2.5 Experience Mechanics

1. **Initiation** : découverte d’une page carrière/offre pendant la navigation.  
2. **Interaction** : clic sur l’extension → capture URL + identification entreprise.  
3. **Feedback** : confirmation visuelle brève (badge “Capturé”).  
4. **Completion** : l’utilisateur continue sa navigation, l’item est centralisé au dashboard.

## Visual Design Foundation

### Color System

- Couleur principale : bleu doux (sérénité, contrôle, stabilité).
- Bleu profond pour actions critiques (CTA) sans agressivité.
- Palette neutre : gris froids pour structure et lisibilité.
- Couleurs sémantiques : succès/alerte/erreur en ton discret pour éviter le stress.
- Contrastes conformes WCAG AA.

### Typography System

- Sans‑serif moderne et neutre (aligné MUI).
- Hiérarchie claire (H1–H3 + body) pour lecture rapide.
- Lisibilité prioritaire pour tableaux et listes.

### Spacing & Layout Foundation

- Densité aérée pour réduire l’accablement.
- Grille d’espacement 8px (MUI) pour cohérence.
- Blocs de contenu respirants + marges généreuses.
- Principe : une idée par bloc pour préserver le calme.

### Accessibility Considerations

- WCAG 2.1 AA sur parcours critiques.
- Contraste minimal 4.5:1 pour texte, 3:1 pour composants UI.

## Design Direction Decision

### Design Directions Explored

- Direction 1 (Minimalisme Zen) : dashboard calme, hiérarchie claire.
- Direction 2 (Efficacité technique) : capture dominante, feedback immédiat.

### Chosen Direction

Mix Direction 1 + Direction 2.

### Design Rationale

L’outil disparaît derrière l’action de capture (vitesse), tout en restant un havre de paix sur le dashboard (sérénité).

### Implementation Approach

- Capture prioritaire et visible (CTA/extension)
- Dashboard minimaliste et apaisant
- Feedback immédiat après capture (badge/toast)

## User Journey Flows

### 1) Capture rapide via extension (core loop)

```mermaid
flowchart TD
  A[Détection page intéressante] --> B[Clic sur l'extension]
  B --> C[Capture URL + auto-détection entreprise]
  C --> D{Auto-détection OK ?}
  D -- Non --> E[Champ rapide: \"Nom entreprise ?\"]
  E --> F[Valider]
  D -- Oui --> G[Continuer]
  F --> G
  G --> H{Scraping > 2s ?}
  H -- Oui --> I[Capture asynchrone<br/>UI non bloquée]
  H -- Non --> J[Capture immédiate]
  I --> K[Feedback visuel: \"Capturé\"]
  J --> K
  K --> L[Option: ajout rapide de tag]
  L --> M[Fermeture discrète de l'extension]
  M --> N[Navigation continue]
  N --> O[Item disponible dans le dashboard]
```

### 2) Alerte ultra‑pertinente → action

```mermaid
flowchart TD
  A[Offre détectée] --> B[Filtrage critères (stack + localisation)]
  B --> C{Pertinente ?}
  C -- Oui --> D[Notification (email/push/dashboard)]
  D --> E[Statut livraison: délivrée / retardée]
  E --> F[Ouverture détail offre]
  F --> G[Action: sauvegarder / postuler / noter]
  G --> H[Statut mis à jour]
  C -- Non --> I[Ignorer / ajuster filtres suggérés]
```

### 3) Gestion du bruit / ajustement filtres

```mermaid
flowchart TD
  A[Trop d'alertes] --> B[Détection du bruit]
  B --> C[Suggestion d'ajustements]
  C --> D[Prévisualisation impact (ex. -60% alertes)]
  D --> E{Accepter ?}
  E -- Oui --> F[Appliquer filtres]
  F --> G[Réduction du volume]
  E -- Non --> H[Conserver critères]
  G --> I{Bruit persistant ?}
  I -- Oui --> J[Proposer mode digest quotidien]
  I -- Non --> K[Flux stabilisé]
  H --> L[Option: activer mode \"calme\"]
```

### Journey Patterns

- Capture asynchrone et non‑bloquante
- Feedback immédiat (toast/badge)
- Progressive disclosure (tags & enrichissement plus tard)
- Suggestions discrètes avec impact attendu
- Statut clair des sources/alertes
- Digest optionnel si bruit persistant

### Flow Optimization Principles

- Zéro friction à la capture
- Pas de rupture de navigation (fermeture discrète)
- Réduction du bruit avant tout
- Feedback clair à chaque étape
- Ajustements guidés plutôt qu’imposés
- Contrastes validés et navigation clavier.

## Component Strategy

### Design System Components

MUI fournit la base : Buttons, Inputs, Dialogs, Cards, Tabs, Tooltips, Chips, Badges, Snackbar, Lists, DataGrid.

### Custom Components

### Capture Toast
**Purpose:** Confirmation non intrusive après capture.  
**Usage:** Après clic extension / capture réussie.  
**States:** success, error, pending (async), delayed.  
**Accessibility:** aria-live polite.

### Source Status Chip
**Purpose:** Statut de source (OK/Lent/KO).  
**Usage:** Dashboard et liste entreprises.  
**States:** ok, slow, down.  
**Accessibility:** label explicite.

### Alert Card
**Purpose:** Résumer une offre + actions.  
**Usage:** Liste d’alertes.  
**States:** new, viewed, archived, delayed.  
**Actions:** ouvrir, sauvegarder, noter.

### Company Card
**Purpose:** Vue synthétique entreprise.  
**Usage:** Dashboard entreprises.  
**Content:** nom, tags, alertes, statut source.

### Noise Control Panel
**Purpose:** Ajuster filtres + preview impact.  
**Usage:** Après détection de bruit.  
**States:** default, preview, applied.

### Quick Tagger
**Purpose:** Ajout rapide de tags.  
**Usage:** Capture extension + fiche entreprise.  
**States:** empty, suggested, confirmed.

### Delivery Status Badge
**Purpose:** Alerte délivrée/retardée.  
**Usage:** Liste alertes.  
**States:** delivered, delayed.

### Capture Drawer
**Purpose:** Compléter une capture sans quitter le dashboard.  
**Usage:** Ouverture latérale depuis une capture incomplète.  
**States:** open, closed, saving, error.

### Capture Queue
**Purpose:** Liste priorisée des captures à compléter.  
**Usage:** Dashboard, mode “zen”.  
**States:** empty, pending, sorted.

### Component Implementation Strategy

- Prioriser les composants MVP liés à la capture et aux alertes
- Construire sur tokens MUI + thème personnalisé
- Accessibilité systématique (labels, focus, keyboard)
- États d’erreur/latence explicités pour composants critiques

### Implementation Roadmap

**Phase 1 (MVP):**
- Capture Toast
- Source Status Chip
- Alert Card
- Company Card
- Quick Tagger
- Capture Drawer
- Capture Queue

**Phase 2 (Post‑MVP):**
- Noise Control Panel
- Delivery Status Badge

**Phase 3 (Enhancements):**
- Variantes avancées (filtres intelligents, stats intégrées)

## UX Consistency Patterns

### Button Hierarchy

**When to Use:** Action de capture = primaire, réglages = secondaires.  
**Visual Design:** CTA bleu profond; actions secondaires neutres.  
**Behavior:** 1–2 clics max pour capture.  
**Accessibility:** focus visible, labels explicites.  
**Mobile Considerations:** CTA toujours accessible.

### Feedback Patterns

**When to Use:** Capture, scraping, alertes, erreurs.  
**Visual Design:** toasts sobres, chips statut source.  
**Behavior:** feedback immédiat; statut clair (OK/Lent/KO).  
**Accessibility:** aria-live polite; icônes + texte.  
**Mobile Considerations:** toasts non intrusifs.

### Empty & Loading States

**When to Use:** premières captures, scraping en attente, erreurs.  
**Visual Design:** messages d’invitation (“Capturer votre première offre”).  
**Behavior:** progress + retries visibles.  
**Accessibility:** texte clair, pas d’animations agressives.  
**Mobile Considerations:** états compacts.

### Search, Filters & Cards

**When to Use:** dashboard, alertes, entreprises.  
**Visual Design:** cartes cohérentes (Alert/Company) avec hiérarchie visuelle stable.  
**Behavior:** filtres visibles mais discrets; preview d’impact.  
**Accessibility:** navigation clavier, focus visible.  
**Mobile Considerations:** filtres en drawer.

### Navigation & Forms

**When to Use:** navigation globale + enrichissement fiches.  
**Visual Design:** navigation minimale; formulaires MUI standardisés.  
**Behavior:** étapes courtes, validation douce.  
**Accessibility:** labels, erreurs explicites.  
**Mobile Considerations:** sections courtes et scroll léger.

## Responsive Design & Accessibility

### Responsive Strategy

- **Desktop-first** : extension navigateur + dashboard optimisés pour grand écran.
- **Mobile** : focus sur alertes, consultation rapide, changement de statut.

### Breakpoint Strategy

- Breakpoints standards MUI : 320px / 768px / 1024px.

### Accessibility Strategy

- WCAG 2.1 AA confirmé.
- Cibles tactiles 44x44px.
- Navigation clavier et focus visibles.

### Testing Strategy

- Navigateurs : Chrome/Edge (extension) + Safari mobile.
- Devices : desktop + smartphone.
- Lecteurs d’écran : VoiceOver/NVDA (test de base).
- Navigation clavier systématique.

### Implementation Guidelines

- Desktop-first, mobile optimisé pour les actions critiques.
- Bottom navigation sur mobile (Alertes / Entreprises / Profil).
- Grille MUI et tokens pour cohérence responsive.
