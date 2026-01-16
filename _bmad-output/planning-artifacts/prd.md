---
stepsCompleted: [1, 2, 3, 4, 6, 7, 8, 9, 10, 11]
lastStep: 2
inputDocuments:
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/product-brief-job_tracker_assistant-2026-01-11.md"
documentCounts:
  briefs: 1
  research: 0
  brainstorming: 0
  projectDocs: 0
workflowType: 'prd'
lastStep: 0
---

# Product Requirements Document - job_tracker_assistant

**Author:** Tjoyeux
**Date:** 2026-01-11
## Executive Summary

Job Tracker Assistant est une web app (avec extension navigateur et mobile) centrée sur la **capture ultra‑rapide** d’entreprises/offres et des **alertes ciblées** en temps réel depuis les **pages carrière officielles** suivies. Elle réduit la dispersion et la charge mentale de la recherche d’emploi en centralisant les opportunités, les documents et le suivi des candidatures, pour rendre l’expérience plus fluide et soutenable.

### What Makes This Special

- Capture en deux temps : enregistrer maintenant, compléter ensuite  
- Alertes ultra ciblées basées sur les pages carrière (moins de bruit)  
- Expérience fluide et agréable qui réduit la charge mentale  

## Project Classification

**Technical Type:** web_app  
**Domain:** general  
**Complexity:** low  
**Project Context:** Greenfield - new project

Classification signals: “web app, dashboard, alerts, browser/extension”.
## Success Criteria

### User Success

- Nombre d’entreprises suivies
- Nombre de fiches complétées
- Nombre d’annonces qualifiées (pertinentes)
- Nombre de contacts LinkedIn initiés
- Nombre de candidatures (CV envoyés)
- Délai moyen entre alerte et candidature
- Réception régulière (hebdomadaire) d’offres pertinentes

### Business Success

**À 3 mois**
- 15 entreprises suivies
- 75% d’offres pertinentes
- 5 candidatures envoyées
- 80% de complétion des fiches
- 1 jour max entre alerte et candidature

**À 12 mois**
- 100 entreprises suivies
- 75% d’offres pertinentes
- 50 candidatures envoyées
- 100% de complétion des fiches
- 1 jour max entre alerte et candidature

### Technical Success

- Capture d’entreprise/offre en < 20s
- Alertes déclenchées en temps quasi réel (minutes)
- Taux d’échec de scraping surveillé et < 5% (MVP)
- Disponibilité du service ≥ 99% (MVP)

### Measurable Outcomes

- % d’offres pertinentes sur le total d’alertes
- Délai moyen alerte → candidature
- Taux de complétion des fiches entreprises
- Nombre de candidatures envoyées via l’outil
- Nombre d’entreprises actives suivies

## Product Scope

### MVP - Minimum Viable Product

- Enregistrement ultra‑rapide d’entreprises/offres
- Backoffice pour compléter les fiches (avec rappels)
- Alertes sur nouvelles offres pertinentes
- Consultation centralisée des entreprises/offres

### Growth Features (Post-MVP)

- Scraping enrichi (auto‑préremplissage complet)
- Intégration Glassdoor
- Organisation avancée (tags, dossiers)
- Partage public/communautaire

### Vision (Future)

- Gamification du processus
- Génération de CV/LM adaptés aux annonces
- Chatbot / conseiller d’orientation

## User Journeys

**Journey 1 — Thomas (parcours principal)**  
Thomas reçoit des alertes Indeed et repère une annonce intéressante. Il consulte l’entreprise, vérifie la distance et le cadre, puis trouve une page carrière avec des offres de stage. Il épingle la page et ajoute quelques tags (ex. “-20 min”, “cadre”). Il sait qu’il sera alerté dès qu’une nouvelle offre correspondant à ses critères sera publiée. Il se sent en contrôle, sans dispersion.

**Journey 2 — Thomas (cas limite : trop d’alertes)**  
Thomas active les alertes pour plusieurs entreprises, mais reçoit trop d’offres peu pertinentes. Il se sent submergé et craint de retomber dans la dispersion. L’outil détecte ce bruit et propose un ajustement guidé (mots‑clés, contrat, localisation), avec aperçu du filtrage. Une fois les filtres resserrés, il retrouve un flux d’alertes utile et soutenable.

