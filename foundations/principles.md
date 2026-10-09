# Principles of Good Documentation

> **What:** Ten principles that decide whether docs get used or ignored.
> **Read when:** before you create a doc structure, or when you have to argue for a documentation decision.

## TL;DR

- One document has **one audience and one job**.
- Keep a **single source of truth**: link to things, don't copy them.
- Docs live **close to the code** and change **in the same PR** (docs-as-code).
- Write for **scanning first**, reading second.
- Every doc has an **owner, a status and a review date**.
- **Wrong docs are worse than missing docs.** Delete or archive anything stale.

---

## 1. One audience, one job

A document that tries to serve a new developer, an auditor and a customer at the same time serves none of them well.

Before writing, fill in this sentence:

> *"This document helps **[audience]** to **[do / decide / understand X]**."*

If you can't finish it in one sentence, split the doc.

| ❌ Mixed | ✅ Split |
|---|---|
| `payments.md` covering business rules, API endpoints and the on-call procedure | `requirements/payments-rules.md`, `api/payments.md`, `runbooks/payments-failures.md` |

## 2. Single source of truth (SSOT)

Every fact lives in **one** place. Everywhere else **links** to it.

- ✅ The API reference is generated from the OpenAPI spec, and guides link to it.
- ✅ Environment variables are listed in `.env.example` (or one config doc), and other pages link there.
- ❌ The same setup steps copied into README, CONTRIBUTING and the wiki, which then drift apart within weeks.

When duplication is unavoidable (for example a short summary in the README), mark which copy is canonical:

```markdown
> Summary only. Canonical version: [architecture/overview.md](architecture/overview.md)
```

## 3. Docs-as-code

Treat docs like source code:

| Practice | Why |
|---|---|
| Store in the same Git repo (Markdown) | Versioned with the code, so history and blame work |
| Change in the same pull request as the code | Docs can't fall behind silently |
| Review in PRs | Catches mistakes and spreads knowledge |
| Lint and link-check in CI | Prevents broken links and formatting rot |
| Publish automatically (optional) | A docs site is always current |

Exceptions: content written mainly by non-engineers (marketing, some business docs) may fit a wiki or CMS better. See [storage-locations](../organizing/storage-locations.md).

## 4. Proximity: keep docs near what they describe

The closer a doc is to its subject, the more likely it is to be updated.

```
Distance from code  →  Likelihood of staying correct
───────────────────────────────────────────────────
code comment / docstring          highest
README.md in the module folder
/docs folder in the same repo
separate docs repository
external wiki (Confluence, Notion)  lowest
```

Use the closest location that the audience can still find and read.

## 5. Write for scanning

Most readers skim first, so design for that:

- Put the **answer first** (TL;DR, summary, "use X when Y").
- Use **descriptive headings**: "Rotate the API key", not "Procedure".
- Keep paragraphs to **3–4 sentences**.
- Use **tables** for comparisons and **numbered lists** for sequences.
- Make code **copy-pasteable** and correct.

## 6. Show, then tell

A working example beats three paragraphs of explanation. Pair every concept with a real example: a command, a request/response, a sample user story, or a diagram.

## 7. Progressive disclosure

Layer information from simple to deep:

```
README (what + quick start)
  └─ Getting started guide (first real task)
       └─ How-to guides (specific tasks)
            └─ Reference (every option)
                 └─ Explanation (why it works this way)
```

A reader should be able to stop at any layer with something useful.

## 8. Explicit ownership and status

Docs without owners rot. Each important doc should state:

```yaml
---
owner: team-payments        # who keeps it correct
status: active              # draft | active | deprecated | archived
last_reviewed: 2026-10-01
---
```

See [navigation-and-metadata](../organizing/navigation-and-metadata.md).

## 9. Delete or archive stale docs

A doc that is 30% wrong costs readers time and trust in *every* doc. Prefer:

1. **Fix** it, if it's still needed.
2. **Archive** it (move to `archive/`, add a banner) if it has historical value, such as old specs and superseded ADRs.
3. **Delete** it otherwise. Git keeps the history.

## 10. Consistency beats perfection

A consistent, average structure is easier to use than a brilliant structure followed half the time. Write your conventions down (a short `docs/README.md` or `CONTRIBUTING.md` section) and use templates ([templates](../templates/README.md)).

---

## Common anti-patterns

| Anti-pattern | Symptom | Fix |
|---|---|---|
| **Wall of text** | No headings, 20-line paragraphs | Add structure; see [style-guide](../writing/style-guide.md) |
| **Junk drawer** | `docs/misc/`, `notes.md`, `stuff-v2-final.md` | Pick an [organizing model](../organizing/README.md) |
| **Copy-paste drift** | Same instructions in 3 places, all different | Single source of truth + links |
| **Wiki graveyard** | Hundreds of pages, nobody knows which are current | Status metadata, owners, archiving |
| **Docs-only-in-heads** | "Ask Alex, they know how deploy works" | Write a runbook, starting with a bad one |
| **Over-documentation** | Docs that restate what the code says, line by line | Document *why* and *how to use*, not *what each line does* |
| **Orphan pages** | Pages no index or page links to | Every folder has a README index |

---

**Related:** [audiences.md](audiences.md) · [organizing-models](../organizing/README.md) · [maintenance](../writing/maintenance.md)
**Up:** [Foundations](README.md)
