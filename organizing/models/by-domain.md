# Model: Organize by Domain / Feature

> **What:** Top-level folders are business domains, bounded contexts or features (billing, auth, catalog). Each domain folder holds all doc types about that domain.
> **Read when:** several teams each own a part of the product, or readers mostly think in terms of features.

## TL;DR

- Everything about **billing** is in `billing/`: rules, API, architecture, runbooks.
- Mirrors **team ownership** (Conway's law). Each team owns its folder, which you can enforce with `CODEOWNERS`.
- Weak spot: **cross-cutting docs** (setup, overall architecture, conventions) have no natural home. Add a `platform/` or `_shared/` area for them.
- Pairs well with domain-driven design and modular monoliths.

---

## What it looks like

```
docs/
├── README.md                  index of domains + cross-cutting docs
├── _shared/                   cross-cutting (underscore sorts it first)
│   ├── getting-started.md
│   ├── architecture-overview.md
│   ├── conventions.md
│   └── glossary.md
├── billing/
│   ├── README.md              what this domain does, owner, key links
│   ├── requirements.md        PRD / stories / scope
│   ├── rules.md               business rules (BR-BIL-xx)
│   ├── architecture.md        internals, diagrams
│   ├── api.md                 or link to generated reference
│   ├── decisions/             domain-scoped ADRs
│   └── runbooks/
├── catalog/
│   └── ...
└── identity/
    └── ...
```

Each domain folder uses the **same internal layout**. Write that down as a template so that each domain doesn't invent its own.

### Domain README pattern

```markdown
# Billing

Handles subscriptions, invoices, payments and refunds.

- **Owner:** team-billing (#billing on Slack)
- **Code:** `src/Billing/`, `services/billing-api/`
- **Depends on:** identity, catalog
- **Key docs:** [Rules](rules.md) · [API](api.md) · [Runbooks](runbooks/README.md)
```

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Clear ownership: one team ↔ one folder | Cross-cutting docs need a separate home |
| All knowledge about a feature in one place | Readers looking for "all runbooks" must visit every domain |
| Scales with the number of teams/domains | Domain boundaries change, and moving folders breaks links |
| Matches code structure in modular/DDD codebases | New readers may not know domain names yet (needs a good index + glossary) |

## Best for

- Products with **3+ teams** owning distinct areas.
- Domain-driven design, modular monoliths.
- **Business/requirements docs**, which are naturally discussed per domain.
- Large requirement sets (as the secondary dimension under `requirements/`).

## Avoid when

- Small team, small product: domains would be 1–2 files each.
- Domains aren't stable yet (early startup pivoting).
- Most readers are on-call engineers who need **all runbooks together**. Add a cross-domain runbook index, or keep runbooks type-based.

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| Each domain folder has a different layout | Add a domain-folder template; check in review |
| Shared docs duplicated in every domain | Move to `_shared/` and link |
| "Where are all the ADRs?" | Generate or maintain a cross-domain index (`decisions-index.md`) |
| Domain renamed in code but not in docs | Keep domain names in the glossary; rename via a migration PR |

## Variants

- **Domain at the second level** (most common): `requirements/billing/`, `operations/runbooks/billing/`. See [hybrid](hybrid.md).
- **Feature folders for product specs:** `product/features/partial-refunds/{prd.md, stories.md, designs.md}`, archived when shipped.
- **Domain docs co-located** in the code module: `src/Billing/docs/`. See [co-located](co-located.md).

## Migrating

- **To this model:** define the domain list (match code modules and teams), create `_shared/`, move docs, add a `README.md` per domain and set up `CODEOWNERS`.
- **Away from it:** if domains are tiny, collapse them into [by-doc-type](by-doc-type.md) with domain-named files (`requirements/billing.md`).

---

**Related:** [hybrid](hybrid.md) · [co-located](co-located.md) · [business-requirements](../../doc-types/business-requirements.md)
**Up:** [Organizing](../README.md)
