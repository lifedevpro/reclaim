# RECLAIM — AI Agent Instructions

## Mission

Build RECLAIM according to committed product and engineering specifications. Prefer small, verifiable changes over speculative architecture.

## Required reading

Before changing code, read the relevant docs plus:
- `docs/architecture/RECLAIM-Foundation-v1.0-Technical-Specification.md`
- `docs/architecture/RECLAIM-Architecture-Evolution-Strategy-v1.0.md`
- the relevant screen/API/design-system specification

## Architecture rules

- MVP is Web-first.
- Backend is API-first and client-agnostic.
- Web: Next.js + React + TypeScript.
- API: Laravel REST/JSON.
- Database: PostgreSQL.
- API namespace: `/api/v1`.
- Authentication: Laravel Sanctum.
- Server state: TanStack Query.
- Forms: React Hook Form + Zod.
- Styling: Tailwind CSS.
- Never access PostgreSQL from the frontend.
- Keep controllers thin and business rules outside UI/controllers.
- Follow documented API contracts.

## Future compatibility

Do not build Mobile, Strapi, or Filament into the MVP unless explicitly requested. Do not create architecture that prevents future iOS/Android clients, Strapi editorial content, Filament/Laravel-native administration, multilingual content, or additional clients.

## P0 rule

Do not implement P0 screens from memory. Read the corresponding specification first. Each screen follows: Route -> Page -> Components -> API -> DB -> State Machine -> Validation -> Actions -> Navigation -> Error Handling -> Acceptance Criteria -> Agent Notes.

## Security

Never commit secrets. Validate on the server. Enforce authorization server-side. Do not expose sensitive information in logs or errors.

## Testing

Behavior changes require tests. Before completion run relevant lint, typecheck, tests, build, and E2E checks.

## Git discipline

Keep commits small and focused. Do not mix unrelated refactors with features. Do not rewrite committed history unless explicitly requested. Never commit generated secrets or local environment files.

## Decision discipline

If a requirement is unspecified, inspect existing docs and ADRs first. If still ambiguous, document the assumption or ask before introducing a foundational decision.

## Foundation gate

Sprint 0 establishes local development, Web/API skeleton, database connectivity, authentication foundation, API conventions, design-system foundation, testing infrastructure, environment configuration, and CI. Only after the Foundation gate passes should the 18 P0 screens be implemented systematically.