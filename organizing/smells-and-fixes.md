# Organization Smells & Fixes

> **What:** Symptoms that your documentation structure isn't working, what usually causes them, and how to fix each one.
> **Read when:** people complain they "can't find anything", or before a docs cleanup.

## TL;DR

- Most problems come from **mixed dimensions**, **missing indexes**, **duplication** and **no owner**.
- Fix structure **incrementally**, one folder at a time, with redirects or link updates.
- Don't add folders to solve a findability problem. **Add indexes first.**

---

## Smell catalog

| # | Smell | Likely cause | Fix |
|---|---|---|---|
| 1 | "Where do I put this?" asked every week | No written organizing rules; mixed dimensions at one level | Write the rules ([hybrid](models/hybrid.md#writing-down-the-rules)); one dimension per level |
| 2 | `misc/`, `other/`, `general/`, `notes/` folders | Missing category or unneeded docs | Classify each file: move, merge or delete |
| 3 | `-v2`, `-final`, `-old`, `(copy)` in names | Versioning by file name | Use Git; status in front matter; delete old copies |
| 4 | Same info in 3 places, all different | No single source of truth | Choose canonical; replace others with links |
| 5 | Folder with 50+ files | Primary dimension too coarse | Add secondary dimension subfolders ([dimensions](dimensions.md)) |
| 6 | 5 levels of nesting | Too many dimensions as folders | Flatten; move dimensions to metadata |
| 7 | Folders with 1 file each | Structure created "for later" | Collapse; create folders when content exists |
| 8 | Nobody knows if a page is current | No owner/status/review date | Add front matter; review cycle ([maintenance](../writing/maintenance.md)) |
| 9 | Old specs rank above current docs in search | No lifecycle handling | `status`, banners, `archive/`, exclude archive from search |
| 10 | Orphan pages nobody links to | No index pages | README index per folder; orphan check in CI |
| 11 | Business people never read the docs | Docs hidden in code folders or in Git only | Business-facing index; publish to site/wiki; link from tools they use |
| 12 | Runbooks not found during incidents | Organized by system, not by alert | Name by alert; link from alerts |
| 13 | Docs in Confluence *and* repo disagree | Two sources of truth | Pick one per doc type ([storage-locations](storage-locations.md)) |
| 14 | AI agents give wrong answers about the project | Ambiguous/outdated docs; no agent entry point | AGENTS.md + docs map; fix stale pages ([writing-for-ai-agents](../writing/writing-for-ai-agents.md)) |
| 15 | Agent-generated plans and reports clutter `docs/` | No separate agent working area | Move to `.agents/` or similar; promote reviewed docs only ([ai-agent-docs](../doc-types/ai-agent-docs.md#where-to-put-agent-generated-documents)) |
| 16 | Every module README looks different | No template | Template + review checklist |

---

## Quick health check (10 minutes)

Score 1 point per "yes":

- [ ] A newcomer can find setup instructions from the root README in one click.
- [ ] The docs root has an index explaining how docs are organized.
- [ ] No folder has more than ~20 files without subfolders.
- [ ] No `misc`/`other`/`old` folders.
- [ ] Every important doc has an owner.
- [ ] Draft/deprecated docs are visibly marked.
- [ ] There's one source of truth per doc type.
- [ ] A link checker runs in CI.
- [ ] Business rules have stable IDs in one place.
- [ ] AI agents have an entry file pointing to the docs map.

**8–10:** healthy. **5–7:** fix the gaps one by one. **0–4:** plan a restructure ([evolving-structure](../choosing-structure/evolving-structure.md)).

---

**Related:** [evolving-structure](../choosing-structure/evolving-structure.md) · [principles](../foundations/principles.md#common-anti-patterns) · [maintenance](../writing/maintenance.md)
**Up:** [Organizing](README.md)
