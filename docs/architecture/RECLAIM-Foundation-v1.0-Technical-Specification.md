# RECLAIM Foundation v1.0 — Technical Specification

**Status:** Foundation baseline  
**Scope:** MVP / Sprint 0 foundation  
**Version:** 1.0

## 1. Purpose

RECLAIM Foundation defines the technical baseline for the first working MVP while preserving architectural boundaries for future mobile clients, administration, CMS/content management, multilingual content, and additional RECLAIM products.

The MVP is intentionally limited in product scope. The architecture must not require a fundamental backend rewrite when future clients are introduced.

## 2. Technical baseline

| Area | Foundation decision |
|---|---|
| Web | Next.js App Router + React + TypeScript |
| Styling | Tailwind CSS |
| API | Laravel REST/JSON API |
| API version | /api/v1 |
| Authentication | Laravel Sanctum |
| Database | PostgreSQL |
| Cache / queues | Redis |
| Web data fetching | TanStack Query |
| Forms / validation | React Hook Form + Zod |
| Backend validation | Laravel Form Requests |
| Backend ORM | Laravel Eloquent |
| Testing | Pest, Vitest, Testing Library, Playwright |
| Local/dev infrastructure | Docker |
| Reverse proxy | Nginx |
| CI | GitHub Actions |

## 3. Architecture principles

### API-first
The frontend communicates with the backend through versioned API contracts. The frontend must not depend directly on database tables.

### Client-agnostic backend
Laravel domain/application logic must not assume requests originate from Next.js. Future mobile clients must be able to consume the same API.

### Separation of concerns
Target flow:

UI → API → Application layer → Domain rules → Persistence

Controllers should remain thin. Business rules must not be embedded in React components or HTTP controllers.

### Contract-first integration
API response structures, validation rules, authentication behavior, and error semantics should be documented and kept stable within an API version.

### Security by default
Secrets are environment-specific and never committed. Authentication, authorization, validation, rate limiting, auditability, and safe error handling are foundation concerns.

## 4. API contract

Base path: /api/v1

Successful responses use a consistent data/meta shape where appropriate.

Errors use a consistent error structure containing machine-readable information suitable for frontend and future mobile clients.

Public-facing resource identifiers should use UUIDs rather than exposing sequential database IDs as application identifiers.

## 5. Authentication

The Foundation uses Laravel Sanctum.

Initial Foundation flow:
1. Registration
2. Login
3. Authenticated profile
4. Logout

Authentication is implemented independently of the Web UI so the same backend can later support mobile clients.

## 6. Foundation data model

Initial database foundation includes:
- users
- profiles
- authentication/token infrastructure required by Sanctum
- audit/event infrastructure
- queue infrastructure required by the application

Business-domain tables are introduced only when their requirements are defined.

## 7. State and validation

- Server state: TanStack Query
- Form state: React Hook Form
- Client validation: Zod
- Backend validation: Laravel Form Requests
- Business invariants: application/domain layer

Validation must never rely exclusively on the client.

## 8. Testing baseline

- Backend unit/feature tests with Pest
- Frontend unit/component tests with Vitest and Testing Library
- End-to-end critical-flow coverage with Playwright
- Linting
- Type checking
- Production build verification

## 9. CI baseline

GitHub Actions should validate pull requests and main-branch changes with deterministic checks for dependency installation, lint, typecheck, backend tests, frontend tests, build, and relevant integration/e2e checks.

## 10. Explicit non-goals for Foundation

The Foundation does not prematurely implement:
- all 18 P0 screens
- a mobile application
- Strapi
- Filament
- GraphQL
- microservices
- Kubernetes
- AI services
- unnecessary infrastructure complexity

## 11. Future compatibility requirement

Although mobile and CMS/admin functionality are not implemented in Foundation, all core contracts must remain compatible with them.

See docs/architecture/RECLAIM-Architecture-Evolution-Strategy-v1.0.md.
