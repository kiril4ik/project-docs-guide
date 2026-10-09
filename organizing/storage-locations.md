# Storage Locations

> **What:** *Where* documentation physically lives (repo root, docs folder, next to code, separate repo, wiki, docs site, issue tracker) and how to choose for each doc type.
> **Read when:** deciding between "in the repo" and "in Confluence/Notion", or when docs are spread over too many tools.

## TL;DR

- **Default: Markdown in the code repo.** It's versioned, reviewed and close to the code.
- Use a **wiki/Notion** for content written mainly by non-engineers, or for fast-changing team notes. **Link** to it from the repo.
- Use a **docs site** to *publish* Markdown from the repo, not as a separate place to write.
- Decide the **source of truth per doc type** and write it down. The worst setup is the same doc type in two tools.

---

## The locations

| Location | Example | Strengths | Weaknesses |
|---|---|---|---|
| **Repo root files** | `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `AGENTS.md` | Seen first; recognized by platforms and tools | Only for a handful of standard files |
| **Docs folder in repo** | `docs/`, `handbook/` | Versioned with code, PR-reviewed, docs-as-code | Non-engineers may find Git hard |
| **Co-located with code** | `services/billing/README.md` | Freshest; ownership automatic | No overview; hidden from business readers |
| **Separate docs repo** | `org/handbook`, `org/product-docs` | Independent release cycle; different access rights; non-dev contributors | Drifts from code; cross-repo PRs needed |
| **Wiki / knowledge tool** | Confluence, Notion, GitHub Wiki, Outline | Easy editing for everyone, comments, permissions | Weak versioning/review; stale pages pile up; not near code |
| **Docs site (published)** | MkDocs, Docusaurus, VitePress, Starlight, GitBook | Search, navigation, versioning, public access | Build/hosting effort; is a *view*, not a source |
| **Issue tracker** | Jira, Linear, GitHub Issues | Stories, tasks, discussion, status | Not a knowledge base; hard to read as a whole |
| **Design tools** | Figma, Miro | Visual specs, workshops | Not searchable as text; link, don't embed |
| **Generated artifacts** | API reference from OpenAPI, schema docs | Always accurate | Need a pipeline; can't hold "why" |

---

## Source of truth per doc type (recommended defaults)

| Doc type | Source of truth | Mirrors / links |
|---|---|---|
| README, CONTRIBUTING, CHANGELOG, AGENTS.md | Repo root | — |
| Setup, conventions, architecture, ADRs | Repo docs folder | Published to internal docs site |
| Module/service docs | Co-located with code | Aggregated into portal/site |
| API reference | Spec file in repo (OpenAPI/SDL/proto) | Rendered on docs site |
| API guides | Repo docs folder | Published to developer portal |
| BRD / PRD | Repo **if** product + eng both use Git; otherwise wiki | Link from repo `requirements/README.md` |
| User stories | Issue tracker | Linked from PRD |
| Business rules, glossary | **Repo** (stable IDs, greppable, readable by AI agents) | Linked from wiki |
| Runbooks | Repo (readable during outages via Git host) | Linked from alerts |
| Postmortems | Repo or incident tool | Linked from runbooks |
| Meeting notes, team rituals | Wiki | — |
| Roadmap | Product tool / wiki | Linked from README |
| User docs | Repo → published docs site / help center | — |
| Designs | Figma | Linked from PRD |

---

## Choosing: in the repo or in a wiki?

| Question | Repo | Wiki |
|---|---|---|
| Does it change when code changes? | ✅ | |
| Will engineers be the main editors? | ✅ | |
| Should it be reviewed like code? | ✅ | |
| Must AI coding agents read it? | ✅ | |
| Are the main editors non-technical? | | ✅ |
| Is it discussion-heavy, with lots of comments? | | ✅ |
| Is it short-lived (meeting notes, brainstorms)? | | ✅ |
| Does it need fine-grained permissions? | | ✅ (or separate repo) |

Mostly ✅ in one column → put it there.

---

## Repo layout options

### Single repo, one docs folder (most projects)

```
repo/
├── README.md
├── docs/
└── src/
```

### Monorepo: central + co-located

See [co-located model](models/co-located.md).

### Separate docs repo

Use it when docs have a different audience, release cycle or access rights than the code, for example a public product docs site written by a docs team.

```
org/
├── product-app/           code (private)
└── product-docs/          public docs site source
```

⚠️ Add a CI check or a PR-template checkbox to the code repo: "Docs updated in product-docs? Link the PR."

### Handbook repo (organization-level)

Org-wide engineering standards, onboarding and the architecture landscape. See [per-service-repo](models/per-service-repo.md).

---

## Anti-patterns

| ❌ | Why it hurts | ✅ Instead |
|---|---|---|
| Same doc type in Confluence *and* repo | Nobody knows which is current | Pick one; leave a link stub in the other |
| Copying Confluence pages into the repo "for AI" | Two drifting copies | Move the source of truth, or export automatically |
| Docs only in the docs site's CMS | Not versioned with code | Generate the site from repo Markdown |
| Runbooks hosted on infrastructure that fails with production | Unreachable during incidents | Keep them in Git as well |
| Personal Google Docs as specs | Lost when people leave | Team-owned location |

---

**Related:** [internal-vs-public](internal-vs-public.md) · [co-located](models/co-located.md) · [per-service-repo](models/per-service-repo.md)
**Up:** [Organizing](README.md)
