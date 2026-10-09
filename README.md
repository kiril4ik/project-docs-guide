# Project Documentation Guide

> **What:** A practical handbook for creating, organizing and maintaining project documentation, mostly in Markdown.
> **For:** developers, tech leads, product/business analysts, technical writers and AI coding agents.
> **Start here:** read this page (5 min), then jump to the section you need.

---

## TL;DR

1. **Know who you're writing for.** Every document has one main audience and one job.
2. **Pick the doc type before you write.** A tutorial, an API reference and a business requirement are different things with different shapes.
3. **Pick an organizing model on purpose.** Group docs by audience, by type, by domain, or a mix of these, and write the choice down.
4. **Keep docs close to what they describe.** Docs that live in the repo get reviewed in the same PR as the code.
5. **Write for scanning.** Lead with a summary, use clear headings, short paragraphs, tables and real examples.
6. **Make it navigable.** Every folder has a `README.md` index, and every page links up to its parent and across to related pages.
7. **Maintain it.** Each doc needs an owner, a status and a "last reviewed" date. Wrong docs are worse than no docs.

---

## How this guide is organized

The guide follows the order in which you actually make documentation decisions:

```
project-docs-guide/
├── README.md                    ← you are here: basics, doc types, map
│
├── foundations/                 WHY & BASICS
│   ├── README.md
│   ├── principles.md            core rules of good documentation
│   ├── audiences.md             who reads docs and what they need
│   ├── markdown-essentials.md   Markdown syntax, GFM, front matter, Mermaid
│   └── glossary.md              terms used in this guide
│
├── doc-types/                   WHAT TO WRITE
│   ├── README.md                catalog of all doc types (master table)
│   ├── developer-docs.md        README, CONTRIBUTING, setup, conventions, CHANGELOG
│   ├── api-docs.md              REST/GraphQL/gRPC/events, OpenAPI, reference vs guides
│   ├── business-requirements.md BRD, PRD, SRS, user stories, use cases, business rules
│   ├── architecture-docs.md     C4, ADRs, RFCs / design docs
│   ├── operations-docs.md       runbooks, deployment, incidents, postmortems
│   ├── user-docs.md             end-user guides, FAQ, release notes
│   ├── process-docs.md          onboarding, roadmap, meetings, policies
│   └── ai-agent-docs.md         AGENTS.md, CLAUDE.md, llms.txt, agent rules
│
├── organizing/                  WHERE & HOW TO STORE IT  (core section)
│   ├── README.md                comparison matrix of all models
│   ├── dimensions.md            6 axes: type, audience, domain, lifecycle, version, visibility
│   ├── models/                  one page per organizing model
│   │   ├── by-doc-type.md       by-audience.md    by-domain.md     diataxis.md
│   │   ├── by-lifecycle.md      co-located.md     per-service-repo.md
│   │   ├── sequential-and-dated.md  by-version.md  flat-with-metadata.md
│   │   └── hybrid.md            combining models, one dimension per level
│   ├── storage-locations.md     repo root, docs folder, next to code, separate repo, wiki, site
│   ├── internal-vs-public.md    keeping published and internal docs apart
│   ├── folder-structures.md     8 ready-made trees for common project shapes
│   ├── naming-conventions.md    files, folders, numbering, dates, IDs, docs-root name
│   ├── navigation-and-metadata.md  indexes, cross-links, front matter, status
│   └── smells-and-fixes.md      symptoms of bad organization and fixes
│
├── choosing-structure/          HOW TO PICK THE RIGHT SETUP
│   ├── README.md
│   ├── decision-guide.md        questions, decision tree, scoring matrix
│   ├── scenarios.md             recommended setups for common project shapes
│   └── evolving-structure.md    when and how to restructure safely
│
├── writing/                     HOW TO WRITE IT
│   ├── README.md
│   ├── writing-process.md       plan → outline → draft → review → publish
│   ├── style-guide.md           voice, headings, lists, code, terminology
│   ├── page-patterns.md         page anatomy for each kind of page
│   ├── diagrams-and-visuals.md  Mermaid, C4, screenshots, tables
│   ├── writing-for-ai-agents.md making docs easy for LLMs and agents to use
│   └── maintenance.md           ownership, reviews, linting, CI, deprecation
│
└── templates/                   COPY-PASTE STARTERS
    ├── README.md                template index
    └── *-template.md            README, CONTRIBUTING, CHANGELOG, docs index, module README,
                                 ADR, RFC, BRD, PRD, user story, use case, business rules,
                                 API endpoint, runbook, postmortem, tutorial, how-to, AGENTS.md
```

