# RECLAIM Testing Foundation v1.0

**Status:** Foundation baseline

## Test layers

### Backend
Use Pest for Laravel unit and feature tests covering authentication, validation, authorization, API contracts, domain/application rules, and database behavior.

### Frontend
Use Vitest and Testing Library for components, forms, validation behavior, API states, navigation-critical behavior, and accessibility-critical states.

### End-to-end
Use Playwright for critical journeys. Foundation E2E: registration, login, authenticated profile/me, logout. P0 E2E expands with each implemented screen.

## Principles

Test observable behavior rather than implementation details. Keep unit tests fast. Use realistic API contracts. Cover success, loading, empty, validation-error, authorization-error, and server-error states where relevant. Prefer accessible roles and labels over brittle selectors.

## Quality gates

Every Foundation change should pass lint, typecheck, backend tests, frontend tests, production build, and relevant E2E tests.

## Acceptance

A feature is not complete merely because the happy path works. Its documented validation, authorization, error, and accessibility behavior must also be covered.