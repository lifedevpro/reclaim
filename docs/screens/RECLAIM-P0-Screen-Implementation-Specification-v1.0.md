# RECLAIM P0 Screen Implementation Specification v1.0

**Status:** Foundation baseline

## Purpose

This document turns the 18 P0 UX screens into implementation contracts for developers and AI coding agents.

Every screen follows:

**Route -> Page -> Components -> API -> DB -> State Machine -> Validation -> Actions -> Navigation -> Error Handling -> Acceptance Criteria -> Agent Implementation Notes**

## Global rules

- Protected screens require authentication.
- UI never accesses PostgreSQL directly.
- Server state uses TanStack Query.
- Forms use React Hook Form + Zod.
- Backend validation is authoritative.
- Loading, empty, success, and failure states are explicit.
- Accessibility follows the UI Design System.
- API base path is `/api/v1`.

## Per-screen contract

### Route
Canonical Next.js route.

### Page
Page responsibility and authentication boundary.

### Components
Reusable design-system components and screen-specific composition.

### API
Exact endpoint, HTTP method, request, response, and error contract.

### DB
Domain entities read or changed. Frontend never depends on physical table names.

### State Machine
Explicit states and transitions, including loading, success, empty, validation failure, authorization failure, and recoverable server failure.

### Validation
Client and server validation rules.

### Actions
User-triggered mutations and side effects.

### Navigation
Allowed entry points and destinations after actions.

### Error handling
Inline validation, recoverable errors, retry behavior, and authentication failures.

### Acceptance criteria
Observable behavior required for completion.

### Agent implementation notes
Files/components, constraints, tests, and forbidden shortcuts.

## P0 implementation rule

The canonical approved 18-screen UX specification remains the source of truth for exact screen names, routes, and content. Agents must not invent missing screen definitions from memory.

## Foundation gate

No P0 screen is implementation-complete until its API, state, validation, error handling, tests, and acceptance criteria are documented and verified.