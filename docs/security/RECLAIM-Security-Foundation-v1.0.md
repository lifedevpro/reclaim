# RECLAIM Security Foundation v1.0

**Status:** Foundation baseline

## Principles

Security is part of Foundation, not a later hardening phase.

## Authentication

- Laravel Sanctum
- secure session/token handling appropriate to the client
- logout invalidates applicable authentication state
- authentication errors do not reveal sensitive account information

## Authorization

Every protected resource is authorized server-side. Frontend route guards are UX controls, not security controls.

## Input security

Validate all API input server-side, use allow-listed validation, parameterized ORM/query access, context-appropriate output escaping/sanitization, and never trust client-supplied ownership or authorization fields.

## Secrets

`.env` files are not committed. Production secrets use deployment secret storage. No credentials, tokens, private keys, or API secrets in source control.

## API protection

Rate-limit abuse-sensitive endpoints, use HTTPS in deployed environments, return safe structured errors, and do not leak stack traces or internal details.

## Data protection

Minimize collected personal data. Logs must not contain passwords, authentication tokens, sensitive recovery notes, or unnecessary personal information.

## Dependencies

Keep lockfiles committed and review security advisories during maintenance.

## Uploads

Future uploads must validate type, size, storage location, and authorization. Uploaded content must never become executable application code.

## Auditability

Security-sensitive actions should produce appropriate audit events without storing sensitive payloads unnecessarily.

## Security gate

Foundation is incomplete until authentication, authorization, validation, secret handling, error handling, and dependency/security checks are tested.