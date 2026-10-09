# Model: Hybrid (Combining Models)

> **What:** Using different organizing models at different levels or in different parts of the docs. This is what most mature projects actually do.
> **Read when:** no single model fits, or your project has grown past a simple structure.

## TL;DR

- A hybrid is fine, and usually best, **as long as each level follows one rule** and the rules are written down.
- Proven combinations: **Type → Domain**, **Audience → Diátaxis**, **Central + co-located**, **Type with sequential sub-folders**.
- Write the rules in the docs-root `README.md` under a "How these docs are organized" heading.
- Don't mix dimensions **within the same level**: `architecture/`, `billing/` and `users/` as siblings is a red flag.

---

## The golden rule: one dimension per level

```
✅  docs/<TYPE>/<DOMAIN>/file.md
    docs/requirements/billing/refund-rules.md
    docs/operations/runbooks/billing/stripe-down.md

❌  docs/
    ├── architecture/     ← type
    ├── billing/          ← domain
    ├── users/            ← audience
    └── old/              ← lifecycle
```

The ❌ version forces every writer to choose between equally valid folders, and every reader to check all of them.

**Allowed exception:** cross-cutting folders that are clearly special, like `_shared/`, `archive/` and `glossary.md`, can sit alongside the others.

---

## Proven hybrid patterns

### 1. Type → Domain (most common for product teams)

```
docs/
├── getting-started/
├── architecture/
│   ├── overview.md
│   └── decisions/                 sequential
├── requirements/
│   ├── billing/                   domain
│   ├── catalog/
│   └── rules/
├── api/
└── operations/
    ├── runbooks/
    │   ├── billing/               domain
    │   └── platform/
    └── postmortems/               dated
```

Use this when one product has several domains and readers think in doc types first.

### 2. Audience → Diátaxis (product with public docs)

```
docs/
├── user-guide/            public, end users
│   ├── tutorials/
│   ├── how-to/
│   ├── reference/
│   └── concepts/
├── developer-guide/       public, integrators
│   ├── quick-start.md
│   ├── guides/
│   └── api-reference/
└── internal/              not published
    ├── architecture/
    ├── decisions/
    └── runbooks/
```

Use this for SaaS products and platforms with external users and integrators.

### 3. Central + co-located (monorepo)

```
repo/
├── README.md                  map of everything
├── docs/                      cross-cutting, type-based
│   ├── architecture/
│   ├── conventions/
│   └── decisions/
└── services/
    └── billing/
        ├── README.md          co-located
        └── docs/
            ├── runbooks/
            └── decisions/
```

Use this for monorepos and modular monoliths. Rule: **"If it's about one module, put it in the module. If it's about two or more, put it in `docs/`."**

### 4. Domain → Type (large, team-aligned product)

```
docs/
├── _shared/                   getting started, conventions, glossary
├── billing/
│   ├── README.md
│   ├── requirements/
│   ├── architecture.md
│   ├── decisions/
│   └── runbooks/
└── catalog/
    └── ...
```

Use this when each team owns a domain end to end. Add cross-domain index pages (all runbooks, all ADRs).

### 5. Lifecycle inside type (spec-heavy teams)

```
product/
├── README.md                  index with status column
├── features/
│   ├── partial-refunds/       status: in-development
│   └── multi-currency/        status: draft
└── archive/                   shipped & superseded specs
```

Use this for product teams with many specs. Living rules move to `requirements/rules/` once a feature ships.

---

## Writing down the rules

Put this in the docs root `README.md`:

```markdown
## How these docs are organized

- **Top level = doc type.** One folder per kind of document.
- **Second level = domain** (billing, catalog, identity) when a folder has >15 files.
- **ADRs** are numbered `NNNN-title.md` in `architecture/decisions/`.
- **Postmortems** are dated `YYYY-MM-DD-title.md`.
- **Module docs** live next to the code in `services/<name>/README.md`.
- **Status** is in front matter, not in folder names. Dead docs go to `archive/`.
- Not sure where something goes? Ask in #docs or put it in the closest folder and flag it in the PR.
```

---

## Hybrid decision table

| Situation | Recommended hybrid |
|---|---|
| One product, 2–5 teams, internal docs | Type → Domain (#1) |
| Product with public user docs | Audience → Diátaxis (#2) |
| Monorepo | Central + co-located (#3) |
| Large product, teams own domains end to end | Domain → Type (#4) + cross-domain indexes |
| Many feature specs | Lifecycle inside type (#5) |
| Polyrepo | [Per-service repos](per-service-repo.md) + handbook repo using #1 |

---

**Related:** [dimensions](../dimensions.md) · [folder-structures](../folder-structures.md) · [decision-guide](../../choosing-structure/decision-guide.md)
**Up:** [Organizing](../README.md)
