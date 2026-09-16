# RECLAIM

RECLAIM is a Christian recovery and support application focused on helping people break free from gambling addiction and rebuild their lives through faith, structure, accountability, and practical recovery tools.

## Repository status

This repository is being initialized as the source of truth for the RECLAIM product, technical architecture, design system, implementation specifications, and application code.

The first phase is **Foundation / Sprint 0**. The goal is to establish a clean repository structure and development foundation before implementing the P0 screens.

## Planned repository structure

```text
reclaim/
├── README.md
├── docs/
│   ├── product/
│   ├── architecture/
│   ├── design-system/
│   ├── screens/
│   ├── api/
│   ├── database/
│   ├── security/
│   ├── testing/
│   ├── deployment/
│   └── decisions/
├── apps/
│   ├── web/
│   └── api/
├── packages/
└── infra/
```

## Documentation-first approach

The repository will keep product and engineering decisions documented before they become implementation assumptions. Existing project specifications will be added and reviewed before the application architecture is treated as final.

## Development principles

- Mobile-first, accessible UX
- Clear separation between product, frontend, backend, and infrastructure concerns
- Versioned API contracts
- Secure handling of authentication and user data
- Testable application behavior
- Small, reviewable commits
- Documentation as part of the implementation process

## Current milestone

**Foundation / Sprint 0 — repository bootstrap**

Next steps are to add the approved RECLAIM specifications, establish the development environments, and then implement the foundation before moving to the 18 P0 screens.