**Journey 3 — Admin/Ops (qualité des sources & alertes)**  
Camille administre la plateforme pour une cohorte d’apprenants. Elle surveille la qualité des sources et les taux de pertinence. En cas d’échecs récurrents (pages inaccessibles, formats changeants), elle met en pause la source et lance une vérification. Elle ajuste des règles globales (fréquence d’alerte, critères par défaut) et observe l’amélioration immédiate. Son “aha moment” : la chute du bruit et le retour d’usage actif.

**Journey 4 — Support (résolution & récupération)**  
Alex reçoit un ticket : “je ne reçois plus d’alertes depuis 2 semaines”. Il constate une page carrière inaccessible et des critères trop stricts. Il relance la source, assouplit les filtres, puis crée une alerte test. L’utilisateur reçoit une annonce pertinente et confirme le rétablissement. Alex enregistre l’incident pour améliorer le diagnostic automatique.

### Journey Requirements Summary

- Capture rapide d’une entreprise/offre depuis une page web
- Ajout de tags/critères simples lors de la capture
- Alertes ciblées et ajustables (mots‑clés, contrat, localisation)
- Gestion du bruit (trop d’alertes) avec recommandations
- Suivi de la disponibilité des pages carrière et retries
- Gestion des doublons (détection et fusion)
- Historisation des offres supprimées
- Outils admin pour surveiller la qualité des sources et ajuster les règles
- Support avec diagnostic guidé et alertes de test

## Innovation & Novel Patterns

### Detected Innovation Areas

- Passage d’une logique d’agrégateurs (push bruité) à un **back‑office personnel** où l’utilisateur sélectionne ses entreprises et affine ses critères.
- **Pertinence adaptive** : les alertes s’améliorent au fur et à mesure des ajustements.

### Market Context & Competitive Landscape

La norme actuelle est la réception d’offres via agrégateurs (LinkedIn, Indeed) avec un bruit important et des offres vues trop tard. L’approche proposée privilégie la maîtrise de la source (pages carrière) et la personnalisation progressive.

### Validation Approach

- Mesurer la **pertinence perçue** des alertes (feedback utilisateur).
- Comparer le **délai d’accès** à l’offre vs. agrégateurs.
- Mesurer la **réduction du bruit** (ratio offres pertinentes / totales).

### Risk Mitigation

- Si le volume d’offres est trop faible, proposer un **mode élargi** (sources supplémentaires).
- Si la pertinence est faible, proposer des **ajustements guidés** et presets de critères.

## Web App Specific Requirements

### Project-Type Overview

Web app orientée tableau de bord avec extension navigateur et support mobile. Priorité à une expérience fluide de capture et de consultation.

### Technical Architecture Considerations

- **SPA** pour une navigation rapide et une UX fluide
- **Support navigateurs** : Chrome, Firefox, Safari, Edge + mobile
- **SEO** : non requis
- **Temps réel** : quasi temps réel en MVP (polling 5–15 min), améliorable ensuite
- **Accessibilité** : cible WCAG AA

### Implementation Considerations

- Optimiser les performances pour capture < 20s
- Notifications/alertes fiables avec tolérance aux latences
- Prise en compte mobile pour capture rapide et consultation

## Project Scoping & Phased Development

### MVP Strategy & Philosophy

**MVP Approach:** Experience MVP  
**Resource Requirements:** petite équipe (1–2 devs) + temps partiel produit/ops pour calibrer les alertes

### MVP Feature Set (Phase 1)

**Core User Journeys Supported:**
- Capture ultra‑rapide d’une entreprise + page recrutement
- Alertes ciblées dès qu’une nouvelle offre apparaît

**Must-Have Capabilities:**
- Extension navigateur avec capture en 1–2 clics
- Scraping automatisé des pages carrière suivies
- Système d’alertes ciblées (stack + localisation)
- Dashboard minimal de centralisation (entreprises + alertes)

### Post-MVP Features

**Phase 2 (Post-MVP):**
- Enrichissement automatique (distance + note Glassdoor)
- Gestion de documents/notes (CV + ressenti)
- Historique des échanges et contacts
- Suivi simplifié des candidatures (statuts)