> **Why topic-named folders and not `docs/`?** This repository *is* a guide, so every top-level folder is named after its topic. You can open `writing/` or `templates/` straight from the file tree without following links. The order in the tree above is the suggested reading order. In your own projects `docs/` is still a fine default. See [naming the docs root](organizing/naming-conventions.md#naming-the-documentation-root) for alternatives.

**Folder → question it answers:**

| Folder | Answers |
|---|---|
| [foundations/](foundations/README.md) | *Why* document, *who* reads it, *how* Markdown works |
| [doc-types/](doc-types/README.md) | *What* kinds of documents exist and when to write each |
| [organizing/](organizing/README.md) | *Where* to store docs and *how* to structure folders |
| [choosing-structure/](choosing-structure/README.md) | *Which* structure fits *my* project |
| [writing/](writing/README.md) | *How* to write, illustrate and maintain docs |
| [templates/](templates/README.md) | *Give me* a starting file to copy |

---

## Documentation types at a glance

Every project needs some of these. The full catalog, with when-to-use rules, is in [doc-types](doc-types/README.md).

| Family | Typical documents | Main audience | Details |
|---|---|---|---|
| **Developer** | README, CONTRIBUTING, local setup, coding conventions, CHANGELOG | Engineers working *on* the code | [developer-docs.md](doc-types/developer-docs.md) |
| **API** | API reference (OpenAPI/GraphQL schema), auth guide, error catalog, SDK guides | Engineers *consuming* the code | [api-docs.md](doc-types/api-docs.md) |
| **Business / requirements** | BRD, PRD, SRS, user stories, use cases, business rules, glossary | Product, business, QA, engineers | [business-requirements.md](doc-types/business-requirements.md) |
| **Architecture** | System overview, C4 diagrams, ADRs, RFCs / design docs | Engineers, architects, tech leads | [architecture-docs.md](doc-types/architecture-docs.md) |
| **Operations** | Runbooks, deployment guides, incident postmortems, SLOs | On-call, DevOps/SRE | [operations-docs.md](doc-types/operations-docs.md) |
| **User** | Tutorials, how-to guides, FAQ, release notes | End users, customers, support | [user-docs.md](doc-types/user-docs.md) |
| **Process / team** | Onboarding, roadmap, meeting notes, policies, SECURITY.md | Team members, stakeholders | [process-docs.md](doc-types/process-docs.md) |
| **AI agent** | AGENTS.md, CLAUDE.md, rules files, llms.txt | AI coding assistants | [ai-agent-docs.md](doc-types/ai-agent-docs.md) |

---

## Ways of organizing docs at a glance

There is no single correct structure. Pick the one that matches how people *look for* information in your project. Full comparison matrix: [organizing/README.md](organizing/README.md). The theory behind it: [organizing/dimensions.md](organizing/dimensions.md).

| Model | Top-level folders look like | Best when |
|---|---|---|
| [**By doc type**](organizing/models/by-doc-type.md) | `architecture/`, `api/`, `requirements/`, `runbooks/` | Small/medium single product, one team |
| [**By audience**](organizing/models/by-audience.md) | `developers/`, `users/`, `operators/`, `business/` | Distinct reader groups with little overlap |
| [**By domain / feature**](organizing/models/by-domain.md) | `billing/`, `auth/`, `catalog/` | Large product, teams own domains |
| [**Diátaxis**](organizing/models/diataxis.md) | `tutorials/`, `how-to/`, `reference/`, `explanation/` | Product docs, libraries, public docs sites |
| [**By lifecycle**](organizing/models/by-lifecycle.md) | `proposals/`, `active/`, `archive/` | Lots of specs/RFCs that change status |
| [**Co-located**](organizing/models/co-located.md) | `services/payments/README.md` next to the code | Monorepos, microservices, component libraries |
| [**Per-service repos + portal**](organizing/models/per-service-repo.md) | docs in each repo, aggregated in a handbook or portal | Many repos, microservice organizations |
| [**Sequential & dated**](organizing/models/sequential-and-dated.md) | `0012-use-stripe.md`, `2026-09-18-outage.md` | ADRs, RFCs, postmortems, meeting notes (inside a folder) |
| [**By version**](organizing/models/by-version.md) | `v1/`, `v2/` or a versioned docs site | Several live major versions (public APIs, SDKs) |
| [**Flat + metadata**](organizing/models/flat-with-metadata.md) | one folder, tags in front matter | Fewer than ~20 docs, wikis |
| [**Hybrid**](organizing/models/hybrid.md) (most common) | type at the top, domain inside, co-located READMEs | Most real projects past the early stage |

**Quick picker:** go to [choosing-structure/decision-guide.md](choosing-structure/decision-guide.md). It asks about 8 questions and gives you a recommended tree.

---

## The 60-second recommended default

If you don't want to decide yet, start here. It scales well and is easy to restructure later.

```
your-project/
├── README.md              what it is, quick start, links to everything below
├── CONTRIBUTING.md        how to work on it
├── CHANGELOG.md           what changed per version
├── AGENTS.md              instructions for AI coding agents (optional)
└── docs/                  (or handbook/, wiki/, knowledge/, ...)
    ├── README.md          index of everything in this folder
    ├── getting-started/   setup, first run, onboarding
    ├── architecture/      overview + decisions/ (ADRs)
    ├── api/               reference + guides
    ├── requirements/      PRDs, user stories, business rules
    ├── operations/        deployment, runbooks, incidents
    └── glossary.md        shared vocabulary
```

Why this default works and when to leave it: see [choosing-structure/scenarios.md](choosing-structure/scenarios.md).

---

## Suggested reading paths

| You are... | Read in this order |
|---|---|
| **Starting docs for a new project** | [principles](foundations/principles.md) → [decision-guide](choosing-structure/decision-guide.md) → [folder-structures](organizing/folder-structures.md) → [templates](templates/README.md) |
| **Fixing messy existing docs** | [organizing-models](organizing/README.md) → [evolving-structure](choosing-structure/evolving-structure.md) → [maintenance](writing/maintenance.md) |
| **Writing one specific document** | [doc-types catalog](doc-types/README.md) → matching type page → [page-patterns](writing/page-patterns.md) → [template](templates/README.md) |
| **Product / business analyst** | [business-requirements](doc-types/business-requirements.md) → [style-guide](writing/style-guide.md) → [PRD template](templates/prd-template.md) |
| **Setting up docs for AI agents** | [ai-agent-docs](doc-types/ai-agent-docs.md) → [writing-for-ai-agents](writing/writing-for-ai-agents.md) → [AGENTS.md template](templates/agents-md-template.md) |
| **New to Markdown** | [markdown-essentials](foundations/markdown-essentials.md) |

---

## Conventions used in this guide

Every page in this guide follows the same shape, so humans can scan it and AI agents can parse it reliably:

- **Header block:** a `> **What:** / **Read when:**` quote at the top.
- **TL;DR:** 3–7 bullets with the key points.
- **Body:** H2 sections in a predictable order, tables for comparisons, fenced code for anything you copy.
- **Related:** links to the parent index and related pages at the bottom.
- **Labels:** ✅ *Do*, ❌ *Don't*, ⚠️ *Watch out*.
- **Links:** always relative (`../doc-types/api-docs.md`), so they work on GitHub, GitLab, in IDEs and on doc sites.

## For AI agents reading this repository

- The guide is plain Markdown. Start from this file and follow links. Each folder's `README.md` lists its pages.
- When asked to **create documentation** for a project, apply [choosing-structure/decision-guide.md](choosing-structure/decision-guide.md) first, then use the files in [templates/](templates/README.md).
- When asked **where a doc belongs**, use the master table in [doc-types/README.md](doc-types/README.md) and the trees in [organizing/folder-structures.md](organizing/folder-structures.md).
- When **writing**, follow [writing/style-guide.md](writing/style-guide.md) and [writing/writing-for-ai-agents.md](writing/writing-for-ai-agents.md).
