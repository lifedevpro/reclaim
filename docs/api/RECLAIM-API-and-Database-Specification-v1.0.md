# RECLAIM API + Database Specification v1.0

**Status:** Foundation baseline

## API

Base namespace: `/api/v1`

Initial authentication endpoints:
- POST `/api/v1/auth/register`
- POST `/api/v1/auth/login`
- POST `/api/v1/auth/logout`
- GET `/api/v1/me`

Successful resources use a consistent `data` envelope. Collections may include `meta`. Validation/application errors use a consistent message/errors structure. Timestamps are UTC and exposed as ISO 8601.

## Backend flow

Route -> Controller -> Form Request -> Action/Service -> Domain rules -> Model/Repository -> API Resource

Controllers remain thin. Authorization is enforced server-side.

## Authentication

Laravel Sanctum. Authentication is independent of the Next.js client so future mobile clients can consume the same API.

## Identifiers

Application-facing resource identifiers use UUIDs. Sequential database IDs must not become public identifiers.

## Core data

Foundation includes users, profiles, authentication infrastructure, and the supporting audit/event and queue infrastructure. Recovery-domain entities are added when their requirements are explicitly specified.

## Content boundary

Editorial content is accessed through an application/content abstraction rather than exposing a CMS schema. A future Strapi installation may become the content source without clients knowing Strapi collection names.

## Database rules

PostgreSQL is the system of record for core application data. Use foreign keys, constraints, appropriate indexes, version-controlled migrations, and safe seed data. Sensitive values are not stored in plaintext unless explicitly justified.

## API stability

`/api/v1` remains backwards compatible unless an explicit breaking-change decision creates a new version.

## Time and locale

Store timestamps in UTC. User timezone and locale are explicit preferences.

## Future clients

Web and future Mobile clients consume the same API. No client accesses PostgreSQL directly.