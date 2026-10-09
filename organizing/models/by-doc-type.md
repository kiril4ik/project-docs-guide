# Model: Organize by Doc Type

> **What:** Top-level folders are named after the *kind* of document: architecture, API, requirements, operations, guides.
> **Read when:** you have one product and one or a few teams, and readers usually know what *kind* of doc they want.

## TL;DR

- The **most common and intuitive** model, and the default recommendation for small and medium projects.
- Works because readers usually think "I need *the runbook*" or "*the API docs*".
- Weak spot: as the product grows, each type folder mixes all domains. Fix this by adding **domain subfolders** (→ [hybrid](hybrid.md)).

---

## What it looks like

```
docs/
├── README.md                 index + "who is this for"
├── getting-started/          setup, first run, troubleshooting
├── architecture/
│   ├── README.md             overview + diagrams
│   └── decisions/            ADRs (sequential)
├── api/                      reference + guides
├── requirements/             PRDs, stories, business rules
├── development/              conventions, testing, release process
├── operations/               deployment, runbooks, postmortems
└── glossary.md
```

## Typical top-level folders

| Folder | Holds | See |
|---|---|---|
| `getting-started/` | Setup, onboarding, first steps | [developer-docs](../../doc-types/developer-docs.md) |
| `architecture/` | Overview, diagrams, ADRs, data model | [architecture-docs](../../doc-types/architecture-docs.md) |
| `api/` | API reference, guides, webhooks | [api-docs](../../doc-types/api-docs.md) |
| `requirements/` or `product/` | BRD, PRDs, stories, rules, NFRs | [business-requirements](../../doc-types/business-requirements.md) |
| `development/` | Conventions, testing, tooling | [developer-docs](../../doc-types/developer-docs.md) |
| `operations/` | Deploy, config, runbooks, postmortems | [operations-docs](../../doc-types/operations-docs.md) |
| `guides/` or `user-guide/` | End-user docs | [user-docs](../../doc-types/user-docs.md) |
| `rfcs/` or `design/` | Proposals / design docs | [architecture-docs](../../doc-types/architecture-docs.md#rfcs-and-design-docs) |

Use **only the folders you need**. Empty `requirements/` folders "for later" just add noise.

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Immediately understandable to everyone | Type folders grow large and mix many domains |
| Matches how most people search | Domain ownership is unclear: who owns `requirements/`? |
| Maps cleanly to doc templates (one template per folder) | Info about one feature is spread over 4 folders |
| Easy to start, easy to explain | Some docs fit two types (a design doc with requirements) |

## Best for

- Single product or monolith, 1–3 teams.
- Internal docs where most readers are developers.
- Projects starting their docs from scratch.

## Avoid when

- Multiple teams own clearly separate domains (→ [by-domain](by-domain.md) or [hybrid](hybrid.md)).
- Audiences are very different, for example public users and internal engineers (→ [by-audience](by-audience.md)).
- You have dozens of services (→ [co-located](co-located.md), [per-service-repo](per-service-repo.md)).

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| `requirements/` has 60 files with no grouping | Add domain subfolders: `requirements/billing/` |
| A `misc/` or `other/` folder appears | A doc type is missing or the doc isn't needed. Decide which. |
| Feature info is hard to piece together | Add a per-domain index page that links across type folders |
| "Is this architecture or development?" debates | Write a one-line rule for each folder in `docs/README.md` |

## Migrating

- **To this model** (from a flat folder): create type folders, move files, add a README index per folder, and fix links (see [evolving-structure](../../choosing-structure/evolving-structure.md)).
- **From this model to hybrid:** keep type at the top and add domain subfolders only in folders with more than ~15 files.

---

**Related:** [by-domain](by-domain.md) · [hybrid](hybrid.md) · [folder-structures](../folder-structures.md)
**Up:** [Organizing](../README.md)
