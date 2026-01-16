---
stepsCompleted: [1, 2, 3, 4, 5]
lastStep: 2
inputDocuments:
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/prd.md"
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/ux-design-specification.md"
  - "/home/tjoyeux/repo/bmad_method/job_tracker_assistant/_bmad-output/planning-artifacts/product-brief-job_tracker_assistant-2026-01-11.md"
workflowType: 'architecture'
project_name: 'job_tracker_assistant'
user_name: 'Tjoyeux'
date: '2026-01-12'
---

# Architecture Decision Document

_This document builds collaboratively through step-by-step discovery. Sections are appended as we work through each architectural decision together._

## Project Context Analysis

### Requirements Overview

**Functional Requirements:**
L’application doit permettre la capture ultra-rapide d’entreprises/offres (1–2 clics) avec gestion des doublons et “capture en deux temps”, puis la centralisation et l’enrichissement des fiches. Elle doit surveiller les pages carriere et declencher des alertes filtrees (criteres globaux + par entreprise), proposer des ajustements anti-bruit, et fournir un tableau de bord de suivi. Des parcours admin/support sont requis pour surveiller la qualite des sources, mettre en pause, diagnostiquer les incidents et relancer des alertes test.

**Non-Functional Requirements:**
- Performance: capture < 1s, dashboard < 2s.
- Fiabilite: polling 15–30 min, 95% alertes < 15 min, scraping > 95% avec retries.
- Securite: TLS 1.3, AES-256, isolation stricte par utilisateur.
- Accessibilite: WCAG 2.1 AA.
- Scalabilite: jusqu’a ~500 entreprises et 2000 offres suivies par utilisateur, extensible x10.

**Scale & Complexity:**
- Primary domain: web app full-stack + extension navigateur + pipeline d’alertes/scraping.
- Complexity level: moyenne.
- Estimated architectural components: 6–8 (extension capture, API, ingestion/scraping, scheduler/polling, alerting/notification, dashboard web, stockage, observabilite).

### Technical Constraints & Dependencies

- SPA avec experience fluide, pas de SEO requis.
- Support navigateurs: Chrome/Firefox/Safari/Edge + consultation mobile.
- Quasi temps reel via polling 5–15 min en MVP.
- UX impose un flux de capture asynchrone, feedback immediat, et un dashboard “calme”.

### Cross-Cutting Concerns Identified

- Fiabilite du scraping et monitoring des sources.
- Pertinence des alertes (anti-bruit, ajustements guides).
- Donnees personnelles, isolation par utilisateur et securite.
- Accessibilite (WCAG AA) et performance percue.
- Observabilite/ops pour admin et support.

## Starter Template Evaluation

### Primary Technology Domain

Full-stack web app (SPA/SSR) + extension navigateur + worker d’alertes/scraping.

### Starter Options Considered

- **Next.js (create-next-app)**: base officielle, App Router, TypeScript, ESLint. Ideal pour un MVP full-stack avec infra minimale.
- **T3 Stack (create-t3-app)**: Next.js + tRPC + Prisma + Auth.js. Plus opinionne, plus de pieces a maintenir.
- **Vite React (create vite)**: front uniquement, exige un backend separe (plus d’infra et de couts).

### Selected Starter: Next.js (create-next-app)

**Rationale for Selection:**
- Minimalisme infra pour reduire les frais (full-stack dans un seul projet).
- Compatible avec MUI (spec UX).
- Facile a faire evoluer (ajout d’un worker, API, etc.).

**Initialization Command:**

```bash
npx create-next-app@latest job-tracker-assistant --ts --eslint --app --src-dir
```

**Architectural Decisions Provided by Starter:**

**Language & Runtime:**
- TypeScript + React + Next.js.

**Styling Solution:**
- Baseline CSS; MUI ajoute ensuite (sans lock-in Tailwind).

**Build Tooling:**
- Tooling Next.js standard, App Router.

**Testing Framework:**
- Non inclus par defaut (a ajouter ensuite si besoin).

**Code Organization:**
- Structure Next.js avec `src/`, routing App Router, conventions Next.js.

**Development Experience:**
- Dev server Next.js, hot reload, ESLint.

**Note:** l’initialisation via cette commande sera la premiere story d’implementation.

## Core Architectural Decisions

### Decision Priority Analysis

**Critical Decisions (Block Implementation):**
- Database provider: Supabase (managed Postgres, free tier).
- ORM: Prisma 7.2.0.
- Data validation: Prisma schema + Zod at API boundaries.

**Important Decisions (Shape Architecture):**
- Migration strategy: Prisma Migrate.
- Caching strategy: none for MVP.

**Deferred Decisions (Post-MVP):**
- Application-level caching (e.g., Redis) if throughput grows.

### Data Architecture