**Phase 3 (Expansion):**
- Scraping multi-sources (Indeed, etc.) avec filtre anti‑bruit
- Assistant IA de candidature (CV/LM adaptés)
- Synchronisation mobile / app compagnon
- Analyses prédictives (périodes de publication)

### Risk Mitigation Strategy

**Technical Risks:** scraping fragile → monitoring + fallback manuel  
**Market Risks:** manque d’usage → validation rapide du “magic moment”  
**Resource Risks:** scope trop large → garder dashboard minimal en MVP

## Functional Requirements

### Onboarding & Profil Utilisateur
- FR1: L’utilisateur peut créer un compte et se connecter.
- FR2: L’utilisateur peut définir ses critères globaux de recherche (stack, localisation, type de contrat).
- FR3: L’utilisateur peut mettre à jour ses critères globaux à tout moment.

### Capture & Enregistrement
- FR4: L’utilisateur peut enregistrer une entreprise/offre depuis une page web en 1–2 actions.
- FR5: L’utilisateur peut enregistrer une source via un lien ou une capture (photo/URL).
- FR6: Le système peut détecter les doublons lors de l’enregistrement.
- FR7: L’utilisateur peut fusionner deux entreprises en doublon.
- FR8: L’utilisateur peut effectuer une capture en deux temps (sauver maintenant, compléter plus tard).

### Fiches Entreprises & Données
- FR9: L’utilisateur peut compléter une fiche entreprise (notes, tags, informations clés).
- FR10: L’utilisateur peut associer des liens (page carrière, site, LinkedIn).
- FR11: Le système peut conserver l’historique des offres supprimées.
- FR12: Le système peut rappeler à l’utilisateur de compléter une fiche incomplète.

### Alertes & Pertinence
- FR13: Le système peut détecter les changements/nouvelles offres sur les pages carrière suivies.
- FR14: Le système peut filtrer les offres selon les critères utilisateur.
- FR15: L’utilisateur peut ajuster les filtres lorsque trop d’alertes sont reçues.
- FR16: L’utilisateur peut recevoir des alertes via email, push, et tableau de bord.
- FR17: L’utilisateur peut définir des critères spécifiques par entreprise, en plus des critères globaux.
- FR18: Le système peut signaler l’inaccessibilité d’une page carrière et réessayer automatiquement.

### Tableau de Bord & Suivi
- FR19: L’utilisateur peut consulter un tableau de bord centralisant entreprises et offres.
- FR20: L’utilisateur peut voir l’état des alertes par entreprise.
- FR21: L’utilisateur peut suivre les candidatures (statut basique).

### Documents & Notes (Post‑MVP)
- FR22: L’utilisateur peut associer un CV ou document à une entreprise/offre.
- FR23: L’utilisateur peut enregistrer un ressenti/avantages sur une entreprise.

### Admin / Ops
- FR24: Un admin peut surveiller la qualité des sources (pages carrière).
- FR25: Un admin peut mettre en pause une source en cas d’échec répété.
- FR26: Un admin peut ajuster des règles globales de filtrage/alertes.

### Support
- FR27: Un support peut diagnostiquer l’absence d’alertes pour un utilisateur.
- FR28: Un support peut déclencher un test d’alerte et proposer une correction.

## Non-Functional Requirements

### Performance

- Enregistrement d’URL en < 1s pour la capture rapide.
- Chargement initial et filtrage du tableau de bord en < 2s.

### Fiabilité

- Vérification des pages carrière toutes les 15 à 30 minutes.
- Taux de succès du scraping > 95% avec retries automatiques sur erreurs 404/500.
- 95% des alertes délivrées en < 15 minutes.
- Taux de faux positifs des alertes maintenu bas (objectif à définir).

### Sécurité

- Chiffrement des données en transit (TLS 1.3) et au repos (AES-256).
- Isolation stricte des données par utilisateur.

### Scalabilité

- Support fluide jusqu’à 500 entreprises suivies actives et 2000 offres suivies par utilisateur.
- Architecture capable d’une montée en charge x10 sans refonte majeure.

### Accessibilité

- Conformité WCAG 2.1 AA sur les parcours critiques (navigation clavier, contrastes validés).
