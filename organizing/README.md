# Organizing Docs

> **What:** All the main ways to divide, group and store project documentation, compared side by side, with one detailed page per model.
> **Read when:** you're creating a doc structure, your current docs are hard to navigate, or you're unsure where a new doc belongs.

## TL;DR

- Docs can be split along **six dimensions**: **type, audience, domain, lifecycle, version, visibility**. Every organizing model is a choice of which dimension goes where. See [dimensions.md](dimensions.md).
- **Rule of three levels:** one dimension decides the **top-level folders**, a second the **subfolders**, and the rest go into **file names or front-matter metadata**. Never nest more than 3 levels without a strong reason.
- Choose the top-level dimension by asking: **"What do readers know when they start looking?"** They might know the kind of doc, their role, the feature, or the version.
- Most mature projects end up **hybrid**: type or audience at the top, domain inside, module READMEs co-located with the code.
- Every folder gets a `README.md` index. Structure without navigation is still a maze.

---

## Pages in this section

### Concepts

| Page | What it covers |
|---|---|
| [dimensions.md](dimensions.md) | The 6 axes of organization and the "primary / secondary / metadata" rule |
| [storage-locations.md](storage-locations.md) | *Where* docs physically live: repo root, docs folder, next to code, separate repo, wiki, docs site |
| [internal-vs-public.md](internal-vs-public.md) | Separating internal and published docs safely |

### Organizing models (one page each)

Index: [models/README.md](models/README.md)

| Model | Top-level folders | Page |
|---|---|---|
| **By doc type** | `architecture/`, `api/`, `requirements/`, `operations/` | [models/by-doc-type.md](models/by-doc-type.md) |
| **By audience** | `developers/`, `users/`, `operators/`, `business/` | [models/by-audience.md](models/by-audience.md) |
| **By domain / feature** | `billing/`, `auth/`, `catalog/` | [models/by-domain.md](models/by-domain.md) |
| **Diátaxis** (by user need) | `tutorials/`, `how-to/`, `reference/`, `explanation/` | [models/diataxis.md](models/diataxis.md) |
| **By lifecycle / status** | `proposed/`, `active/`, `archive/` | [models/by-lifecycle.md](models/by-lifecycle.md) |
| **Co-located with code** | `src/billing/README.md`, `packages/*/docs/` | [models/co-located.md](models/co-located.md) |
| **Per-service repos + portal** | docs in each repo, aggregated centrally | [models/per-service-repo.md](models/per-service-repo.md) |
| **Sequential & dated** | `0001-…md`, `2026-10-09-…md` | [models/sequential-and-dated.md](models/sequential-and-dated.md) |
| **By version** | `v1/`, `v2/`, versioned site | [models/by-version.md](models/by-version.md) |
| **Flat + metadata** | one folder, tags in front matter, wiki-style, PARA | [models/flat-with-metadata.md](models/flat-with-metadata.md) |
| **Hybrid** | combinations of the above | [models/hybrid.md](models/hybrid.md) |

### Practical structure

| Page | What it covers |
|---|---|
| [folder-structures.md](folder-structures.md) | Complete, copyable trees for 8 common project shapes |
| [naming-conventions.md](naming-conventions.md) | File and folder names, numbering, dates, IDs, naming the docs root |
| [navigation-and-metadata.md](navigation-and-metadata.md) | Index READMEs, cross-links, front matter schema, status, tags |
| [smells-and-fixes.md](smells-and-fixes.md) | Signs your organization is failing and how to fix each |

---

## Comparison matrix

Ratings: ●●● strong · ●●○ okay · ●○○ weak.

| Model | Findability for newcomers | Scales to large docs | Ownership clarity | Stays in sync with code | Easy to start | Typical failure |
|---|---|---|---|---|---|---|
| By doc type | ●●● | ●●○ | ●○○ | ●●○ | ●●● | Giant folders mixing all domains |
| By audience | ●●● | ●●○ | ●●○ | ●●○ | ●●○ | Duplication across audiences |
| By domain | ●●○ | ●●● | ●●● | ●●○ | ●●○ | Cross-cutting docs have no home |
| Diátaxis | ●●● | ●●● | ●○○ | ●●○ | ●○○ | Misclassified pages, forced fits |
| By lifecycle | ●○○ | ●●○ | ●●○ | ●○○ | ●●● | Broken links when files move |
| Co-located | ●○○ | ●●● | ●●● | ●●● | ●●● | No big picture, hard to browse |
| Per-service + portal | ●●○ | ●●● | ●●● | ●●● | ●○○ | Portal tooling overhead |
| Sequential & dated | ●○○ | ●●● | ●●○ | n/a | ●●● | Unreadable without an index |
| By version | ●●○ | ●●○ | ●●○ | ●●○ | ●○○ | Fixes not backported |
| Flat + metadata | ●○○ | ●○○ | ●○○ | ●○○ | ●●● | Turns into a junk drawer |
| Hybrid | ●●● | ●●● | ●●● | ●●● | ●○○ | Inconsistent rules if not written down |

**Note:** sequential/dated and lifecycle are usually **sub-patterns** used *inside* a folder (`decisions/`, `rfcs/`, `postmortems/`) rather than a whole-project model.

---

## Fast mapping: what readers know → which model

| When readers start looking, they know... | Use as top level |
|---|---|
| "I need the architecture / the API / a runbook" (the **kind** of doc) | [By doc type](models/by-doc-type.md) |
| "I'm a user / developer / operator" (their **role**) | [By audience](models/by-audience.md) |
| "This is about billing" (the **feature or area**) | [By domain](models/by-domain.md) |
| "I want to learn / do / look up / understand" (their **need**) | [Diátaxis](models/diataxis.md) |
| "This is about the `payments` service" (the **component**) | [Co-located](models/co-located.md) or [per-service](models/per-service-repo.md) |
| "I'm on version 2" (the **version**) | [By version](models/by-version.md) |

Still unsure? Use the [decision guide](../choosing-structure/decision-guide.md).

---

**Up:** [Guide home](../README.md) · **Previous section:** [Doc types](../doc-types/README.md) · **Next section:** [Choosing a structure](../choosing-structure/README.md)
