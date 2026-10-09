# Model: Diátaxis (by User Need)

> **What:** A documentation framework that splits content into four kinds by what the reader needs: **tutorials** (learning), **how-to guides** (doing), **reference** (looking up) and **explanation** (understanding).
> **Read when:** you build product, library, API or platform docs for users, especially a public docs site.

## TL;DR

- Four kinds, four folders: `tutorials/`, `how-to/`, `reference/`, `explanation/`.
- Each kind has **one job** and a **distinct writing style**. Mixing them is the most common cause of confusing docs.
- Widely used for user-facing and developer-facing product docs.
- Less suited to **internal project docs** like ADRs, PRDs or runbooks. Use it for the *user/consumer* part only, or treat those as special types.

---

## The four quadrants

|  | **Practical** (doing) | **Theoretical** (knowing) |
|---|---|---|
| **Learning** (study) | **Tutorials**: "Build your first bot" | **Explanation**: "How the event loop works" |
| **Working** (at work) | **How-to guides**: "Deploy to AWS" | **Reference**: "CLI flags" |

| Kind | Reader says | Shape | Rules |
|---|---|---|---|
| **Tutorial** | "Teach me" | A guided lesson with a guaranteed result | One path, no choices, every step works, minimal explanation |
| **How-to guide** | "Help me do X" | Steps toward a specific goal | Assumes competence; title starts "How to…" or a verb; no teaching |
| **Reference** | "Tell me the facts" | Structured, complete, consistent | Mirrors the product's structure; no instructions or opinions; often generated |
| **Explanation** | "Help me understand" | Discursive discussion | Context, background, alternatives, *why*; no steps |

Page layouts for each: [page-patterns](../../writing/page-patterns.md).

## What it looks like

```
docs/
├── README.md               landing: four doors + popular pages
├── tutorials/
│   ├── README.md
│   ├── 01-first-project.md   (numbered: tutorials are sequential)
│   └── 02-add-auth.md
├── how-to/
│   ├── README.md
│   ├── deploy-to-aws.md
│   ├── configure-sso.md
│   └── migrate-from-v1.md
├── reference/
│   ├── README.md
│   ├── cli.md
│   ├── configuration.md
│   └── api/                  generated
└── explanation/              (some sites call it concepts/ or topics/)
    ├── README.md
    ├── architecture.md
    └── security-model.md
```

Popular naming variants: `guides/` for how-to, `concepts/` or `topics/` for explanation, `learn/` for tutorials.

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Based on how people actually use docs | Requires discipline to classify pages correctly |
| Improves writing: each page has one mode | Doesn't cover internal docs well (ADRs, PRDs, runbooks, meeting notes) |
| Scales well to large docs sites | Information about one feature spreads across 4 folders |
| Well-known, with good public guidance | Writers new to it often produce "how-to-tutorial-explanation" hybrids |

## Best for

- **Public product docs**, libraries, SDKs, CLIs, developer platforms.
- User docs in [by-audience](by-audience.md) setups (`users/tutorials/`, `users/how-to/`, …).
- API docs: tutorial = quick start, how-to = guides, reference = spec, explanation = concepts.

## Avoid when

- It's mainly **internal engineering knowledge** (decisions, requirements, ops). Use [by-doc-type](by-doc-type.md).
- Docs are tiny (fewer than ~10 pages). Four folders of 2 pages each is overkill. Use Diátaxis as a writing discipline, not a folder structure.

## Classification cheat sheet

Ask two questions about a page:

1. Is it about **action** (doing) or **cognition** (knowing)?
2. Is the reader **learning** or **working**?

| Action + learning | → Tutorial |
|---|---|
| Action + working | → How-to |
| Cognition + working | → Reference |
| Cognition + learning | → Explanation |

If a page fits two, **split it**. For example, a how-to with a long "why" section becomes a how-to that links to an explanation page.

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| Tutorials full of options and caveats | Move options to how-to/reference, keep one happy path |
| Reference pages with opinions and steps | Move steps to how-to, opinions to explanation |
| Huge `how-to/` folder | Add domain subfolders: `how-to/billing/` |
| Readers can't find feature X | Add a feature index or good search; cross-link the 4 kinds per feature |

## Migrating

- **To Diátaxis:** classify each existing page (spreadsheet: page → kind → action: move/split), split mixed pages first, then move. Do one section at a time.
- **Hybrid:** keep Diátaxis for the user/consumer section only and use type-based folders for internal docs. See [hybrid](hybrid.md).

---

**Related:** [page-patterns](../../writing/page-patterns.md) · [user-docs](../../doc-types/user-docs.md) · [by-audience](by-audience.md)
**Up:** [Organizing](../README.md)
