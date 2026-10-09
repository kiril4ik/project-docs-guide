# The Six Dimensions of Doc Organization

> **What:** The axes along which any document can be classified, and how to decide which axis becomes folders and which becomes metadata.
> **Read when:** before picking an organizing model. This page explains the reasoning behind all the models.

## TL;DR

- Every document has a position on **six dimensions**: **type, audience, domain, lifecycle, version, visibility**.
- Folders can express only **one dimension per level**. Choose wisely.
- **Primary dimension → top-level folders.** **Secondary → subfolders.** **Everything else → file names, front matter, or tags.**
- Choose the primary dimension by **how readers search**. Choose the secondary by **how writers own** the content.
- Visibility (internal/public) is often the one dimension that **must** be a hard split (separate folder or repo), for safety.

---

## The six dimensions

| # | Dimension | Question it answers | Example values |
|---|---|---|---|
| 1 | **Type** | What kind of document is it? | architecture, API, requirements, runbook, ADR, guide |
| 2 | **Audience** | Who is it for? | developers, users, operators, business, partners, AI agents |
| 3 | **Domain** | What part of the product/business is it about? | billing, auth, catalog, shipping |
| 4 | **Lifecycle** | What state is it in? | draft, proposed, active, deprecated, archived |
| 5 | **Version** | Which release does it describe? | v1, v2, 2026-10 |
| 6 | **Visibility** | Who may see it? | public, internal, confidential |

One document, all six dimensions:

```yaml
# requirements/billing/refund-rules.md
type: business-rules        # 1
audience: [product, qa, dev] # 2
domain: billing             # 3
status: active              # 4
version: current            # 5
visibility: internal        # 6
```

Here **type** and **domain** became folders, and the other four live in front matter.

---

## Why you can't have it all in folders

Folders form a **tree**, and a tree has exactly one parent per item. If you nest all six dimensions, you get paths like this:

```
❌ internal/developers/v2/active/billing/architecture/refund-flow.md
```

That's impossible to navigate, and moving a document from `active` to `archive` changes its URL and breaks links.

**The solution is the three-level rule:**

```
<primary dimension>/<secondary dimension>/<file named with tertiary info>.md
+ remaining dimensions in front matter or tags
```

```
✅ requirements/billing/refund-rules.md   (status, audience, visibility in front matter)
```

---

## Choosing the primary dimension (top-level folders)

The primary dimension is the one readers use to **start** searching.

| If most readers start with... | Primary dimension | Model |
|---|---|---|
| "I need *the architecture*", "where are *the runbooks*?" | Type | [by-doc-type](models/by-doc-type.md) |
| "I'm a *customer* / *developer* / *operator*" | Audience | [by-audience](models/by-audience.md) |
| "Something about *billing*" | Domain | [by-domain](models/by-domain.md) |
| "I want to *learn* / *do* / *look up* / *understand*" | Type (Diátaxis variant) | [diataxis](models/diataxis.md) |
| "I'm on *v2*" | Version | [by-version](models/by-version.md) |

**Test:** take your 10 most common reader questions (ask the team, or check search logs and Slack) and ask, for each one, which dimension the reader knows first. The dimension that wins most often is your primary.

## Choosing the secondary dimension (subfolders)

The secondary dimension is usually chosen by **ownership and growth**. Ask which split keeps each folder **owned by one team** and **under about 15–20 files**.

| Primary | Common secondary | Example |
|---|---|---|
| Type | Domain | `requirements/billing/`, `requirements/auth/` |
| Audience | Type (or Diátaxis) | `developers/architecture/`, `users/how-to/` |
| Domain | Type | `billing/architecture.md`, `billing/api.md`, `billing/runbooks/` |
| Diátaxis | Domain | `how-to/billing/`, `reference/billing/` |
| Version | Diátaxis or type | `v2/guides/`, `v2/reference/` |

## Tertiary and beyond: metadata

Put the rest into front matter, tags or naming:

| Dimension | Best expressed as |
|---|---|
| Lifecycle | `status:` in front matter + a status banner; physical `archive/` folder only for long-dead docs |
| Version | Git tags/branches, or a versioned docs site, rather than folders (unless several versions must be browsed side by side) |
| Audience (when not primary) | `audience:` in front matter, and "Who is this for" in the header |
| Sequence/time | File name prefix: `0012-…`, `2026-10-09-…` |
| Visibility | **Hard split** (folder or repo). Don't rely on metadata alone. See below. |

---

## Visibility: the exception

Visibility is about **safety**, not navigation. Metadata won't stop an internal doc from being published by mistake.

- ✅ Separate by **folder** (`public/` vs `internal/`) with a publish pipeline that only builds `public/`.
- ✅ Or separate by **repository** for strong isolation (public docs repo, private code repo).
- ❌ Don't rely on `visibility: internal` front matter alone unless the build tool enforces it and you test that.

Details: [internal-vs-public.md](internal-vs-public.md).

---

## Worked example

**Project:** a SaaS with 3 teams (billing, catalog, platform), an internal API used by a frontend, and on-call duty.

1. Top reader questions: "how do I set up locally?", "what are the refund rules?", "how does the billing service talk to Stripe?", "what to do on alert X?", "why did we pick Kafka?"
2. What readers know first: mostly the **kind** of doc (setup, rules, runbook, decision), sometimes the domain.
3. Primary = **type**. Secondary = **domain** where folders grow (requirements, runbooks).
4. Lifecycle → front matter. ADRs are sequential. Visibility is all internal, so no split is needed.

```
docs/
├── README.md
├── getting-started/
├── architecture/
│   ├── overview.md
│   └── decisions/            sequential ADRs
├── requirements/
│   ├── billing/
│   ├── catalog/
│   └── rules/
├── api/
└── operations/
    └── runbooks/
        ├── billing/
        └── platform/
```

That's a [hybrid](models/hybrid.md): type at the top, domain inside, sequential ADRs.

---

**Related:** [organizing overview](README.md) · [decision guide](../choosing-structure/decision-guide.md) · [navigation-and-metadata](navigation-and-metadata.md)
**Up:** [Organizing](README.md)
