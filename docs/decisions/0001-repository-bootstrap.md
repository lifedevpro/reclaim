# ADR 0001 — Repository Bootstrap

**Status:** Accepted

## Context

The RECLAIM GitHub repository was created as an empty private repository. The project already has product and UI planning work, but the exact contents of the previously prepared specifications should not be reconstructed as if they were already committed source files.

## Decision

Initialize the repository with a documentation-first structure and a minimal project README. Keep implementation architecture decisions provisional until the relevant RECLAIM Foundation specifications are added and reviewed.

## Initial structure

- `docs/` for product and engineering specifications
- `apps/` for executable applications
- `packages/` for shared code
- `infra/` for infrastructure and deployment configuration

## Consequences

The repository is immediately usable as the project source of truth without prematurely locking the implementation to assumptions that have not yet been committed as specifications.
