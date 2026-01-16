---
stepsCompleted: [1, 2, 3, 4, 5]
inputDocuments: []
date: 2026-01-11
author: Tjoyeux
---

# Product Brief: job_tracker_assistant

<!-- Content will be appended sequentially through collaborative workflow steps -->
## Executive Summary

Job Tracker Assistant vise à réduire la dispersion et la charge mentale de la recherche d’emploi en centralisant la collecte d’entreprises et d’offres pertinentes, tout en gardant les documents clés à portée de main. L’outil s’adresse en priorité aux personnes en recherche de stage/emploi (notamment juniors) qui subissent une expérience fragmentée entre multiples outils. La valeur clé : une capture ultra‑rapide et des alertes ciblées en temps réel à partir des pages carrière des entreprises suivies. L’objectif final est d’aider l’utilisateur à rester prêt et réactif, sans épuiser son énergie.

---

## Core Vision

### Problem Statement

La recherche d’emploi est dispersée entre de nombreux outils (tableaux, favoris, notes, pages ouvertes, contacts LinkedIn), ce qui génère de la friction, du temps perdu et une forte charge mentale.

### Problem Impact

Cette dispersion crée une expérience négative (stress, overwhelm, découragement), ralentit les candidatures, et fait manquer des opportunités pertinentes — particulièrement pour les juniors et personnes en reconversion.

### Why Existing Solutions Fall Short

Les outils généralistes (ex. Notion) ne sont pas dédiés au suivi d’offres et n’intègrent pas les pages carrière pour générer des alertes ciblées. Résultat : l’information se noie dans d’autres usages, sans automatisation utile.

### Proposed Solution

Un assistant qui permet d’enregistrer une entreprise en 1–2 clics (lien ou photo), puis de compléter une fiche dédiée. L’outil surveille ensuite les pages carrière et envoie une alerte immédiate si une offre correspond aux critères (stack, localisation, type de contrat). Un tableau de bord centralise tout : entreprises suivies, offres reçues, candidatures envoyées, échanges.

### Key Differentiators

- Capture ultra‑rapide “en deux temps” (sauver maintenant, compléter ensuite)
- Alertes temps réel sur pages carrière ciblées (pas de bruit d’agrégateurs)
- Expérience fluide et agréable, pensée pour réduire la charge mentale
- Focus stage/alternance/juniors avec critères précis et contexte personnalisé

## Target Users

### Primary Users

**Persona 1 — Thomas Joyeux (reconversion dev, 50 ans)**  
Ancien musicien en reconversion vers le développement. Il a déjà envoyé quelques CV ciblés sans résultats convaincants. Il cherche des entreprises tech liées de près ou de loin à la musique.  
**Motivations :** stabilité financière, soutien familial, équilibre vie pro/perso.  
**Douleurs :** manque de retours, stress financier, sentiment d’insuffisance pour sa famille.  
**Succès :** trouver un poste où il se sent à sa place, avec une sécurité financière et un rythme familial sain.

**Persona 2 — Nouvel entrant (junior)**  
N’a pas d’expérience pro solide. Il cible des entreprises selon ses valeurs (ex. écologie), ambitions salariales, cadre (taille d’équipe), montée en compétences, et technologies.  
**Motivations :** apprendre vite, construire une trajectoire cohérente.  
**Douleurs :** dispersion, difficulté à prioriser, manque de structure.

### Secondary Users

- Organismes de formation (ex. 42) qui souhaitent outiller leurs élèves.  
- Chasseurs de tête pouvant recommander l’outil à des profils juniors.

### User Journey

**Thomas — parcours principal**  
- **Découverte :** via son réseau/école (ex. 42).  
- **Onboarding :** création de compte.  
- **Usage quotidien :** enregistre une entreprise/offre dès qu’elle l’intéresse; reçoit des rappels pour compléter les fiches; tente de contacter des employés via LinkedIn.  
- **Aha moment :** reçoit une alerte immédiate pour une offre parfaitement alignée avec ses critères.  
- **Long terme :** conserve un “réservoir” de boîtes, historiques et contacts, utile même en poste s’il veut changer.

**Nouvel entrant — parcours rapide (à préciser)**  
Découvre l’outil via école/communauté, capture rapidement des entreprises alignées avec ses valeurs et besoins, puis reçoit des alertes ciblées pour postuler efficacement.

## Success Metrics

**User success metrics**
- Nombre d’entreprises suivies
- Nombre de fiches complétées
- Nombre d’annonces qualifiées (pertinentes)
- Nombre de contacts LinkedIn initiés
- Nombre de candidatures (CV envoyés)
- Délai moyen entre alerte et candidature

**User success moment**
- Réception régulière (hebdomadaire) d’offres pertinentes provenant des pages carrière suivies

### Business Objectives

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

### Key Performance Indicators

- % d’offres pertinentes sur le total d’alertes
- Délai moyen alerte → candidature
- Taux de complétion des fiches entreprises
- Nombre de candidatures envoyées via l’outil
- Nombre d’entreprises actives suivies

## MVP Scope

### Core Features

- Enregistrement ultra‑rapide d’entreprises/offres (capture < 20s)
- Backoffice pour compléter les fiches (avec rappels)
- Alertes sur nouvelles offres pertinentes des entreprises suivies
- Consultation centralisée des entreprises/offres enregistrées

### Out of Scope for MVP

- Scraping avancé des infos entreprises (auto‑préremplissage complet)
- Intégration Glassdoor
- Organisation avancée (tags, dossiers, sous‑dossiers)
- Partage public/communautaire
- Gamification
- Génération de CV/LM personnalisés
- Chatbot/conseiller d’orientation

### MVP Success Criteria

- 15 entreprises enregistrées
- Capture < 20s
- 80% des fiches complétées

### Future Vision

- Scraping enrichi (infos entreprise + avis Glassdoor)
- Organisation avancée (tags/dossiers)
- Partage public/privé et collaboration
- Gamification du processus
- Génération de CV/LM adaptés aux annonces
- Chatbot de conseil et scoring de compatibilité
