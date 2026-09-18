# RECLAIM Foundation v1.0 — Repository & File Structure Specification

**Status:** Foundation baseline  
**Version:** 1.0

## 1. Repository model

RECLAIM uses a monorepo structure separating applications, shared packages, infrastructure, and documentation.

    reclaim/
    ├── README.md
    ├── AGENTS.md
    ├── apps/
    │   ├── web/
    │   └── api/
    ├── packages/
    │   ├── ui/
    │   ├── types/
    │   └── config/
    ├── infra/
    ├── scripts/
    ├── docs/
    │   ├── product/
    │   ├── architecture/
    │   ├── design-system/
    │   ├── screens/
    │   ├── api/
    │   ├── database/
    │   ├── authentication/
    │   ├── state/
    │   ├── security/
    │   ├── testing/
    │   ├── deployment/
    │   └── decisions/
    ├── tests/
    ├── .github/
    └── package.json

## 2. Web application

apps/web/

Responsibilities:
- Next.js App Router
- React UI
- Tailwind styling
- client-side form handling
- API consumption
- server-state management
- accessibility
- frontend tests

The Web application must not contain backend business rules.

## 3. API application

apps/api/

Responsibilities:
- Laravel REST API
- authentication
- authorization
- application/domain logic
- persistence
- validation
- events/jobs
- API resources
- backend tests

## 4. Shared packages

packages/ui/ — reusable UI primitives where sharing is justified.

packages/types/ — shared API/domain types and generated/contract types where appropriate.

packages/config/ — shared development and tooling configuration.

Shared packages must remain dependency-light and must not create circular dependencies between applications.

## 5. Infrastructure

infra/ contains reproducible local/deployment infrastructure.

Foundation development uses Docker-based services as required for Web, API, PostgreSQL, Redis, and development mail.

Production infrastructure must be environment-specific and must never commit secrets.

## 6. Documentation

Documentation is part of the implementation contract.

Important documents include architecture, API, database, authentication, state, design system, security, testing, deployment, screen implementation specifications, and Architecture Decision Records.

## 7. Package management

The JavaScript workspace uses pnpm.

The repository must keep lockfiles committed and dependencies reproducible.

## 8. Environment files

Secrets and environment-specific values are not committed.

Commit safe templates such as .env.example where needed.

## 9. GitHub Actions

.github/ contains CI workflows for deterministic quality gates.

At minimum the Foundation CI should cover linting, type checking, tests, and production builds.

## 10. Codex / AI-agent contract

AI coding agents must:
1. read the relevant specification before implementation;
2. follow the repository structure;
3. not invent architecture when a specification exists;
4. not implement P0 screens before the Foundation gate;
5. preserve API contracts;
6. avoid committing secrets;
7. keep changes small and reviewable;
8. add or update tests for behavior changes.

## 11. Foundation gate

Foundation is ready for P0 implementation when:
- repository structure is established;
- development environments run locally;
- API and Web applications communicate;
- database connectivity is working;
- authentication foundation works;
- lint/typecheck/tests/build pass;
- CI is operational;
- documentation and architectural decisions are committed.
