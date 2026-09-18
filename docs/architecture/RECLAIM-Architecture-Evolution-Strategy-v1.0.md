# RECLAIM Architecture Evolution Strategy v1.0

**Status:** Accepted architectural direction  
**Scope:** MVP through future platform expansion

## 1. Principle

RECLAIM is being built as an MVP first, not as the complete future platform.

The MVP must remain small enough to develop and validate quickly while establishing architectural boundaries that support future Web, Mobile, and Admin/CMS clients without a fundamental backend rewrite.

## 2. MVP architecture

    Next.js Web
         |
         v
    Laravel REST API
         |
         v
      PostgreSQL
         ^
         |
    Redis / queues

The Web application is the first client, not the definition of the backend architecture.

## 3. Future client model

    RECLAIM Backend
           |
    Laravel API / Domain
           |
     +-----+-----+-----+
     |           |     |
    Web        Mobile  Admin/CMS
  Next.js    iOS/Android Strapi/
                       Filament

The exact mobile framework and CMS/admin product remain future implementation decisions.

## 4. Mobile strategy

A future mobile application must consume the same versioned RECLAIM API rather than access PostgreSQL directly.

The backend must expose authentication, user/profile data, recovery/application data, content, actions/state transitions, validation, and error contracts through stable API contracts.

The API must not contain assumptions specific to browser rendering or Next.js.

## 5. Admin/CMS strategy

RECLAIM may eventually require a dedicated content management platform or a Laravel-native administration panel.

### Strapi
Potentially suitable for content-heavy workflows such as Bible content, prayers, devotionals, recovery lessons, educational articles, translations, media, and structured editorial content.

### Filament
Potentially suitable for Laravel-native administration of application/domain data and operational workflows.

The Foundation does not select Strapi or Filament as the final CMS/admin platform. The current architectural requirement is that the application does not become tightly coupled to either one.

## 6. Application data vs content

### Application/domain data
Examples: users, profiles, recovery progress, check-ins, goals, streaks, achievements, accountability, notifications, and user preferences.

These belong to the core application/domain model.

### Editorial content
Examples: Bible verses, prayers, devotionals, recovery lessons, educational content, challenges, translations, and media.

The content source may evolve independently.

## 7. Content abstraction

Clients should consume normalized RECLAIM API resources rather than know the underlying CMS schema.

Example:

    {
      "id": "prayer-001",
      "type": "prayer",
      "title": "Morning Prayer",
      "body": "...",
      "language": "en"
    }

The client must not depend directly on Strapi collection names, WordPress tables, or internal Laravel database structures.

## 8. Architectural rule

**Mobile-ready does not mean mobile-first implementation.**

The MVP remains Web-first from a delivery perspective while the backend remains client-agnostic.

## 9. Evolution path

### Phase 1 — MVP
- Next.js Web
- Laravel API
- PostgreSQL
- Redis
- Foundation authentication
- core MVP flows

### Phase 2 — Product expansion
- additional recovery features
- richer content model
- notifications
- additional API resources
- stronger admin workflows

### Phase 3 — Platform expansion
- mobile client(s)
- dedicated content management if justified
- advanced administration
- multilingual content workflows
- additional RECLAIM clients/integrations

## 10. Decision rule

Future technologies should be introduced only when they solve a demonstrated product or operational requirement.

The architecture should provide extension points without implementing future complexity prematurely.
