# Model: Organize by Version

> **What:** Docs are split per product or API version, so readers on v1 and v2 each see accurate docs.
> **Read when:** several major versions are supported at the same time and they behave differently, for example a public API, SDK, library or self-hosted product.

## TL;DR

- **Most projects don't need version folders.** Git already versions docs together with the code. Docs on a release tag describe that release.
- You need *browsable* versions only when **users on old versions still need docs** and versions differ meaningfully.
- Prefer **versioned docs-site builds** (from Git tags/branches) over copying folders by hand.
- If you do copy folders, define a **backport policy**, or old versions rot.

---

## Options, from simplest to heaviest

| Option | How | Use when |
|---|---|---|
| **1. Git only** | Docs live with code; readers browse the tag (`/tree/v1.4.0/docs`) | Internal projects, single supported version |
| **2. "Since / until" notes** | Inline markers: "Added in 2.3", "Deprecated in 3.0" | Small differences between versions |
| **3. Versioned site from branches/tags** | Docs site builds `latest`, `2.x`, `1.x` from release branches (Docusaurus versioning, `mike` for MkDocs, Read the Docs) | Libraries, SDKs, self-hosted products |
| **4. Version folders in repo** | `v1/`, `v2/` side by side | Public APIs with different major versions served at once |

## Inline version notes (option 2)

```markdown
### `timeout` option
> Added in **2.3**. Before 2.3, use `requestTimeout` (removed in 3.0).
```

Cheap and effective. Readers immediately see whether a feature applies to them.

## Version folders (option 4)

```
api/
├── README.md               which version to use, support timeline, migration links
├── v1/                     🟠 deprecated, sunset 2027-03-31
│   ├── README.md           with deprecation banner
│   ├── reference/
│   └── guides/
├── v2/                     ✅ current
│   ├── README.md
│   ├── reference/
│   └── guides/
└── migration-v1-to-v2.md
```

| Rule | Why |
|---|---|
| Version-independent docs (concepts, auth) stay **outside** version folders | Avoid N copies of the same text |
| Old versions get a **banner** and a sunset date | Readers know they're on old docs |
| **Migration guide** between each major version | The most-read page during upgrades |
| Freeze old versions, and only fix critical errors | Backporting everything costs too much |
| Published site shows a **version switcher** and defaults to latest | Search engines and readers land on current docs |

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Accurate docs per version | Duplication, multiplied by each version |
| Users on old versions are supported | Fixes need backporting |
| Clear upgrade path | Search results may surface old versions |

## Best for

Public APIs with several live major versions, SDKs, frameworks, self-hosted / on-premise software, products with long-term-support (LTS) releases.

## Avoid when

SaaS with continuous deployment (there's only "now"), internal apps, early-stage projects.

---

**Related:** [api-docs](../../doc-types/api-docs.md#versioning-and-deprecation) · [by-lifecycle](by-lifecycle.md) · [hybrid](hybrid.md)
**Up:** [Organizing](../README.md)
