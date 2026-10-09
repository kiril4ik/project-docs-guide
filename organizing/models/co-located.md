# Model: Co-located with Code

> **What:** Docs live right next to the code they describe: a `README.md` in each module, package or service folder, sometimes with a local `docs/` subfolder.
> **Read when:** you have a monorepo, multiple packages, microservices or a component library, or docs keep drifting out of date.

## TL;DR

- **Proximity = freshness.** Developers see the doc when they change the code, and reviewers see both in one PR.
- Every significant module gets a **README**: purpose, owner, how to use and run it, links.
- Weak spot: **no big picture**. Always combine it with a central index or overview (→ [hybrid](hybrid.md)).
- Ideal for **component and module-level** docs. Not suited to business requirements or cross-cutting docs.

---

## What it looks like

### Monorepo

```
repo/
├── README.md                     big picture + map of packages
├── docs/                         cross-cutting only: architecture, conventions, ADRs
├── apps/
│   ├── web/
│   │   ├── README.md
│   │   └── docs/                 app-specific how-tos (optional)
│   └── admin/
│       └── README.md
├── services/
│   ├── billing-api/
│   │   ├── README.md
│   │   ├── openapi.yaml          API reference source
│   │   └── docs/
│   │       ├── runbooks/
│   │       └── decisions/        service-level ADRs
│   └── catalog-api/
│       └── README.md
└── packages/
    ├── ui-kit/
    │   ├── README.md
    │   └── src/Button/Button.mdx   component docs next to component
    └── money/
        └── README.md
```

### Modular monolith

```
src/
├── Billing/
│   ├── README.md          domain overview, rules links, public interfaces
│   ├── Domain/
│   └── Http/
└── Catalog/
    └── README.md
```

## What belongs co-located vs central

| Co-located (next to code) | Central (docs root) |
|---|---|
| Module purpose, public interface, usage | System architecture overview |
| How to run/test this service | Getting started for the whole repo |
| Service config, service runbooks | Coding conventions, contribution process |
| Service-specific ADRs | Cross-cutting ADRs |
| API spec of this service | Business requirements, glossary |
| Component examples (Storybook/MDX) | Onboarding, process docs |

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Docs updated in the same PR as code | Hard to get an overview or browse "all docs" |
| Ownership automatic (code owners = doc owners) | Business people won't find docs inside `src/` |
| Moves/deletes with the code | Inconsistent formats across modules without a template |
| Great for AI agents working on one module | Cross-cutting knowledge has no home (needs central docs) |

## Best for

- Monorepos, microservices in one repo, multi-package libraries.
- Component libraries and design systems (docs next to each component).
- Teams that struggle with stale central docs.

## Avoid when

- It would be the only model in a project with business stakeholders. They need a central, browsable place.
- Modules are tiny or unstable, so READMEs would churn constantly.

## Make it navigable

1. **Root README with a package map:**

   ```markdown
   ## Packages
   | Package | Purpose | Owner |
   |---|---|---|
   | [billing-api](services/billing-api/README.md) | Payments, invoices, refunds | team-billing |
   | [ui-kit](packages/ui-kit/README.md) | Shared React components | team-web |
   ```

2. **Standard module README template.** See [developer-docs](../../doc-types/developer-docs.md#module--package-readme).
3. **Optional aggregation:** a docs site that collects all `**/README.md` and `**/docs/**`, using Backstage TechDocs, the MkDocs monorepo plugin, Docusaurus multi-instance or similar.
4. **Nested agent files:** `services/billing-api/AGENTS.md` for module-specific AI rules.

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| Modules with no README | CI check: every folder in `services/*` must have README.md |
| Every README has different sections | Template + review |
| "Where's the overall architecture?" | Central `docs/architecture/` + root map |

---

**Related:** [per-service-repo](per-service-repo.md) · [hybrid](hybrid.md) · [storage-locations](../storage-locations.md)
**Up:** [Organizing](../README.md)
