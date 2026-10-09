# Model: Organize by Lifecycle / Status

> **What:** Folders (or metadata) reflect where a document is in its life: draft, proposed, active, shipped, deprecated, archived.
> **Read when:** you have many documents that change status, such as RFCs, specs, PRDs or policies, or old docs are cluttering current ones.

## TL;DR

- Lifecycle is almost always a **secondary pattern**, used *inside* a folder like `rfcs/` or `product/`, rather than a project-wide top level.
- Prefer **status in front matter** over status folders. Moving files breaks links.
- **One exception:** a physical `archive/` folder for long-dead docs is fine, and it keeps current folders clean.
- Always show status visibly at the top of the doc, not only in metadata.

---

## Two ways to express lifecycle

### A. Status folders

```
rfcs/
├── README.md
├── drafts/
│   └── multi-currency.md
├── accepted/
│   └── 0041-event-sourcing-orders.md
├── rejected/
│   └── 0039-graphql-gateway.md
└── archive/
    └── 0012-legacy-sync.md
```

### B. Status in metadata (recommended)

```
rfcs/
├── README.md                     index table with status column
├── 0039-graphql-gateway.md       status: rejected
├── 0041-event-sourcing-orders.md status: accepted
├── 0042-multi-currency.md        status: draft
└── archive/                      only for things nobody should read anymore
```

```markdown
---
id: RFC-0042
title: Multi-currency support
status: draft            # draft | review | accepted | rejected | withdrawn | implemented
owner: "@anna"
created: 2026-09-20
updated: 2026-10-05
---

# RFC-0042: Multi-currency support

> **Status:** 🟡 Draft. Open for comments until 2026-10-20.
```

| | Status folders | Status metadata |
|---|---|---|
| Browsing by status | ✅ Easy | Needs index table or tooling |
| Stable links | ❌ Links break on every move | ✅ Path never changes |
| Git history per file | ⚠️ Rename noise | ✅ Clean |
| Works with AI agents/search | Both fine | ✅ Status grep-able: `grep "status: accepted"` |

## Common lifecycles

| Doc type | Lifecycle |
|---|---|
| RFC / design doc | draft → review → accepted / rejected / withdrawn → implemented |
| ADR | proposed → accepted / rejected → deprecated / superseded |
| PRD / feature spec | draft → approved → in development → shipped → archived |
| Policy | draft → approved → active → under review → retired |
| Guide / reference | draft → active → deprecated → removed |
| Postmortem | draft → reviewed → published (immutable) |

## Status banners

Make status visible to readers who never look at metadata:

```markdown
> [!WARNING]
> **Deprecated** since 2026-06. Replaced by [Payments v2 guide](../v2/payments.md).
> This page will be removed after 2027-01.
```

```markdown
> 📦 **Archived.** Kept for history. Describes the system as of 2024; do not use for current work.
```

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Current docs aren't buried under dead ones | Status folders break links |
| Clear where each proposal stands | Status gets stale if nobody updates it |
| Makes review workflows explicit | Adds overhead for docs that are simply "living" |

## Best for

- RFCs, design docs, PRDs, feature specs, policies.
- Large business-requirements sets where shipped specs pile up.
- Cleaning up legacy docs (an `archive/` folder).

## Avoid when

- Docs are "living" (README, guides, reference). They're simply current, or they get deleted.
- As a project-wide top level (`active/`, `archive/`), because it hides every other dimension.

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| Everything is "draft" forever | Add status to review checklist; [maintenance](../../writing/maintenance.md) |
| Archived docs still rank first in search | Exclude `archive/` from site search; add banners |
| Broken links after moving to `accepted/` | Switch to metadata status, or add redirects |

---

**Related:** [sequential-and-dated](sequential-and-dated.md) · [navigation-and-metadata](../navigation-and-metadata.md) · [architecture-docs](../../doc-types/architecture-docs.md)
**Up:** [Organizing](../README.md)
