# Naming Conventions

> **What:** Rules for naming the docs root, folders and files, including numbering, dates and IDs.
> **Read when:** setting up a docs structure, or when you find `Final_Spec_v2 (copy).md` in your repo.

## TL;DR

- Files and folders: **lowercase kebab-case**, `refund-rules.md`.
- **UPPERCASE** only for conventional root files: `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `AGENTS.md`.
- Name files by **topic**, not by doc type or date (unless it's a [sequential/dated record](models/sequential-and-dated.md)).
- Use **ISO dates** (`2026-10-09`) and **zero-padded numbers** (`0012`).
- Never put versions or statuses in file names: no `-v2`, `-final` or `-old`. Git and front matter handle those.

---

## Naming the documentation root

`docs/` is the most widely recognized name. GitHub Pages, many doc tools and most developers expect it. Choose a different name when it signals something useful or avoids a clash.

| Name | Signals | Good for |
|---|---|---|
| `docs/` | Standard project documentation | **Default** for most projects |
| `documentation/` | Same, more explicit | Teams that dislike abbreviations |
| `handbook/` | How we work, team/org knowledge | Team or company handbooks, engineering handbooks |
| `guide/`, `guides/` | Instructional content | Single-purpose guide repos |
| `knowledge/`, `kb/` | Knowledge base | Support, internal KB |
| `wiki/` | Loosely structured, collaborative | Wiki-style repos (watch for junk-drawer drift) |
| `manual/` | User manual | Products with a formal manual |
| `website/`, `site/` | Docs site *source* including config/theme | Docusaurus/VitePress projects |
| `spec/`, `specs/` | Specifications | Requirements-driven or protocol projects |
| `design/` | Design docs / RFCs | Engineering design archives |
| `.agents/`, `planning/` | AI-agent working documents | Keep agent output **separate** from human docs |
| *No root: topic folders at repo root* | The repo **is** the docs | Docs-only repos, like this guide |

**Rules:**

- ✅ One docs root per repo (plus co-located module docs). Two competing roots (`docs/` and `documentation/`) cause confusion.
- ✅ If you rename it, say so in the root README: "Documentation lives in `handbook/`."
- ⚠️ Check your tooling. Some hosts and generators default to `docs/`, so you may need a config change.

---

## Files

| Rule | ✅ | ❌ |
|---|---|---|
| Lowercase kebab-case | `refund-rules.md` | `Refund_Rules.md`, `refundRules.md`, `refund rules.md` |
| Topic, not type | `architecture/payments.md` | `architecture/architecture-doc-payments.md` |
| No version/status in name | `api-guide.md` + git tag | `api-guide-v2-final.md` |
| No dates (for living docs) | `deployment.md` | `deployment-2026.md` |
| Short but specific | `stripe-webhooks.md` | `information-about-how-stripe-webhooks-work.md`, `misc.md` |
| `.md` extension | `setup.md` | `setup.markdown`, `setup.txt` |
| `README.md` as folder index | `runbooks/README.md` | `runbooks/index-of-runbooks.md` |

> **`README.md` or `index.md`?** GitHub/GitLab display `README.md` automatically when browsing a folder. Many doc site generators expect `index.md`, though most can be configured to use README. **For repo-browsed docs, use `README.md`.**

### Sequential and dated files

| Pattern | Example | Use for |
|---|---|---|
| `NNNN-kebab-title.md` | `0012-use-stripe.md` | ADRs, RFCs |
| `YYYY-MM-DD-kebab-title.md` | `2026-09-18-checkout-outage.md` | Postmortems, meetings |
| `YYYY-MM.md` | `2026-10.md` | Monthly release notes |
| `vX.Y.md` or by SemVer | `v2.3.md` | Per-version release notes |

### ID-prefixed files

For formal requirements, put the ID first so files sort and grep by ID:

```
use-cases/UC-07-issue-refund.md
requirements/FR-PAY-012-refund-approval.md   (only if one file per requirement)
```

Common ID schemes: `BR-` business requirement/rule, `FR-` functional, `NFR-` non-functional, `UC-` use case, `US-` user story, `ADR-`, `RFC-`, `TC-` test case. Add a domain code for scale: `BR-PAY-04`.

---

## Folders

| Rule | Example |
|---|---|
| Lowercase kebab-case, plural for collections | `runbooks/`, `decisions/`, `use-cases/` |
| Singular for a single topic | `architecture/`, `billing/` |
| One dimension per level | see [hybrid](models/hybrid.md#the-golden-rule-one-dimension-per-level) |
| Max ~3 levels below docs root | `docs/requirements/billing/rules.md` |
| Underscore prefix for special/shared folders (sorts first) | `_shared/`, `_templates/`, `_assets/` |
| Assets near their docs | `architecture/images/c4-context.png` |

---

## Numbering folders and files

Prefixes like `01-`, `02-` force an order.

| Use numbering when | Avoid numbering when |
|---|---|
| Content is read **in sequence** (tutorial steps, a course, onboarding days) | Folders are topics without an inherent order |
| A **formal document set** is referenced by number (enterprise/regulated, see [structure G](folder-structures.md#g-enterprise--regulated--client-project)) | You'll insert items later (renumbering breaks links) |
| Records need **stable IDs** (ADRs) | Readers navigate directly by name. Names are easier to type and remember. |

If you number: zero-pad (`01`, not `1`), leave gaps for inserts (`10-`, `20-`, `30-`), and never renumber published items.

---

## Headings and titles

- The H1 **matches the file's topic**: `refund-rules.md` → `# Refund Rules`.
- For records, include the ID: `# ADR-0012: Use Stripe for card payments`.
- Use sentence case and descriptive wording: `## Rotate the API key`, not `## Procedure 2`.

---

**Related:** [navigation-and-metadata](navigation-and-metadata.md) · [sequential-and-dated](models/sequential-and-dated.md) · [style-guide](../writing/style-guide.md)
**Up:** [Organizing](README.md)