- **Database**: PostgreSQL (Supabase managed). Version verified per-instance via `select version()`.
- **Provider**: Supabase free tier to minimize costs; ecosystem advantages (Storage/Auth/Realtime optional).
- **ORM**: Prisma 7.2.0 (latest on npm).
- **Modeling**: Strong typing with Prisma schema for core models (Entreprise, Offre).
- **Validation**: Zod for inbound data (extension scraping, API inputs).
- **Migrations**: Prisma Migrate.
- **Caching**: None for MVP; revisit after scale or latency pressure.

### Authentication & Security

- **Authentication**: Supabase Auth (email + OAuth).
- **SDK**: `@supabase/supabase-js` 2.90.1.
- **Authorization**: RLS policies on tables + application-layer checks for critical actions.
- **API Security**: Rate limiting on sensitive endpoints (per IP/user).
- **Encryption**: TLS in transit + encryption at rest handled by Supabase.

### API & Communication Patterns

- **API Style**: REST/JSON via Next.js Route Handlers.
- **Resource Design**: `/api/companies`, `/api/offers`, `/api/alerts`, `/api/captures`.
- **Error Handling**: Standard HTTP status codes with structured JSON error payloads.
- **Rate Limiting**: Per IP/user on sensitive endpoints.

### Frontend Architecture

- **State Management**: React Context + hooks (MVP). Option to evolve to Zustand 5.0.10 if state grows.
- **Forms**: React Hook Form 7.71.1 + Zod 4.3.5 for validation.
- **Data Fetching**: Native `fetch` with a thin wrapper for error handling.

### Infrastructure & Deployment

- **Hosting**: Vercel for web + API.
- **Database**: Supabase (managed Postgres, free tier).
- **Jobs/Scheduler**: Supabase scheduled functions or GitHub Actions cron for MVP.
- **Monitoring**: Sentry free tier (`@sentry/nextjs` 10.34.0) + Vercel logs.

## Implementation Patterns & Consistency Rules

### Pattern Categories Defined

**Critical Conflict Points Identified:**
Naming, structure, API formats, logging, error handling, and loading states.

### Naming Patterns

**Database Naming Conventions:**
- Tables and columns: snake_case (e.g., `companies`, `offers`, `user_id`).
- Foreign keys: `{entity}_id` (e.g., `company_id`).

**API Naming Conventions:**
- REST endpoints are plural: `/api/companies`, `/api/offers`, `/api/alerts`, `/api/captures`.
- Route params use `:id` semantics in code and `id` in URLs.
- JSON payloads use camelCase (e.g., `companyId`, `createdAt`).

**Code Naming Conventions:**
- Components: PascalCase (e.g., `CompanyCard`).
- Files: kebab-case (e.g., `company-card.tsx`).
- Functions/variables: camelCase (e.g., `getCompanyById`).

### Structure Patterns

**Project Organization:**
- `src/app/`: routing and API (Route Handlers).
- `src/features/`: domain features (e.g., `companies`, `offers`, `alerts`, `scraping`).
- `src/lib/`: shared clients and utilities (Supabase, Prisma, helpers).

**File Structure Patterns:**
- Tests are co-located as `*.test.ts(x)` beside source files.
- Feature folders own their components, hooks, and services.

### Format Patterns

**API Response Formats:**
- Standard wrapper: `{ data, error }`.
- Pagination wrapper: `{ data, meta }` with `meta = { totalCount, currentPage, hasNextPage }`.

**Data Exchange Formats:**
- Dates are ISO 8601 strings.
- Booleans are `true/false`.
- Error payloads: `{ error: { code, message, details? } }`.

### Communication Patterns

**Event System Patterns:**
- If internal events are used: `domain.action` (e.g., `alerts.created`).
- Payload: `{ eventId, occurredAt, data }`.

**State Management Patterns:**
- Local feature state via React Context + hooks; avoid cross-feature globals in MVP.
- Data fetching uses `fetch` wrapper with consistent error handling.

### Process Patterns

**Error Handling Patterns:**
- User-facing error: short message + `error.code` reference.
- Log full error context server-side.

**Loading State Patterns:**
- Local loading state per feature.
- Global loading only for route transitions.

### Enforcement Guidelines

**All AI Agents MUST:**
- Follow naming conventions exactly (snake_case DB, camelCase JSON, kebab-case files).
- Use `{ data, error }` and `{ data, meta }` response formats consistently.
- Emit logs in unified format: `{ level, message, requestId, userId, context }`.

**Pattern Enforcement:**
- Add or update tests alongside changes.
- Document deviations in PR or story notes.
- Update this section if a pattern changes.

### Pattern Examples

**Good Examples:**
- DB column: `company_id`; JSON field: `companyId`.
- Endpoint: `GET /api/companies`.
- Log entry: `{ level: "info", message: "capture created", requestId, userId, context }`.

**Anti-Patterns:**
- Mixing `CompanyId` or `company_id` in JSON payloads.
- Singular endpoints like `/api/company`.
- Logs without `requestId`.
