# Model: Flat Structure + Metadata (Wiki-style)

> **What:** Few or no folders. Documents sit in one place and are organized by **links, tags and front-matter metadata** instead of hierarchy. This also covers personal and team knowledge systems such as PARA and Zettelkasten-style notes.
> **Read when:** your docs are small (fewer than ~20 pages), you're using a wiki or note tool, or content cuts across categories so much that no tree fits.

## TL;DR

- **Small projects:** a flat folder with good file names is perfectly fine. Don't over-structure 8 files.
- **Larger projects:** a flat structure works **only** with strong metadata, index pages and search. Otherwise it turns into a junk drawer.
- Wikis (Confluence, Notion, GitHub Wiki, Obsidian) often work this way by default.
- Graduate to folders once you pass about 20 files, or once people start asking "where do I put this?"

---

## What it looks like

### Small project (good)

```
docs/
├── README.md              index with one line per doc
├── setup.md
├── architecture.md
├── api.md
├── deployment.md
├── decisions.md           ADRs as sections, or a log table
└── glossary.md
```

### Larger flat set with metadata (OK with discipline)

```
notes/
├── index.md                       generated or curated hub pages
├── billing-refund-rules.md        tags: [billing, rules]
├── billing-stripe-integration.md  tags: [billing, architecture]
├── catalog-search-ranking.md      tags: [catalog, explanation]
└── ...
```

```yaml
---
title: Refund rules
type: business-rules
domain: billing
tags: [refunds, finance]
status: active
---
```

A prefix naming convention (`<domain>-<topic>.md`) gives you **pseudo-folders** that still sort together.

## PARA (for team or personal knowledge bases)

A popular structure for note systems, organized by **actionability**:

| Folder | Contains | Project-docs example |
|---|---|---|
| `projects/` | Efforts with a goal and deadline | `projects/checkout-redesign/` |
| `areas/` | Ongoing responsibilities | `areas/security/`, `areas/on-call/` |
| `resources/` | Reference material on topics | `resources/stripe-api-notes.md` |
| `archive/` | Inactive items from the above | finished projects |

It's good for **team wikis and personal notes**, and less suited to product docs that readers browse by topic.

## Hub pages (Maps of Content)

In flat systems, **index pages** do the work that folders would otherwise do:

```markdown
# Billing: hub

## Rules
- [Refund rules](billing-refund-rules.md)
- [Invoice numbering](billing-invoice-numbering.md)

## Architecture
- [Stripe integration](billing-stripe-integration.md)
```

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Zero setup, no "which folder?" debates | Hard to browse at scale |
| Links and tags allow many-to-many classification | Depends on search and discipline |
| Easy to restructure later (no paths to move) | Metadata drifts if not validated |
| Natural for wikis and note tools | Poor for ownership (no folder = no owner) |

## Best for

- Small projects (<20 docs).
- Wikis, team knowledge bases, research notes.
- Early-stage projects before the structure is clear.

## Avoid when

- Many contributors and many docs without a curator.
- Product or API docs for external readers.

## Graduation path

When the flat folder passes about 20 files:

1. Look at the prefixes and tags. The most common ones show your natural primary dimension.
2. Create folders for that dimension ([dimensions](../dimensions.md)).
3. Move files and update links. See [evolving-structure](../../choosing-structure/evolving-structure.md).

---

**Related:** [navigation-and-metadata](../navigation-and-metadata.md) · [smells-and-fixes](../smells-and-fixes.md) · [storage-locations](../storage-locations.md)
**Up:** [Organizing](../README.md)
